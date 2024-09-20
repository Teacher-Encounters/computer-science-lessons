# User Input

To make your programs more generally usable, you need to get input from the user.

In Python, this is very easy using the function `input`, but in Node.js it's rather tricky. It will require the use of a module called `prompt-sync` which will handle the task.

## Node Projects

A Node.js project is generally a folder containing a package.json file. This describes the project and lists any external dependencies. In Repl.it, this file is generally hidden from you, Repl has it's own UI for installing packages.

The first task here will show you how to take a basic TypeScript project, add 3rd party modules and write a very simple program. You will then use that as a basis for writing programs that handle user input, do calculations and print useful output.

## Tasks

### Guided Task - Basic User Input Program

The completed version of this can be found here

{% embed url="https://replit.com/@MarlingSharp/user-input-demo-ts#index.ts" %}

The documentation for the third party library can be found here

{% embed url="https://www.npmjs.com/package/prompt-sync" %}

#### Step 1 - Create TypeScript project

Create a new TypeScript project in Repl.it. Type in the following code and run it, just to check that TypeScript is working correctly.

```typescript
console.log("Hello World")
```

![Hello TypeScript](<../.gitbook/assets/image (73).png>)

#### Step 2 - Import 3rd Party Module

Click on the packages icon (on the left hand side) and search for `prompt-sync`. Click on the `+` button to install it. Repl will then run a command in the shell to enact this installation.

![Installing Packages](<../.gitbook/assets/image (74).png>)

![Package Installed](<../.gitbook/assets/image (75).png>)

![Package Installation in Shell](<../.gitbook/assets/image (76).png>)

#### Step 3 - Install Type Definitions

Some 3rd party libraries come bundled with their TypeScript definitions, but `prompt-sync` does not. The type definitions can generally be found by putting `@types/` on the front of the package name.

Now install `@types/prompt-sync` to your project and it will be ready to use.

![Install Prompt Sync definitions](<../.gitbook/assets/image (77).png>)

#### Step 3 - Hello {name}

We will write our first code that uses this library.

```typescript
import * as promptSync from 'prompt-sync';
const prompt = promptSync()

const name: string = prompt("Enter your name: ")

const ageStr: string = prompt("Enter your age: ")
const age: number = parseInt(ageStr);

const likesMCU_str: string = prompt("Do you like the MCU (y/n)?")
const likesMCU: boolean = likesMCU_str === "y"

console.log(`Hello ${name}, you are ${age} years old, likes MCU? ${likesMCU}`)
```

Line 1 imports the library. Some 3rd party libraries require this strange `import * as` construct. This is roughly based on the documentation for the library.

I have asked for the age and stored it as a string. I have then converted it to an integer using `parseInt`. In Python we do this with the `int()` function.

Here is a screenshot of that code being run.

![Run Hello Name & Age](<../.gitbook/assets/image (79).png>)

### Examples

If you want to ask the user a question, and store the result as a boolean value, you can do it like this:

{% tabs %}
{% tab title="Python" %}
```typescript
import * as promptSync from 'prompt-sync'
const prompt = promptSync();

let yesNoStr: string = prompt("Type in yes/no")

let yesNoBoolean: boolean = yesNoStr === "yes"

print(`As string: ${yesNoStr}`)
print(`As boolean: ${yesNoBoolean}`)
```
{% endtab %}
{% endtabs %}

### Task 1 - Mini Data Collection Program

Write a mini data collection program that does the following.

It asks the user for the following

* First initial
* Surname
* Age
* Do they like marmite (yes/no)

It calculates the following

* Converts the yes/no marmite answer to true/false
* Calculates age in decades

It then prints

* Well hello \<initial> \<surname>
* It is true/false you like marmite
* This is probably because you are \<decades> old

Here is the finished code in Python. Write yours in TypeScript

```python
print("What is your first initial?")
initial = input()
print("What is your surname")
surname = input()
print("What is your age?")
age = int(input())
print("Do you like marmite? Yes or No")
marmite = input()
likes_marmite = marmite == "Yes"
decades = float(age / 10)
print(f"Well hello {initial} {surname}.")
print(f"It is {likes_marmite} that you like marmite.")
print(f"This is probably because you are {decades} decades old")

```
