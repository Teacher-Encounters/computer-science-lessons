# Finite Iteration

## Definite Loops - for

{% embed url="https://www.w3spoint.com/for-loop-typescript" %}

Definite loops allow the programmer to repeat a block of code for a specific number of iterations. Here is a simple example.

{% tabs %}
{% tab title="Python" %}
```python
from random import randint

print("I will print 10 random numbers!")

for i in range(1, 11): # Note up to 11, it excludes the last number
  a_number = randint(1, 10);
  print(f"{i}: {a_number}")

print("Told ya")
```
{% endtab %}
{% endtabs %}

This also shows how to generate random numbers.

The range function in python creates a list of numbers from 1,10 (excluding the 11) and 'iterates' over those in the code block that follows.

Here is the same thing in TypeScript.

{% tabs %}
{% tab title="TypeScript" %}
```typescript
console.log("I will print 10 random numbers!")

for (let i=0; i<11; i++) {
  let a_number: number = Math.floor(10 * Math.random())
  console.log(`${i}: ${a_number}`)
}

console.log("Told ya")
```
{% endtab %}
{% endtabs %}

There is quite a lot going on there, look closely at line 4. There are 3 chunks inside the brackets, separated by semi colons.

* The starting condition
* The condition to evaluate for each iteration
* The statement to execute after each iteration

## Tasks

### Task 1 - Times Table

Write a TypeScript program that prints the times table. Here is the Python Equivalent

{% tabs %}
{% tab title="Python" %}
```python
times_table = 5
answer = 0
print(f"Here is the {times_table} times table")
for x in range(1,11):
    answer = x * times_table
    print(f"{x} times {times_table} is {answer}")

```
{% endtab %}
{% endtabs %}

### Task 2 - Nested Times Table

Use a loop within a loop to print the first 5 times table. The output would look a bit like this:

```
2 times table
2 x 1 = 2
2 x 2 = 2
2 x 3 = 3
...
3 times table
3 x 1 = 3
3 x 2 = 6

...etc
```

It should also ask the user

* What is the first times table to print?
* What is the last times table to print?
* How far up the times table should it go?

Here is a working version in Python, you can convert this to TypeScript

{% embed url="https://replit.com/@MarlingSharp/times-table-py#main.py" %}
