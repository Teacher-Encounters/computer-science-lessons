# Syntax Specific

## Pins and Connections

The syntax of a connection specification is:

```
<part's pin name> = <chip's pin name>
```

Connections describe how a part is connected to the overall chip architecture: each connection describes how one pin of the part is connected to another pin in the chip definition. In the simplest case, one may connect the part’s pin to an input or output pin of the chip.

In other cases, we have to connect the part’s pin to another pin of another part. This is done by defining an internal pin (a chip level object), and connecting the pins of the two parts to it. Thus, the definition of an internal pin is essentially the same as creating and naming a wire that connects an output pin of one chip to the input pin of another.

### Internal pins

In order to connect an output pin of Part1 to the input pins of other parts, the HDL programmer can create and use an internal pin, say _v_, as follows:

```
Part1(...,out=v);     // out of Part1 is piped into v 
Part2(in=v,...);      // v is piped into in of Part2 
Part3(a=v, b=v,...);  // v is piped into a and b of Part 3
```

An internal pin (like v above) acts like a pipe that receives a value from one part and feeds it into one or more other parts. Internal pins are created as needed when they are specified the first time in the HDL program, and require no other definition.

Each internal pin has fan-in 1 and unlimited fan-out. In other words, an internal pin can be fed from a single source only, yet it can feed (through multiple connections) many other parts. In the above example, the internal pin v simultaneously feeds both Part2 (through in) and Part3 (though a and b).

### Input pins

Each input pin of a part may be fed by one of the following sources:

* An input pin of the chip;
* An internal pin;
* One of the constants true and false, representing 1 and 0, respectively. ([more below](syntax-specific.md#constants))

Each input pin has fan-in 1, meaning that it can be fed by one source only. Thus Part(a=v,b=v,...) is a valid statement (assuming that both a and b are input pins of the part), whereas Part(a=v,a=u,...) is not.

### Output pins

Each output pin of a part may feed one of the following destinations:

* An output pin of the chip;
* An internal pin.

## Buses

Each pin used in a connection -- whether input, output, or internal -- may be a multi-bit bus. The widths (number of bits) of input and output pins are defined in the chip header. The widths of internal pins are deduced implicitly by the simulator, as explained below.

In order to connect individual elements of a multi-bit bus input or output pin, the pin name (say x) may be sub-scripted using the syntax x\[n..m]=v, where v is an internal pin. This means that only the bits indexed n to m (inclusive) of pin x are connected to the specified internal pin. An internal pin (like v above) may not be subscripted, and its width is deduced implicitly from the width of the bus pin to which it is connected the first time it is mentioned in the HDL program.

The constants true and false may also be used as buses, in which case the required width is deduced implicitly from the context of the connection. (more below)

## Sub-busing

Sub-busing can only be used on buses that are named in the IN and OUT statements of an HDL file, or inputs and outputs of the chip-parts used in the PARTS section. If you need a sub-bus of an internal bus, you must create the narrower bus as an output from a chip part. For example:

```
CHIP Foo { 
    IN in[16];
    OUT out; 

PARTS:
    Something16 (in=in, out=notIn);
    Or8Way (in=notIn[4..11], out=out);
}
```

This implementation causes an error on the Or8Way statement. This needs to be coded as:

```
PARTS:
    Something16 (in=in, out[4..11]=notIn); 
    Or8Way (in=notIn, out=out);
```

## Multiple Outputs

Sometimes you need more than one sub-bus connected to the output of a chip part. Simply add more than one out= connection to the chip part definition.

```
CHIP Foo { 
    IN in[16];
    OUT out[8]; 

PARTS:
    Not16 (in=in, out[0..7]=low8, out[8..15]=high8); 
    Something8 (a=low8, b=high8, out=out);  
}
```

This also works if you want to use an output of a chip in further computations.

```
CHIP Foo {
    IN a, b, c; 
    OUT out1, out2; 
    
PARTS:
    Something (a=a, b=b, out=x, out=out1);
    Whatever (a=x, b=c, out=out2); 
}
```

## Constants

The constants true and false may also be used as buses, in which case the required width is deduced implicitly from the context of the connection. For example:

```
CHIP Foo {
  IN in[8] // 8-bit input
  OUT out[8] // 8-bit output
  // Foo’s body (irrelevant to the example)
}
```

Suppose now that Foo is invoked by another chip using the part statement:

```
PARTS:
    Foo(in[2..4]=v, in[6..7]=true, out[0..3]=x, out[2..6]=y)
```

Where v is a previously declared 3-bit internal pin, bound to some values. In that case, the connections in\[2..4]=v and in\[6..7]=true will bind the in bus of the Foo chip to the following values:

```
     [7]  [6]  [5]  [4]  [3]  [2]  [1]  [0]
 in = 1    1    ?   v[2] v[1] v[0]  ?    ?
```

Now, let us assume that following its processing, the Foo chip returns the following set of values (an arbitrary assumption):

```
      [7]  [6]  [5]  [4]  [3]  [2]  [1]  [0]
 out = 1    1    0    1    0    0    1    1
```

In that case, the connections out\[0..3]=x and out\[2..6]=y will yield:

```
    [3]  [2]  [1]  [0]
 x = 0    0    1    1
```

```
    [4]  [3]  [2]  [1]  [0]
 y = 1    0    1    0    0
```

## HACK Chipset API

Below is a list of all the chip interfaces in the Hack chip set. If you need to use a chip-part, you can copy-paste the chip interface and proceed to fill in the missing data. This is a very useful list to have bookmarked or printed.

```
Add16(a= ,b= ,out= );
ALU(x= ,y= ,zx= ,nx= ,zy= ,ny= ,f= ,no= ,out= ,zr= ,ng= ); 
And16(a= ,b= ,out= );
And(a= ,b= ,out= );
ARegister(in= ,load= ,out= );
Bit(in= ,load= ,out= );
CPU(inM= ,instruction= ,reset= ,outM= ,writeM= ,addressM= ,pc= ); 
DFF(in= ,out= );
DMux4Way(in= ,sel= ,a= ,b= ,c= ,d= );
DMux8Way(in= ,sel= ,a= ,b= ,c= ,d= ,e= ,f= ,g= ,h= );
DMux(in= ,sel= ,a= ,b= );
DRegister(in= ,load= ,out= );
FullAdder(a= ,b= ,c= ,sum= ,carry= );
HalfAdder(a= ,b= ,sum= , carry= );
Inc16(in= ,out= );
Keyboard(out= );
Memory(in= ,load= ,address= ,out= );
Mux16(a= ,b= ,sel= ,out= );
Mux4Way16(a= ,b= ,c= ,d= ,sel= ,out= );
Mux8Way16(a= ,b= ,c= ,d= ,e= ,f= ,g= ,h= ,sel= ,out= );
Mux(a= ,b= ,sel= ,out= );
Nand(a= ,b= ,out= );
Not16(in= ,out= );
Not(in= ,out= );
Or16(a= ,b= ,out= );
Or8Way(in= ,out= );
Or(a= ,b= ,out= );
Or(a= ,b= ,out= );
PC(in= ,load= ,inc= ,reset= ,out= ); 
RAM16K(in= ,load= ,address= ,out= ); 
RAM4K(in= ,load= ,address= ,out= ); 
RAM512(in= ,load= ,address= ,out= ); 
RAM64(in= ,load= ,address= ,out= ); 
RAM8(in= ,load= ,address= ,out= ); 
Register(in= ,load= ,out= ); 
ROM32K(address= ,out= );
Screen(in= ,load= ,address= ,out= ); Xor(a= ,b= ,out= );
```
