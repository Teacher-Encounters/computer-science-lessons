---
description: >-
  This guide is designed to help you understand and write HDL programs in the
  context of Nand2Tetris courses.
---

# General Information

## Terminology

Throughout this document, we use the terms "HDL file", "HDL program", and "HDL implementation" interchangeably. Likewise, we use the terms "build a chip", "construct a chip", and "implement a chip" interchangeably. The term "HDL file stub" refers to a file that contains the HDL definition of a chip interface. That is, a stub file contains the chip name and the names of all the chip's input and output pins, without the chip's implementation, also known as the "PARTS" section of the HDL program. A stub file also contains the chip's documentation -- a succinct description of what the chip is supposed to do.

## Project Files

There are now 13 directories (folders) on your computer, named projects/01 ..., projects/13. Each directory contains all the files necessary to complete the respective project.

Projects 1-5 focus on building the hardware platform of the Hack computer. Each project walks you through the construction of a certain subset of the Hack chip-set. The directory (folder) that accompanies each project contains stub HDL files for all the chips you need to build, as well as all the test scripts required to test your HDL implementations.

The "only" thing that you have to do is extend the supplied stub HDL files into working chip implementations, i.e. chips that run in the supplied hardware simulator and successfully pass all the tests listed in the supplied test scripts.

## Chip Implementation Order

Each project directory contains a set of HDL stub files, one for each chip that you have to build. It's important to understand that all the supplied HDL files contain no implementations (building these implementations is what the project is all about). For example, consider the construction of a Xor chip. If your Xor.hdl program will include, say, And and Or chip-parts, and you have not yet implemented the And and Or chips, your tests will fail even if your Xor implementation is correct.

## HDL syntax and the meaning of "a=a"

HDL statements are used to describe how chip-parts are connected to each other, as well as to the input and output pins of the constructed chip. The syntax of these statements can be confusing, especially when pin names like in, out, a and b are used both by the chip parts as well as by the constructed chip. This leads to statements like And(a=a, b=b, out=r). This particular statement instructs to (i) connect the a and b input pins of the And chip-part to the a and b input pins of the constructed chip, (ii) create an internal pin ("wire") named r, and (iii) connect the output pin of the And chip-part to r.

Here is a simple rule that helps sort things out:

* The symbol on the left-hand side of each "=" symbol is always the name of a pin in a chip part.
* The symbol on the right-hand side is always the name of a pin or a wire in the constructed chip (the chip that you are building).

The following figure shows a diagram and HDL code of a Xor chip. The diagram uses colour coding to highlight which symbols "belong" to which chips. (Note that there are several different ways to implement Xor; this is just one of them.)

![](<../../.gitbook/assets/Screenshot 2021-11-18 at 21.19.01.png>)

## HDL Syntax Errors

The hardware simulator displays errors on the status bar at the bottom of its window. On some computers with small screens, these messages are off the bottom of the screen and are not visible. If you load your HDL and nothing show up in the HDL window in the simulator and you don't see an error message, this is probably what's happening.

Your computer should have a way to move the window to see the message using the keyboard. For example, on Windows use Alt+Space, M, and the arrow keys.

## Unconnected Pins

The Hardware Simulator does not consider unconnected pins to be errors. It defaults any unconnected input or output to be false (0). This can cause mysterious errors in your chip implementations.

If the output of your chip is always 0, make sure that your chip's output pin is connected to the output pin of one of the chip parts you are using. Double-check the names of the wires involved in the chip's output.

Typographic errors are particularly bad here since the simulator doesn't throw errors on disconnected wires. For example, if you write SomeChip(..., sum=sun); the simulator will happily make a wire named sun and your chip's output will always be 0 (because, quite likely, the sun pin will not be connected to any other chip-part in your implementation, so nothing will be piped further from SomeChip onward).

If the output of a chip-part in your implementation does not appear to be working correctly, check that all of its input pins are connected to something.

For a complete list of all the chips that you need in all the hardware projects, see the Hack Chip-Set API at the end of this document.

## Tests Are More Than Pass/Fail

For every chip.hdl file, your working directory also includes a test script, named chip.tst, and a compare file, named chip.cmp. Once your chip starts generating outputs, your directory will also include an output file named chip.out. When your chip fails the test script, don't forget to consult the .out file. Inspect the listed output values, and seek clues to the failure. If you can't see the output file in the simulator environment (reported bug on some Macs), you can look at it in a text editor.

If you need to, you can copy the chip.tst file to myChip.tst and change it to give you more information about the behavior of your chip. Change the output file name in the output-file line and delete the compare-to line. This will cause the test to always run to completion.

You can also modify the output-list line to show the outputs of your internal wires. The output format specifier is fairly obvious. The format letters are B for binary, D for decimal, and X for hexadecimal.

## Testing A Chip In Isolation

At some point, you may become convinced that your chip is correct, but it is still failing the test. The problem may be with one of the chip-parts used in your chip implementation.

You can diagnose which chip-part is causing the problem as follows. Create a test subdirectory and copy into it only the three .hdl, .tst, and .out files related to the chip that you are building. If your chip implementation passes its test in this subdirectory as-is (letting the simulator use the default Java implementation of the missing chip-parts), there must be a subtle problem with one of your chip-parts implementations, i.e. with one of the chips that you've built earlier in this project. Copy your other chips into this test directory one by one, repeating the test, until you find the problematic chip.

Note also that the supplied tests, especially for more complex chips, cannot guarantee that the tested chips are 100% correct.

## HDL Is Not A Programming Language

Go back to one of your chips that uses 3 or 4 parts. Reverse the order of the HDL statements that describe some of the chip-parts. Will the chip still work?

You may be surprised that the answer is _**yes**_.

The reason that the chip still works is that HDL is a hardware description language(also known as a "declarative" language). It describes the wiring connections that are needed to make the chip, not how it operates once power is applied. It makes no difference what order the parts are put into a circuit board. As long as all the parts get placed and connected together correctly, the circuit board will function.

The Hardware Simulator "applies the power" and tests how the chip functions. An important aspect of this is that there is no such thing as an "uninitialized variable" in HDL. If a wire is connected to an output somewhere in the HDL, it can be connected to any input. This is particularly important to understand for Chapter 3.

\\
