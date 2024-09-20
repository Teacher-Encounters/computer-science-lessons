# Variables and Strings

## Variables and Strings‌

## Declaring Variables <a href="#declaring-variables" id="declaring-variables"></a>

JavaScript requires the use of a keyword in front of a variable declaration.

| Keyword | Purpose                                                                    |
| ------- | -------------------------------------------------------------------------- |
| let     | Declare a new variable, the value can be reassigned later                  |
| const   | Declare a new variable, but it's value cannot be reassigned                |
| var     | This behaves a bit like 'let', but the scope of the variable is different. |

I would always recommend using `let` and `const` and ignoring `var`, but you will see `var` in examples. For the REALLY curious, here is a discussion about the different, but don't feel compelled to read.‌

{% embed url="https://stackoverflow.com/questions/762011/whats-the-difference-between-using-let-and-var" %}

## String Concatenation <a href="#string-concatenation" id="string-concatenation"></a>

Complex strings can be built by combining string literals with variable values. There are several ways to do this, but they boil down to two categories‌

* String concatenation - using the + symbol to 'add' strings together
* Formatted Strings - Some syntax that allows variables to be inserted into strings using special characters

### Code Example <a href="#code-example" id="code-example"></a>

Here we have a short program which demonstrates declaring variables and building strings.TypeScriptPython

{% tabs %}
{% tab title="TypeScript" %}
```typescript
// This name can be reassigned later
// String literals are enclosed by quotations
let myName: string = "Joe Sharp";

// This is a constant value, I wish to give it a name, but it won't change
const DAYS_IN_A_WEEK: number = 7;

// JavaScript does not distinguish between Integers and Floats
let myAge: number = 38;
let myHeight: number = 1.75; // assuming centimetres

// Concatenation can be used to build strings
let aGreeting: string = "Hello " + myName + ", you are " + myAge + " years old.";
console.log(aGreeting)

// But I prefer to use template strings
let anotherGreeting: string = `Hello ${myName}, you are ${myAge} years old.`;
console.log(anotherGreeting);
```
{% endtab %}

{% tab title="Python" %}
```python
# This name can be reassigned later
# String literals are enclosed by quotations
myName = "Joe Sharp"

# This is a constant value, I wish to give it a name, but it won't change
# Python has no way of enforcing that, but ALL CAPS is traditionally used
DAYS_IN_A_WEEK = 7

# Python can distinguish between Integers and Floats
# Largely invisible to the programmer though
myAge = 38
myHeight = 1.75 # assuming centimetres

# Concatenation can be used to build strings
# Note that I have to 'cast' the int to a string
aGreeting = "Hello " + myName + ", you are " + str(myAge) + " years old."
print(aGreeting)

# But I prefer to use template strings
# It gets rid of the need for casting, and removes the ugly + symbols
anotherGreeting = f"Hello {myName}, you are {myAge} years old."
print(anotherGreeting);
```
{% endtab %}
{% endtabs %}

## Tasks <a href="#tasks" id="tasks"></a>

### Task 1 <a href="#task-1" id="task-1"></a>

Write a program which calculates the area of a circle declares 2 variables.‌

* A constant with the value of pi
* A variable which stores a radius (make a value up for radius)

This program should then print the radius and the area, assuming the radius is in metres.‌

Here is the program in Python, you can just convert it over.

```python
# Declare our constant value for PI
PI = 3.14159265359

radius = 5 # assuming metres
area = PI * (radius ** 2) # pi * (r squared)

# Generate a nice message
message = f"A circle of radius {radius} has an area of {area}"

# Output the message to the user
print(message)
```

### Task 2 <a href="#task-2" id="task-2"></a>

Write a program which declares a noun, adjective and verb as variables. The builds a silly sentance using those variables. Here is a Python version for you to work from. Feel free to get creative with the actual sentences (normal rules of decency apply)

```python
noun = "Car"
adverb = "gently"
adjective = "loud"
print(f"The {noun} was {adjective} when it {adverb} went to school")
noun = "Zebra"
adverb = "aggressively"
adjective = "giant"
print(f"The {noun} was {adjective} when it {adverb} went to school"
```
