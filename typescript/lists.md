# Lists

Dealing with single values can get you so far in programming, but at some point you need to deal with data collections. There are a variety of different data collections, but the must fundamental is the array/list.

The two words Array and List are often thrown about interchangeably, but they are meant to be defined slightly differently.

* An array is a fixed size collection of elements of the same type
* A list is a dynamic structure to which new items can be added, old ones removed.

Let's see an example in JavaScript

```javascript
const weekdays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

// This will print each weekday by looping through the list
for (let i=0; i<weekdays.length; i++) {
    console.log(weekdays[i]);
}

// This will achieve the same result, but is more typically used by JavaScript developers
weekdays.forEach(weekday => {
    console.log(weekday);
});
```

The use of forEach on an array is an example of a functional style of programming. It has the following advantages

* You do not need to create variables to keep track of your loop
* It is quite concise and reads more descriptively

## Tasks

### Task 1

Write a program that creates a list of colours in the rainbow and prints them out in order. Here is that same program in Python.

{% tabs %}
{% tab title="Python" %}
```python
# Declare list using square brackets
colours = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']

print("Printing Colours")

# The length of the list is used to limit the loop
for i in range(len(colours)):
  # Note use of square brackets and an index to access a single item
  ith_colour = colours[i]
  print(ith_colour)

print("Finished")
```
{% endtab %}
{% endtabs %}

### Task 2 - Simon Says

Write a program which defines a series of instructions, asks the user to pick one of them using numbers and then prints that instruction. You have worked with user input, converting to numbers before. This is an extension of that.

{% tabs %}
{% tab title="Python" %}
```python
simon_says = ["Hands on head", "Hands on ears",
              "Right hand up", "Left hand up",
              "Hands on shoulders"]

# Note the use of len(list) to make sure we dont have to repeat
# the number in our code
print(f"Pick a number between 0 and {len(simon_says) - 1}")
index = int(input())
instruction = simon_says[index]

print(f"Simon says...{instruction}")
```
{% endtab %}
{% endtabs %}
