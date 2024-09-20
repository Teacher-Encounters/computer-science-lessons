# Graphics & p5.js

It is now time to experiment with programming graphical applications. For this we will use a library called p5.js.

{% embed url="https://p5js.org/" %}

Create an account on p5.js and you can use the web editor to prototype some work.

The web editor only uses JavaScript (no TypeScript) but you can use TypeScript later when we develop on our local machines using Node.js locally with an IDE like Visual Studio Code.

## Guided Tasks

### Simple Interactive Animation

#### Draw a Simple Object

Drawing should generally happen on every animation frame inside the `draw` function. For this example I will draw a rectangle.

```javascript
function draw() {
  background(220);
  
  // No outline
  noStroke()
  
  // Set the fill colour
  fill('green')
  
  // Draw a simple shape
  rect(100, 100, 50, 70);
}
```

![](<../.gitbook/assets/image (84) (1) (1).png>)

#### Specify the Position with Variables

The position is currently hardcoded into the draw function. x=100, y=100, width=50, height=70.

Let's change the x and y position so they are defined by a global variable. The initial values are given inside the `setup` function. Whilst you could give the initial values on lines 2-3, when initialisation makes use of p5.js framework variables, those will only be available inside the setup function.

```javascript
// Define these variables globally
let x;
let y;

function setup() {
  createCanvas(400, 400);
  
  // Give variables initial values once at the start
  x = 100;
  y = 100;
}
```

Now change the draw function to use these variables.

```javascript
function draw() {
  // ... other code
  
  // Draw a simple shape - using variables for position
  rect(x, y, 50, 70);
}
```

#### Animate the Shape

Now that we are using a variable to define the position, we can change the value of that variable to cause the shape to move. Add the following lines to the end of the `draw` function.

```javascript
  // Let's animate by moving from side to side.
  x = x + 5; // Increase the x position
  x = x % width; // wrap around the screen horizontally
```

If you run this code now, the box should scroll across the page. When it gets to the far side, it should wrap around to the start.

#### Respond to Key Presses

For those interested in making games, it will be important to respond to key presses from the user. There are a couple of ways to do this.

* Respond to Key Down Events
* Check that keys are down during the animation frame.

For things like continuous movement, checking the keys are down during animation makes sense. For more discrete actions (like jumping, or shooting) using a Key Down Event is a better fit.

Currently we set the fill colour to green. Replace that line of code with the following.

```javascript
  // Set the fill colour, based on if SHIFT key pressed
  if (keyIsDown(SHIFT)) {
    fill('green')
  } else {
    fill('red');
  }
  
  // Use key for continuous style of movement
  if (keyIsDown(UP_ARROW)) {
    y -= 5; // y-axis is upside down in computer graphics
  } else if (keyIsDown(DOWN_ARROW)) {
    y += 5;
  }
```

![](<../.gitbook/assets/image (83) (1).png>)

Run the code, you should find that when the SHIFT key is pressed, the rectangle goes green.

Using the UP and DOWN arrows should cause the rectangle to move UP and DOWN as well as scrolling across.

{% embed url="https://editor.p5js.org/jms-illustrious/sketches/WYQG5lZTg" %}
Finished Interactive Animation
{% endembed %}
