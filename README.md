# Pong: A Step-by-Step Guide

This guide will take you through the steps to create a simple version of the classic game, [Pong](https://en.wikipedia.org/wiki/Pong), using HTML, CSS, and JavaScript. You will need to create your own repo and add empty `index.html`, `styles.css`, and `script.js` files to it. It is very good practice to re-type the code snippets below, instead of copy and pasting, in order to aid your recollection. 

* * *

### **Step 1: Create the HTML Structure**

#### **Add a `<canvas>` Element**

The `<canvas>` element is where the game will be rendered.

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Simple Pong Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <canvas id="gameCanvas" width="800" height="600">
</canvas>
    <script src="script.js">
</script>
</body>
</html>
```

#### **New Concepts and Vocabulary**

1.  `<!DOCTYPE html>`: Declares the document type and HTML version, ensuring the browser renders the page in standards mode. [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Doctype)
2.  `<html lang="en">`: The root element of the HTML document, with `lang="en"` specifying the content language as English for accessibility and SEO benefits. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/html)
3.  `<head>`: Contains meta-information about the HTML document, such as its title, character encoding, and links to stylesheets or scripts. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head)
4.  `<meta charset="UTF-8">`: Specifies the character encoding for the HTML document, ensuring text is displayed correctly. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta#attr-charset)
5.  `<title>`: Sets the title of the webpage, which appears in the browser tab and is used by search engines. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title)
6.  `<link rel="stylesheet" href="styles.css">`: Links an external CSS file (`styles.css`) to the HTML document, allowing the application of styles to the webpage. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link)
7.  `<body>`: Contains all the content displayed on the webpage, such as text, images, and interactive elements like the canvas. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/body)
8.  `<canvas id="gameCanvas" width="800" height="600"></canvas>`: An HTML5 element used for drawing graphics via JavaScript. The `id` attribute uniquely identifies the canvas, and `width` and `height` set its size. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas)
9.  `<script src="script.js"></script>`: Links an external JavaScript file (`script.js`) to the HTML document, enabling dynamic functionality and interactivity. [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)

#### **Test Your Knowledge**

1.  Why is it necessary to declare `<!DOCTYPE html>` at the start of an HTML document?
2.  What is the role of the `<head>` element in an HTML document?
3.  How do you link an external CSS file to your HTML?
4.  What is the primary purpose of the `<canvas>` element?
5.  Where in the HTML structure is JavaScript typically linked?

#### **Answers**

1.  It ensures the browser renders the page in standards mode, using the correct HTML version.
2.  It contains metadata, such as the document's title, character encoding, and links to stylesheets or scripts.
3.  Using the `<link>` element with the `rel="stylesheet"` attribute.
4.  To provide an area for drawing graphics via JavaScript.
5.  Inside the `<body>` or `<head>` using the `<script>` tag.

* * *

### **Step 2: Style the Canvas with CSS**

In `styles.css`, add the following code to style the canvas with a black background and a border for visibility:

```css

#gameCanvas {
    background-color: #000;
    border: 2px solid #fff;
    display: block;
    margin: 0 auto;
}
```

#### **New Concepts and Vocabulary**

1.  `#gameCanvas`: A CSS ID selector that targets the element with `id="gameCanvas"`. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors)
2.  `background-color`: Sets the background color of an element. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color)
3.  `border`: Defines the border around an element, including its size, style, and color. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/border)
4.  `display: block`: Makes an element behave like a block-level element. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
5.  `margin: 0 auto`: Centers an element horizontally within its container. [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)

#### **Test Your Knowledge**

1.  What does the `#` symbol represent in CSS?
2.  How can you change the background color of an element?
3.  What does `display: block` mean in CSS?
4.  Which property would you use to add a border around an element?
5.  How can you center an element horizontally using CSS?

#### **Answers**

1.  It represents an ID selector, targeting an element with a specific `id` attribute.
2.  Using the `background-color` property.
3.  It makes the element occupy the full width of its container and start on a new line.
4.  The `border` property.
5.  By using `margin: 0 auto`.

* * *

### **Step 3: Initialize the Canvas Context in JavaScript**

In `script.js`, initialize the canvas context:

```javascript

const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
```

#### **New Concepts and Vocabulary**

1.  `getElementById`: A JavaScript method that selects an HTML element by its ID. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
2.  `canvas.getContext('2d')`: Retrieves the 2D drawing context from the canvas. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/getContext)

#### **Test Your Knowledge**

1.  How do you select an HTML element by its ID in JavaScript?
2.  What does `getContext('2d')` do?

#### **Answers**

1.  By using `document.getElementById('id')`.
2.  It initializes a 2D drawing context on the canvas element.

* * *

### **Step 4: Define Paddle Properties**

Define properties for the paddles:

```javascript

const paddleWidth = 10;
const paddleHeight = 100;
const player = {
    x: 10,
    y: canvas.height / 2 - paddleHeight / 2,
    width: paddleWidth,
    height: paddleHeight,
    dy: 0
};
```

#### **New Concepts and Vocabulary**

1.  `Object`: A data structure used to store related properties and methods. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
2.  `property`: A value associated with an object, used to describe attributes.

#### **Test Your Knowledge**

1.  What is an object in JavaScript?
2.  How are properties used within an object?

#### **Answers**

1.  An object is a data structure that stores related properties and methods.
2.  Properties are used to define characteristics or attributes of the object.

* * *

### **Step 5: Draw the Paddles**

Create a function to draw a paddle:

```javascript

function drawPaddle(paddle) {
    ctx.fillStyle = '#fff';
    ctx.fillRect(paddle.x, paddle.y, paddle.width, paddle.height);
}
```

#### **New Concepts and Vocabulary**

1.  `fillStyle`: Sets the color used to fill shapes. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillStyle)
2.  `fillRect`: Draws a filled rectangle on the canvas. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillRect)

#### **Test Your Knowledge**

1.  What is the purpose of `fillStyle` in canvas drawing?
2.  How do you draw a filled rectangle on a canvas?

#### **Answers**

1.  It sets the color used to fill shapes.
2.  By using the `fillRect()` method.

* * *

Great! I'll continue with the remaining steps, maintaining the same format.

* * *

### **Step 6: Define Ball Properties**

Define the ball's properties in the game:

```javascript

const ball = {
    x: canvas.width / 2,
    y: canvas.height / 2,
    size: 10,
    speed: 5,
    dx: 5,
    dy: 5
};
```

#### **New Concepts and Vocabulary**

1.  `size`: Represents the radius (size) of the ball.
2.  `speed`: Indicates how fast the ball moves.
3.  `dx` and `dy`: Commonly used variables representing the change in position along the x-axis and y-axis, respectively.

#### **Test Your Knowledge**

1.  What does `size` represent in this context?
2.  How would you describe `dx` and `dy` in programming terms?

#### **Answers**

1.  It represents the size (radius) of the ball.
2.  They indicate how much the position changes along the x-axis (`dx`) and y-axis (`dy`).

* * *

### **Step 7: Draw the Ball**

Create a function to draw the ball on the canvas:

```javascript

function drawBall(ball) {
    ctx.fillStyle = '#fff';
    ctx.beginPath();
    ctx.arc(ball.x, ball.y, ball.size, 0, Math.PI * 2);
    ctx.fill();
    ctx.closePath();
}
```

#### **New Concepts and Vocabulary**

1.  `beginPath()`: Begins a new path for drawing shapes on the canvas. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/beginPath)
2.  `arc()`: Draws a circular arc. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/arc)
3.  `fill()`: Fills the current path with the `fillStyle` color. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fill)
4.  `closePath()`: Closes the current path, ensuring the shape is completed. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/closePath)

#### **Test Your Knowledge**

1.  What is the purpose of `beginPath()`?
2.  How would you draw a circle on a canvas?
3.  What does `fill()` do in canvas drawing?

#### **Answers**

1.  It starts a new path for drawing on the canvas.
2.  By using the `arc()` method with appropriate parameters.
3.  It fills the current drawing path with the specified color.

* * *

### **Step 8: Handle Player Input**

Allow the player to control the paddle using keyboard events:

```javascript

const keys = {
    ArrowUp: false,
    ArrowDown: false
};

document.addEventListener('keydown', (e) => {
    if (e.key in keys) {
        keys[e.key] = true;
    }
});

document.addEventListener('keyup', (e) => {
    if (e.key in keys) {
        keys[e.key] = false;
    }
});
```

#### **New Concepts and Vocabulary**

1.  `addEventListener`: Registers an event listener for a specified event (e.g., `keydown`). [MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
2.  `keydown` and `keyup`: Events that trigger when a key is pressed or released. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/keydown_event)
3.  `e.key`: Represents the key value of the pressed keyboard key. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key)

#### **Test Your Knowledge**

1.  How do you listen for keyboard events in JavaScript?
2.  What are `keydown` and `keyup` events used for?
3.  How can you identify which key was pressed?

#### **Answers**

1.  By using the `addEventListener()` method.
2.  They detect when a key is pressed (`keydown`) or released (`keyup`).
3.  By accessing the `e.key` property within the event handler.

* * *

### **Step 9: Update Paddle Position**

Create a function to update the paddle's position based on the player's input:

```javascript

function movePaddle(
) {
    if (keys.ArrowUp && player.y > 0) {
        player.y -= 7;
    }
    if (keys.ArrowDown && player.y + player.height < canvas.height) {
        player.y += 7;
    }
}
```

#### **New Concepts and Vocabulary**

1.  `if` statement: A control structure that executes a block of code based on a specified condition. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
2.  `&&` (Logical AND): Ensures that both conditions must be true for the code block to execute. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND)

#### **Test Your Knowledge**

1.  What is an `if` statement used for?
2.  How does the `&&` operator work?

#### **Answers**

1.  An `if` statement executes code only if a specified condition is true.
2.  The `&&` operator checks if both conditions are true before executing a code block.

* * *

### **Step 10: Move the AI Paddle**

Make the AI paddle follow the ball's position automatically:

```javascript

function moveAI(
) {
    if (ai.y + ai.height / 2 < ball.y) {
        ai.y += ai.dy;
    } else {
        ai.y -= ai.dy;
    }

    if (ai.y < 0) ai.y = 0;
    if (ai.y + ai.height > canvas.height) ai.y = canvas.height - ai.height;
}
```

#### **New Concepts and Vocabulary**

1.  `else`: Executes an alternative block of code if the `if` condition is false. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
2.  Comparisons (`<`, `>`): Used to compare two values. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

#### **Test Your Knowledge**

1.  When is an `else` statement executed?
2.  What is the purpose of comparison operators like `<` and `>`?

#### **Answers**

1.  When the preceding `if` condition is false.
2.  To compare two values and determine their relationship (e.g., less than, greater than).

* * *

### **Step 11: Update Ball Position**

Update the ball's position based on its velocity:

```javascript

function moveBall(
) {
    ball.x += ball.dx;
    ball.y += ball.dy;
}
```

#### **New Concepts and Vocabulary**

1.  `+=` operator: Adds a specified value to a variable and updates the variable with the new value. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Addition_assignment)

#### **Test Your Knowledge**

1.  What does the `+=` operator do in JavaScript?
2.  How would you increment a variable by a specific amount?

#### **Answers**

1.  It adds a value to the existing variable and updates the variable with the result.
2.  By using the `+=` operator.

* * *

### **Step 12: Detect Collisions**

Detect and handle collisions with the walls and paddles.

Detecting collisions is probably the trickiest step. We have added comments `//` to the first `if` statement. Try to work out what the other `if` statement are doing before re-typing this code snippet into your own script file.

```javascript

function detectCollision(
) {
    // Check if the ball hits the top or bottom of the canvas
    if (ball.y - ball.size < 0 || ball.y + ball.size > canvas.height) {

        // Reverse the vertical direction of the ball
        ball.dy *= -1;
    }

    if (
        ball.x - ball.size < player.x + player.width &&
        ball.y > player.y &&
        ball.y < player.y + player.height
    ) {
        ball.dx *= -1;
        ball.x = player.x + player.width + ball.size;
    }

    if (
        ball.x + ball.size > ai.x &&
        ball.y > ai.y &&
        ball.y < ai.y + ai.height
    ) {
        ball.dx *= -1;
        ball.x = ai.x - ball.size;
    }

    if (ball.x - ball.size < 0 || ball.x + ball.size > canvas.width) {
        resetBall();
    }
}
```

#### **New Concepts and Vocabulary**

1.  `||` (Logical OR): Returns true if at least one condition is true. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR)
2.  `*=` operator: Multiplies the variable by a value and updates it. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Multiplication_assignment)

#### **Test Your Knowledge**

1.  How does the `||` operator function?
2.  What does the `*=` operator do?

#### **Answers**

1.  It checks if at least one of the conditions is true.
2.  It multiplies the variable by a given value and updates the variable with the result.

* * *

### **Step 13: Reset Ball Position**

Reset the ball to the center of the canvas:

```javascript

function resetBall(
) {
    ball.x = canvas.width / 2;
    ball.y = canvas.height / 2;
    ball.dx = -ball.dx;
    ball.dy = 5;
}
```

#### **New Concepts and Vocabulary**

1.  `-`: A unary operator that inverts the sign of a number, changing positive to negative or vice versa. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unary_negation)
2.  `Assignment`: Setting a variable to a new value.

#### **Test Your Knowledge**

1.  What does the `-` operator do when used in front of a number?
2.  How do you assign a value to a variable?

#### **Answers**

1.  It inverts the sign of the number, making a positive value negative or vice versa.
2.  You use the `=` operator to assign a value to a variable.

* * *

### **Step 14: Render the Game Frame**

Clear the canvas and redraw all elements to update the game view:

```javascript

function render(
) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawPaddle(player);
    drawPaddle(ai);
    drawBall(ball);
}
```

#### **New Concepts and Vocabulary**

1.  `clearRect(x, y, width, height)`: Clears a rectangular area, making it transparent. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/clearRect)
2.  `Redraw`: The process of drawing elements again to update their positions.

#### **Test Your Knowledge**

1.  What does `clearRect()` do?
2.  Why do you need to redraw elements in a game loop?

#### **Answers**

1.  It clears a specific rectangular area on the canvas.
2.  To ensure all elements are updated to their current positions.

* * *

### **Step 15: Create the Game Loop**

Create a function that repeatedly updates the game state using `requestAnimationFrame`:

```javascript

function gameLoop(
) {
    movePaddle();
    moveAI();
    moveBall();
    detectCollision();
    render();
    requestAnimationFrame(gameLoop);
}
```

#### **New Concepts and Vocabulary**

1.  `requestAnimationFrame()`: A method that tells the browser to call a specified function before the next repaint. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)
2.  `Game Loop`: A cycle that keeps the game running by constantly updating and rendering frames.

#### **Test Your Knowledge**

1.  What is the purpose of `requestAnimationFrame()`?
2.  Why is a game loop important in game development?

#### **Answers**

1.  It schedules the next execution of a function before the browser's next repaint.
2.  To continuously update the game state and render frames for smooth gameplay.

* * *

### **Step 16: Start the Game Loop**

Start the game by invoking the `gameLoop` function:

```javascript

gameLoop();
```

#### **New Concepts and Vocabulary**

1.  `Function Invocation`: The act of calling a function to execute its code.

#### **Test Your Knowledge**

1.  How do you start a function in JavaScript?

#### **Answer**

1.  By writing the function name followed by parentheses, e.g., `gameLoop()`.

* * *

### **Step 17: Optional: Add Scoring System**

Implement a scoring system to track points for both players:

```javascript

let playerScore = 0;
let aiScore = 0;

function resetBall(
) {
    ball.x = canvas.width / 2;
    ball.y = canvas.height / 2;
    ball.dx = -ball.dx;
    ball.dy = 5;

    if (ball.dx > 0) {
        playerScore++;
    } else {
        aiScore++;
    }
}

function render(
) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawPaddle(player);
    drawPaddle(ai);
    drawBall(ball);

    // Draw scores
    ctx.fillStyle = '#fff';
    ctx.font = '30px Arial';
    ctx.fillText(playerScore, canvas.width / 4, 50);
    ctx.fillText(aiScore, 3 * canvas.width / 4, 50);
}
```

#### **New Concepts and Vocabulary**

1.  `Variable Incrementation`: The process of increasing a variable's value by a certain amount.
2.  `fillText(text, x, y)`: Draws text on the canvas at specified coordinates. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/fillText)

#### **Test Your Knowledge**

1.  How do you increment a variable's value in JavaScript?
2.  How do you draw text on a canvas?

#### **Answers**

1.  By using `variable++` or `variable += value`.
2.  Using the `fillText()` method.

* * *

### **Step 18: Final Touches**

Enhance the game with additional functionality:

*   Adjust the ball's speed over time.
*   Add start/restart buttons.
*   Improve AI movement for more challenging gameplay.

#### **New Concepts and Vocabulary**

1.  `Refinement`: The process of improving and fine-tuning functionality.
2.  `Event Listener`: Reacting to user interactions such as clicks or keypresses.

* * *

### **Review**

1.  Why is it necessary to declare `<!DOCTYPE html>` at the start of an HTML document?
2.  What is the role of the `<head>` element in an HTML document?
3.  How do you link an external CSS file to your HTML?
4.  What is the primary purpose of the `<canvas>` element?
5.  Where in the HTML structure is JavaScript typically linked?
6.  What does the `#` symbol represent in CSS?
7.  How can you change the background color of an element?
8.  What does `display: block` mean in CSS?
9.  Which property would you use to add a border around an element?
10.  How can you centre an element horizontally using CSS?
11.  How do you select an HTML element by its ID in JavaScript?
12.  What does `getContext('2d')` do?
13.  What is an object in JavaScript?
14.  How are properties used within an object?
15.  What is the purpose of `fillStyle` in canvas drawing?
16.  How do you draw a filled rectangle on a canvas?
17.  What does `size` represent in this context?
18.  How would you describe `dx` and `dy` in programming terms?
19.  What is the purpose of `beginPath()`?
20.  How would you draw a circle on a canvas?
21.  What does `fill()` do in canvas drawing?
22.  How do you listen for keyboard events in JavaScript?
23.  What are `keydown` and `keyup` events used for?
24.  How can you identify which key was pressed?
25.  What is an `if` statement used for?
26.  How does the `&&` operator work?
27.  When is an `else` statement executed?
28.  What is the purpose of comparison operators like `<` and `>`?
29.  What does the `+=` operator do in JavaScript?
30.  How would you increment a variable by a specific amount?
31.  How does the `||` operator function?
32.  What does the `*=` operator do?
33.  What does the `-` operator do when used in front of a number?
34.  How do you assign a value to a variable?
35.  What does `clearRect()` do?
36.  Why do you need to redraw elements in a game loop?
37.  What is the purpose of `requestAnimationFrame()`?
38.  Why is a game loop important in game development?
39.  How do you start a function in JavaScript?
40.  How do you increment a variable's value in JavaScript?
41.  How do you draw text on a canvas?

#### **Answers**

1.  It ensures the browser renders the page in standards mode, using the correct HTML version.
2.  It contains metadata, such as the document's title, character encoding, and links to stylesheets or scripts.
3.  Using the `<link>` element with the `rel="stylesheet"` attribute.
4.  To provide an area for drawing graphics via JavaScript.
5.  Inside the `<body>` or `<head>` using the `<script>` tag.
6.  It represents an ID selector, targeting an element with a specific `id` attribute.
7.  Using the `background-color` property.
8.  It makes the element occupy the full width of its container and start on a new line.
9.  The `border` property.
10.  By using `margin: 0 auto`.
11.  By using `document.getElementById('id')`.
12.  It initializes a 2D drawing context on the canvas element.
13.  An object is a data structure that stores related properties and methods.
14.  Properties define characteristics or attributes of the object.
15.  It sets the color used to fill shapes.
16.  By using the `fillRect()` method.
17.  It represents the size (radius) of the ball.
18.  They indicate how much the position changes along the x-axis (`dx`) and y-axis (`dy`).
19.  It starts a new path for drawing on the canvas.
20.  By using the `arc()` method with appropriate parameters.
21.  It fills the current drawing path with the specified color.
22.  By using the `addEventListener()` method.
23.  They detect when a key is pressed (`keydown`) or released (`keyup`).
24.  By accessing the `e.key` property within the event handler.
25.  An `if` statement executes code only if a specified condition is true.
26.  The `&&` operator checks if both conditions are true before executing a code block.
27.  When the preceding `if` condition is false.
28.  To compare two values and determine their relationship (e.g., less than, greater than).
29.  It adds a value to the existing variable and updates the variable with the result.
30.  By using the `+=` operator.
31.  It checks if at least one of the conditions is true.
32.  It multiplies the variable by a given value and updates the variable with the result.
33.  It inverts the sign of the number, making a positive value negative or vice versa.
34.  You use the `=` operator to assign a value to a variable.
35.  It clears a specific rectangular area on the canvas.
36.  To ensure all elements are updated to their current positions.
37.  It schedules the next execution of a function before the browser's next repaint.
38.  To continuously update the game state and render frames for smooth gameplay.
39.  By writing the function name followed by parentheses, e.g., `gameLoop()`.
40.  By using `variable++` or `variable += value`.
41.  Using the `fillText()` method.
