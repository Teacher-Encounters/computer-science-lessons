# Condition Controlled Iteration

## Indefinite Loops - while

{% embed url="https://www.w3spoint.com/while-loop-typescript" %}

Code blocks can be repeated while a condition is true. Here is an example of a program which keeps looping until the user types in a specific word.

{% tabs %}
{% tab title="Python" %}
```python
# Ask user for their first word
user_word = input("Enter a word: ")

# Keep asking until they type 'quit'
while user_word != "quit":
  # Just print their word
  print(f"You typed {user_word}")

  # Ask for another word
  user_word = input("Enter another word: ")

# This will print after the loop is done
print("You finally quit!")
```
{% endtab %}

{% tab title="TypeScript" %}
```typescript
import * as promptSync from 'prompt-sync';

const prompt = promptSync();

// Ask user for their first word
let userWord: string = prompt("Enter a word: ");

while (userWord !== 'quit') {
  // Just print their word
  console.log(`You typed ${userWord}`);

  // Ask for another word
  userWord = prompt("Enter a word: ");
}

// This gets printed after the loop
console.log("You finally quit!")


```
{% endtab %}
{% endtabs %}

Note that Python again uses the colon and indentation to mark a code block. Java/TypeScript uses brackets around the condition and then curly braces to enclose a block.

## Tasks

### Task 1

Write a program that picks a random number from 1 to 10, then asks the user to keep guessing until they guess the matching number. Here is the same program in Python.

{% tabs %}
{% tab title="Python" %}
```python
from random import randint

# Computer picks a number
number = randint(1, 10)

# Asks user for guess
print("Guess a number between 1 and 10 (inclusive)")
guess = int(input())

# If the guess does not equal the number, go round again
while guess != number:
  print("Incorrect")
  print("Guess a number between 1 and 10")
  guess = int(input())

# Assume they have guessed correctly
print("Correct")
```
{% endtab %}
{% endtabs %}
