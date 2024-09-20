# Object Oriented Programming

## Objects

Most programs need to deal with data types which are compound structures. For example a users contact details might have several separate properties

* House name/number
* Street
* Town
* PostCode
* Phone Number

Each property can be stored as a primitive type, but combined form a structure which can be passed around as a single unit. This is incredibly useful. Let us look at an example in plain JavaScript.

```javascript
// Declare a new objects with properties and values
const aStudent = {
    name: "Adam A Anderson",
    age: 18,
    subjects: []
}

// Show how to use the dot notation to access single members
const justTheName = aStudent.name;
```

The curly brace syntax that is used by JavaScript is known as JSON (JavaScript Object Notation). It's a really important format used across the web for transmitting and storing information.

## Classes

Objects are useful, but to really unlock their power, we need to be able to define the blueprints that can be used to create those objects. For that we need to dive into classes.

{% tabs %}
{% tab title="Animals TypeScript" %}
```typescript
// Create an abstract concept of animal
abstract class Animal {
  // All animals have this property
  name: string;

  // When I create an Animal, I need to tell it it's name
  constructor(name: string) {
    this.name = name;
  }

  // This is a method that each specific sub class will implement
  abstract talk(): string;
}

// Extend the concept of animal with something more specific
class Dog extends Animal {
  talk() {
    return `${this.name} says Woof`
  }
}

// Another extension of Animal
class Cat extends Animal {
  talk() {
    return `Meow from ${this.name}`;
  }
}

// Create some animals and put them in an array of Animals
const animals: Animal[] = [];
animals.push(new Dog("Rover"));
animals.push(new Dog("Buster"));
animals.push(new Cat("Felix"));

// Use polymorphism to treat all animals alike
animals.forEach(a => {
  console.log(a.talk()); 
});
```
{% endtab %}
{% endtabs %}

## Tasks

### Task 1 - Add more Objects

This program defines a TypeScript object interface called 'Person' and then creates several objects that adhere to that interface.

* Create another instance of person and print it.
* Add another property to the Person interface, then make values up for that property for all the objects.

{% embed url="https://replit.com/@MarlingSharp/object-demo-ts#index.ts" %}
Base Project for Simple Objects
{% endembed %}

### Task 2 - Add More Shapes

Here is a program which uses inheritance to encapsulate shapes as classes. Each Shape sub class has a method for calculating the area of that shape.

Take this existing code, then add another shape subclass and calculate it's area. (Pick any shape you know from maths).

Note that I have put each Shape class in it's own TypeScript file. Add additional TypeScript files for your new shapes, then import them and use them in the main `index.ts` file.

{% embed url="https://replit.com/@MarlingSharp/shape-area-ts#index.ts" %}
