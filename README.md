Circularity
===

A motion poem using random number generation and velocity applied to circles...

**Table of Contents**

- [Circularity](#circularity)
  - [Installation](#installation)
  - [Overview](#overview)
    - [Specs](#specs)
    - [Take Away](#take-away)
    - [Entering Code](#entering-code)
    - [Type of App : Web](#type-of-app--web)
  - [Lesson Steps](#lesson-steps)
    - [Initializing Our App](#initializing-our-app)
    - [Variable Declaration](#variable-declaration)
      - [TODO 1 : Declare Our Variables](#todo-1--declare-our-variables)
    - [Variable Initialization](#variable-initialization)
      - [TODO 2 : Initialize The Counter and Circles Array](#todo-2--initialize-the-counter-and-circles-array)
      - [TODO 3 : Stub Out The While Loop](#todo-3--stub-out-the-while-loop)
    - [Figure It Out](#figure-it-out)
      - [TODO 4 : Initialize Random Radius and Color Every Loop](#todo-4--initialize-random-radius-and-color-every-loop)
    - [TODO 5 : Draw A Circle](#todo-5--draw-a-circle)
    - [Figure It Out](#figure-it-out-1)
      - [TODO 6 : Randomly Position the Circle Within the Canvas](#todo-6--randomly-position-the-circle-within-the-canvas)
      - [TODO 7 : Push the Circle Into The Circles Array and Add It To The View](#todo-7--push-the-circle-into-the-circles-array-and-add-it-to-the-view)

## Installation

Create a new Cloud9 workspace and clone the project from github.com:

1. From your Cloud9 Dashboard, find in the upper left corner and click the green button, "Create New Workspace" > "Clone From URL":

    <img src="https://raw.githubusercontent.com/OperationSpark/using-c9/master/img/clone-new-workspace.png">

2. In the "Source URL" form input, copy and paste in the following URL (see A):
    
        https://github.com/OperationSpark/circularity.git
    
    Then, in the environment selection box, select "HTML5" (see B).  Finally, click the green button "Create" (see C).
    
    <img src="https://raw.githubusercontent.com/OperationSpark/line-crawler/master/img/clone-workspace.png">

3. Wait for the workspace to finish spooling (while spooling up, you'll see a spinning gear on the newly created workspace in the sidebar), and once the workspace is completed, click the green button, "START EDITING".

    <img src="https://raw.githubusercontent.com/OperationSpark/line-crawler/master/img/start-editing.png">

4. Now, when the workspace is loaded, select the command-line in the bottom window pane, and enter the command `bower install`, then press `Enter`, like this:

    <img src="https://raw.githubusercontent.com/OperationSpark/using-c9/master/img/motion-poem-install-bower.png">

    You'll see some test flying by on the command-line as some required files are installed... 

    and when complete, you'll see something like this:
    
    <img src="https://raw.githubusercontent.com/OperationSpark/using-c9/master/img/bower-done.png">

Nice, you're in business...

***

## Overview

### Specs

The portrait of the programmer as a young artist continues, using random number generation, color, and velocity applied to circles in this little motion poem.  As usual, we're going to be drawing to an HTML5 Canvas element using the drawing API of the CreateJS module, EaselJS, and our helper library, draw, that simplifies the drawing process somewhat.

### Take Away

Using the draw line API to create a cool randomized piece of art.

Some concepts you'll learn are:


* Drawing with CreateJS and our draw utility.
* RGB color.
* Leveraging the power of built-in and 3rd party API (DRY), like Math and opspark-draw.
* Variable declaration and initialization.
* Function invocation and passing arguments to functions.
* The While loop.
* Conditional statements - making decisions in code.
* Recognizing code blocks.
* Random number generation.
* Pair programming.

### Entering Code

As we work through the app, you'll find `// TODO //` notes in our `app.js` file, and _under_ these `TODO` lines is where you'll enter the code we need to type.  It's important you enter the code you need to type for the step under these `TODO` place markers, because code is executed in a particular order.

So, to complete a lesson step, _find_ the `TODO` place marker in the appropriate JavaScript file:

<img src="https://raw.githubusercontent.com/OperationSpark/using-c9/master/img/find-todo.png">

...then put your cursor on the line below the `TODO`, and enter the code from the current lesson step:

<img src="https://raw.githubusercontent.com/OperationSpark/using-c9/master/img/todo-done.png">

Sweet!

### Type of App : Web

Note that **this app will run _in a web browser_**, preferably Chrome.

***

## Lesson Steps

All of our coding will happen in the and write your code in the `<script id="motion-poem">` tag located at the bottom of the `index.html` file.

So, open the file at:

    index.html

***

### Initializing Our App

Starting up an application often takes a few steps of:

* Importing some libraries of code.
* Loading some external data.
* Declaring and initializing some variables for use in our app.

We've setup the app a little bit already, importing some libraries and initializing the basic plumbing in the background, and we won't be loading any external data in our app, so let's move on to declaring, initializing and using our variables.

Our motion poem will contain 100 randomly drawn circles, arranged randomly within the area of our canvas.  The big take-away in this project is **DRY**: Don't repeat yourself!

We want to draw 100 circles, but we don't want to write the code to do so 100 times.  That would be a silly waste of time and effort, making the code very difficult to maintain.

#### Loops To The Rescue

Every programming language comes with features built-in to help you implement repetative processes, like looping over a list of data, or drawing a circle 100 times.  If we want to do anything more than once, we can use a _loop_, and is most often best practice to do so.

JavaScript comes with a number of built in loops, like `for` `for-in` and `while`, and many 3rd party libraries, like _lodash_, have implementations of other types of loops.

We're going to use the `while` loop to accomplish our task.  It works like this:

````javascript
var i = 0;

while (i < 100) {
    console.log(i);
    i++;
}
````

The while loops checks first if a condition is `true`: `while (i < 100)`.  So while `i` is _less than_ `100`, the code block between the braces `{ //... }` will execute.

After executing the code block, the while loop loops-back to check the condition again, and will continue to loop until that condition is `false`.

To break out of the loop, we need the condition to return `false`, and by _incrementing_ our `i` counter on each loop using `i++;`, the value of `i` increases by one on each loop.  `i++;` is shorthand for `i = i + 1;`, and you'll see the `++` or `--` opporators used often in code to accomplish this type of pattern.

In fact, most loops use this exact same pattern: some counter checked against the length of a collection (an Array or Object), and incremented or decremented on each loop, depending on if you want to loop forward or backwards through a collection.

So then, looking at the above snippet of code, what would be the result of running that code?

#### Code Blocks

Blocks of code belong to functions, loops and conditional statements.  Code blocks are always encased within the braces `{ // code block... }`, and the code inside them is always indented by one tab.  The `{ }` braces around code blocks might seem confusing because these braces also represent Object literals.  You will, however, come to knowing when they stand for an Object, and when they represent a code block: it has everything to do with the _keyword_ that preceeds the braces.

For example:

````javascript
var myObject = {nameFirst: 'John'};
````

Above, the keyword `var` tells you you're creating a variable, and the assignment opporator, `=`, points to an object literal, `{nameFirst: 'John'};`  The braces in this case encapsulate the key/value pairs of the object, in this case, `nameFirst` and `'John'`.

Where as:

````javascript
var i = 0;

while (i < 100) {
    console.log(i);
    i++;
}
````

In this last example, the keyword `while` tells us we're opening a `while` loop, so the `{ }` braces that follow it represent the _body_ or _code block_ of the `while` loop.  The code inside these braces is the _block_ of code that will be executed each time the condition of `while (i < 100)` is `true`.

This is the same pattern with function definitions:

````javascript

function add(a, b) {
    return a + b;
}
````

Same thing here, the keyword `function` tells us we're declaring a function, and the `{ }` braces that follow it represent the _body_ or _code block_ of the `function`.  The code inside these braces is the _block_ of code that will be executed each time the function is invoked.

You should alway pay attention to blocks of code and their `{ }` braces _ you MUST always have an opening AND closing brace, otherwise the JavaScript interpreter will throw an error or your IDE will complain.

Great stuff, we're going to use the `while` loop to draw and initialize our circles.  Before we get there, let's first declare our app's required variables.

***

### Variable Declaration

#### TODO 1 : Declare Our Variables

For our app, the things we'll need are:

* `i`: a counter for our while loop.
* `circle`: we will use this variable to hold the circle shape we create using the `draw` library.
* `circles`: this variable will be an Array to hold all of our circles so we can loop through them all and update each.

Ok, we can take care of declaring our varialbes all in one statement: Find **TODO 1** and declare our varialbes like so:

````javascript
// other code...

// TODO 1: Declare our varialbes //
var i, circle, circles;

// other code...
````

### Variable Initialization

#### TODO 2 : Initialize The Counter and Circles Array

Sweet, next let's _initialize_ our counter and the circles Array.  Find **TODO 2** and initialize our counter `i` to `0` and the circles variable to `[]`, an empty Array:

````javascript
// other code...

// TODO 2: Initialize i to 0 //
i = 0;
circles = [];

// other code...
````

Excellent!  Now witness the power of computation:

We know we want to draw 100 circles, and that the `while` loop is the way go, so let's go ahead and put the while loop in place.  Once we've got that done, we'll _circle back_ to draw our circles and add each of them as children of our `view`, positioned somewhere randomly within the area of our canvas - we'll do all of this initializing within the code block of the `while` loop.

We've stub out the while loop for you; it looks like this:

````javascript
// other code...

while (i < 100) {
    // TODO 3 : YOUR CODE STARTS HERE //////////////////////////
    
    
    
    // TODO 3 : YOUR CODE ENDS HERE ////////////////////////////
					
	/*
	 * IMPORTANT NOTE: 
	 * The statement i++; increments our counter by 1 on each loop.
	 * If we did not do this, the conditional check of while (i < 100)
	 * would never return false, and we would loop forever!
	 *
	 * Leave this as the last statement in the while loop
	 */
    i++;
}

// other code...
````
Ok, now, _inside_ the code block of the `while` loop, we're going to initialize our `circle` shape!

#### TODO 3 : Generate a Radomized Circle

Implement the following code such that your `while` loop now looks like this:

````javascript
// other code...
while (i < 100) {
    // TODO 3 : YOUR CODE STARTS HERE //////////////////////////
    circle = draw.randomCircleInArea(canvas, true, true, '#999', 2);
					
    if (circle.alpha < .2) {
    	draw.blurFilterOn(circle);
    }
    
    physikz.addRandomVelocity(circle, canvas);
    circles.push(circle);
    view.addChild(circle);
    
    // TODO 3 : YOUR CODE ENDS HERE ////////////////////////////
					
	/*
	 * IMPORTANT NOTE: 
	 * The statement i++; increments our counter by 1 on each loop.
	 * If we did not do this, the conditional check of while (i < 100)
	 * would never return false, and we would loop forever!
	 *
	 * Leave this as the last statement in the while loop
	 */
    i++;
}

// other code...
````

First, we're going to use the API of our `draw` utility to draw a `randomCircleInArea()`.  This method will draw a circle random in its color, radius, transparency and position, _and_ add a cross shape to the circle.  Why the cross shape?  You'll see...

The API of this function is:

    randomCircleInArea(area, randomizeAlpha, addCross, borderColor, borderThickness, randomRadialProps)

...and we're passing in the arguments:

    circle = draw.randomCircleInArea(canvas, true, true, '#999', 2);
    
The area in this case is the `canvas`, so our cirlce will be given a randomly generated x and y coordinate within the area of our canvas.  Next we pass in two boolean values of `true`, which means we want to randomize its transparency (alpha) and add a cross shape to our circle.  Finally, the last two values, `'#999', 2`, represent the color and thickness of the circle's border.Circularity

Next, we check `if (circle.alpha < .2)`, which says _if_ the transparency of the circle happens to be less than .2, which would be almost fully transparent, we use again our `draw` utility to add a blur filter to our circle.  This will produce a neat effect on the circles such that those almost transparent will appear to be _off in the distance_.

After this, we create some magic:  We pass in our newly created `circle` and the area of the `canvas` to the `addRandomVelocity()` method of the `physikz` library, and this will add some randomly generated velocity properties, giving our circle a speed and direction within the area of our canvas:

    physikz.addRandomVelocity(circle, canvas);

Finally, we `push` our initialized circle into the the circles Array.  `push` is part of the API of a JavaScript Array, and this is the method we use to add elements to an Array.  We do this for all our circles created within the `while` loop, so we can have all the circles collected into a list which we can loop through at a later time, and update the properties of each circle.  In doing so, we can easily update the `x` and `y` properties of 


***

### Update our Variables

Awesome, let's do some fun stuff with our circles now.

Find the `update()` function; the rest of our work will take place within this function.  Right now, it's stubbed out like this:

````javascript
function update() {
    for (var i = 0; i < circles.length; i++) {
        // TODO 4 : pull out one circle at at time from the circles Array //
        
        
        physikz.updatePosition(circle);
        
        
        // TODO 5 : YOUR CODE STARTS HERE //////////////////////
    
    
    
         // YOUR TODO 5 CODE ENDS HERE //////////////////////////
        }
    }
````

The thing to notice here is that we're utilizing another type of loop: the `for` loop.  The syntax of loop looks like this:

````javascript
for (var i = 0; i < circles.length; i++) {
    // this is the code block or body of the for loop //
}
````
Following the keyword `for` the first part of the for loop within parenthesis, `(var i = 0; i < circles.length; i++)`, configures the condition for the loop.  In fact, there's three parts to it:

* var i = 0; : This initializes a counter i to 0.
* i < circles.length; : This statement is the condition against which we check on each loop.  If i is less than the length of the circles Array, the code block for the for loop will execute.
* i++ : This statement increments the counter i.  We could loop backwards, in which case we'd do something like i--.

Finally, we have our code block within the braces `{ }`.

All your code for TODO 4 and 5 will go _within_ the code block of this `for` loop, so keep that in mind!

It's your job to fill out **TODO 4** and **TODO 5**!

#### TODO 4 : Pull Out The Current Circle from the Circles Array

Use the Array syntax to pull out the circle at index `i`.

#### TODO 5 : Keep The Current Circle Within the Bounds of the Canvas

Try using an `if` and `else-if` conditional statement to check the value of the circle's `x` and `y` coordinate to keep the circle within the bounds of the circle. 

````javascript
// other code ...

// TODO 9 : pull out one circle at at time from the circles Array //
circle = circles[i];

// other code ...
````

````javascript
// other code ...

// TODO 10 : Update the position of the circle //
physikz.updatePosition(circle);

// other code ...
````

####Run the App

### Figure It Out

Alrighty, your turn!  Will help you:

* We need to keep each circle within the area of the canvas.  We know the canvas has properties proportional properties of `canvas.width` and `canvas.height`, which we can use to find the edges of the canvas.
* The circle is centered around its own x and y position, so we can find where its outer edges are located within the canvas by adding or subtracting its radius from its own x or y value.