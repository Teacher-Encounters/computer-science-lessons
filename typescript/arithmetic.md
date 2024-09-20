# Arithmetic

## Operators

JavaScript/TypeScript have a set of arithmetic operators that can be used to calculate values.

They are all described here

{% embed url="https://www.tutorialspoint.com/typescript/typescript_arithmetic_operators_examples.htm" %}

## Maths Library

In addition to the basic operators, there is a standard Math library which can be used to calculate the sorts of functions you see on a scientific calculator.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math" %}

## Tasks

### Task 1

Write a program which a user can calculate how to split a bill. It will ask the user the following questions

* Ask for the bill total
* Ask for number of people in the group
* Ask for percentage tip
* Calculate the total bill and then the amount per person
* Print out this information

Here is the program in Python, so you can simply convert it to TypeScript.

```python
print("---Welcome to Split My Bill---")
print("What is the total bill?")
bill_total = float(input())
print("How many people are sharing?")
people = int(input())
print("What percentage tip would you like to leave?")
tip_percentage = int(input())

percentage_decimal = tip_percentage / 100
tip_total = bill_total * percentage_decimal
bill_total = bill_total + tip_total

cost_per_person = bill_total / people

print(f"Total bill including tip is £{bill_total}")
print(f"Total cost per person is £{cost_per_person}")

```
