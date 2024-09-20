# Selection

## Control Statements

{% embed url="https://www.w3spoint.com/if-else-typescript" %}

## If, Else If, Else

Selection refers to a programs ability to execute different blocks of code depending on conditions. The conditions are specified using boolean expressions.

Here is a simple example

{% tabs %}
{% tab title="Python" %}
```python
print("Enter your name")
name = input()

if name == "Lionel":
  print("It was you I was looking for!")
elif name == "Mario":
  print("Your princess is in another castle")
else:
  print("Nice to meet you")
  
print("Program Complete")
```
{% endtab %}
{% endtabs %}

If I run it an type the following things in for names, this is what happens

{% tabs %}
{% tab title="Lionel" %}
```bash
Enter your name
Lionel
It was you I was looking for!
Program Complete
```
{% endtab %}

{% tab title="Mario" %}
```
Enter your name
Mario
Your princess is in another castle
Program Complete
```
{% endtab %}

{% tab title="Joe" %}
```bash
Enter your name
Joe
Nice to meet you
Program Complete
```
{% endtab %}
{% endtabs %}

Note that it prints **Program Complete** regardless of the name. The indentation is used by Python to determine which code statements are within a block. Let us now see the same code in TypeScript.

{% tabs %}
{% tab title="TypeScript" %}
```typescript
import * as promptSync from 'prompt-sync';

const prompt = promptSync();

const myName = prompt("Enter your name: ");

if (myName === "Lionel") {
  console.log("It was you I was looking for!");
} else if (myName === "Mario") {
  console.log("Your princess is in another castle");
} else {
  console.log("Nice to meet you");
}

console.log("Program Complete");
```
{% endtab %}
{% endtabs %}

{% embed url="https://replit.com/@MarlingSharp/selection-demo-ts#index.ts" %}

The condition now needs to be enclosed in brackets, and the statements in the code blocks are now enclosed in curly braces.

## Nested Selection

Code blocks can be nested. Here is a simple example in Python and TypeScript.

{% tabs %}
{% tab title="Python" %}
```python
print("Username: ")
username = input()
if username == "Eirini":
  print("Password: ")
  password = input()
  if password == "Fish4321":
    print("Access granted")
  else:
    print("Invalid password")
else:
  print("Unknown User")
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
import * as promptSync from 'prompt-sync';

const prompt = promptSync();

const username = prompt("Username: ")
if (username === "Eirini") {
  const password = prompt("Password: ")
  if (password === "Fish4321") {
    console.log("Access granted");
  } else {
    console.log("Invalid password");
  }
} else {
  console.log("Unknown User")
}
```
{% endtab %}
{% endtabs %}

Note how the indendation increases for each nested block. In TypeScript observe how the curly braces occur in pairs to wrap entire blocks of code.

## Tasks

### Task 1 - Guess the Animal Game

Here is some Python code which gets the computer to 'guess an animal' based on your responses to a couple of questions. It uses nested selection and also .lower() to convert all user inputs to lowercase. Converting to lowercase makes it easier to compare in the conditions.

Your task is to write a TypeScript equivalent to this Python program.

```typescript
print("Pick either Ostrich, Lion or Whale")
print("I will attempt to guess your choice")
print("Does the animal live in the water? Y/N")
answer = input().lower()

if answer == "n":
   print("Does the animal have wings? Y/N")
   answer = input().lower()
   if answer == "y":
       print("It must be an Ostrich!")
   elif answer == "n":
       print("It must be a Lion!")
   else:
       print("I was looking for a y/n answer")
elif answer == "y":
   print("It must be a Whale!")
```

### Task 2 - Guess the Vegetable

Same basic premise, but instead of the Python code, you are given this flow chart. You need to write a TypeScript program that executes this same process.

![Vegetable Guesser](<../.gitbook/assets/Vegetable Guesser - Nested Selection.png>)
