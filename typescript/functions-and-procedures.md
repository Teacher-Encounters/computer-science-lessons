# Functions & Procedures

Programs that run from top to bottom are all very well, but at some point we need to do the same thing multiple times. We can either repeat blocks of code as required, or start writing functions and procedures.

Let's look at an example (same functionality implemented in both languages).

{% tabs %}
{% tab title="JavaScript" %}
```javascript
function factorial(n) {
  let result = 1;

  // Loop where i goes from 1 to a
  for (let i=1; i<=a; i++) {
    // Use arithmetic operators
    result = result * i;
  }

  // This function should return a number to the caller
  return result;
}

// Call the function a couple of times
factorial5 = factorial(5)
factorial7 = factorial(7)

// Print the results
console.log(`Factorial of 5 is ${factorial5}`)
console.log(`Factorial of 7 is ${factorial7}`)
```
{% endtab %}

{% tab title="Python" %}
```python
def factorial(n):
  result = 1;

  # Loop where i goes from 1 to a
  for i in range(1, a + 1):
    # Use arithmetic operators
    result = result * i;

  # This function should return a number to the caller
  return result;

# Call the function a couple of times
factorial5 = factorial(5)
factorial7 = factorial(7)

# Print the results
print(f"Factorial of 5 is {factorial5}")
print(f"Factorial of 7 is {factorial7}")
```
{% endtab %}
{% endtabs %}

From this you can see that I have abstracted the code for calculating a factorial to it's own function. The calling code on lines 15 and 16 doesn't need to know how the job gets done, it just calls the function and stores the result.

## Functions vs Procedures

Functions and Procedures are both specific types of sub-routine. A sub-routine being a named block of code that can be called from other parts of a program. The key difference is that Functions will return a value, whereas procedures do not. Producures will generally result in some side effect such as writing to file, writing to screen, writing to network. Functions may do those things too, but they will also return some value.

Note: In JavaScript the keyword **function** is used for any sub-routine, so this concept and distiction can be confusing.

Keeping it simple (Hello World) here is a _procedure_

```typescript
// Declare a function that says hello
function sayHello(name: string) {
    console.log(`Hello ${name}`)
}

sayHello();
```

Here is how that might be done as a _function_.

```typescript
/**
This function generates a greeting to the named
individual and returns it.

@param name - A string name
@returns string - The generated greeting
*/
function sayHello(name: string): string {
    let greeting = `Hello ${name}`;
    return greeting;
}

// Call the function
// The return value is assigned to a variable
let myGreeting = sayHello("Mr Sharp")

// I can now print the value
console.log(myGreeting);
```

## JavaScript Function Syntax

There are a number of different ways to define functions in JavaScript, which can lead to very terse/concise code. Let us take a very simple example of a function that multiplies two numbers together. I have written 4 versions of this function, with slightly different syntax each time.

```typescript
/**
 * This declares a function called multiply that will be
 * globally available
 */
function multiplyA(a: number, b: number) {
  let answer = a * b;
  return answer;
}

/**
 * This declares the function as a variable
 * Often used to declare functions when already within a code block
 */
const multiplyB = function(a: number, b: number) {
  let answer = a * b;
  return answer;
}

/**
 * Also declaring function as a variable, but now using
 * 'arrow functions'.
 */
const multiplyC = (a: number, b: number) => {
  let answer = a * b;
  return answer;
}

/**
 * If a function is a single statement, and that statement is an expression of a result, you can remove the curly braces altogether.
 */
const multiplyD = (a: number, b: number) => a * b;

// If it isn't tested, it can't be said to work
console.log('Start Testing')
console.assert(multiplyA(3, 5) === 15, 'Incorrect A');
console.assert(multiplyB(3, 5) === 15, 'Incorrect B');
console.assert(multiplyC(3, 5) === 15, 'Incorrect C');
console.assert(multiplyD(3, 5) === 15, 'Incorrect D');
console.log('Tests Passed')
```

Why have they done this to us? JavaScript allows you to embed functions as arguments to other functions, so a concise method of expressing them is very useful. You will see this more in the section on Lists.

The section on testing at the bottom, will be explained now...

## Unit Tests

One of the most important things you can do for a body of code is to test it thoroughly. Now that we have started using the key means of building modular code, we can start writing tests for that code.

There are dedicated 3rd party frameworks for running Unit Tests in a presentable way, but for these examples we will use the basic languages ability to make assertions. Making an assertion is the programmer saying 'at this point XYZ should be true' and if it isn't true, the program throws an error.

Here is an example program that contains unit tests, both in Python and TypeScript.

{% tabs %}
{% tab title="Python" %}
```python
def sum(a, b):
  return a + b

assert sum(3, 4) == 7, "Sum Function Failed"
assert sum(12, 7) == 19, "Sum Function Failed"
assert sum(5, 21) == 26, "Sum Function Failed"

print("Completed")
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
function sum(a: number, b: number): number {
  return a + b
}

console.assert(sum(3, 4) == 7, "Sum Function Failed")
console.assert(sum(12, 7) == 19, "Sum Function Failed")
console.assert(sum(5, 21) == 3, "Sum Function Failed")

console.log("Completed")
```
{% endtab %}
{% endtabs %}

Here I show what happens when an assertion fails. Note that Python literally stops the program and 'crashes' whereas JavaScript just logs an error and keeps going.

![Python - Showing Assertion Failure](<../.gitbook/assets/image (80).png>)

![TypeScript - Showing Assertion Failure](<../.gitbook/assets/image (81).png>)

Look out for these unit tests in all future code examples.

## Tasks

### Task 1 - Which is Larger

Write a function that determines which of two numbers is larger. Remember you can use the comparison operators and if statements to determine which number to return.

Here is the equivalent function in Python, together with unit tests

```python
def which_is_larger(a, b):
  if (a > b):
    return a
  else:
    return b

assert which_is_larger(4, 5) == 5, 'Test 1 Failed'
assert which_is_larger(7, 3) == 7, 'Test 2 Failed'
assert which_is_larger(1, 8) == 8, 'Test 3 Failed'
assert which_is_larger(45, 57) == 57, 'Test 4 Failed'

print("Program Completed")
```

### Task 2 - Highest Common Factor

Write a function that implements the Euclidean algorithm for calculating the Highest Common Factor of two numbers.

Here is an implementation in Python

```python
def highest_common_factor(a, b):
  while a > 0 and b > 0:
    if a == b:
      return a
    elif a > b:
      a -= b
    else:
      b -= a
    
  return 1

print("Begin Testing")

assert highest_common_factor(12, 15) == 3, 'Test 1 Failed'
assert highest_common_factor(28, 35) == 7, 'Test 2 Failed'
assert highest_common_factor(40, 22) == 2, 'Test 3 Failed'
assert highest_common_factor(60, 48) == 12, 'Test 4 Failed'
assert highest_common_factor(273, 105) == 21, 'Test 5 Failed'

print("Testing Complete")
```
