Part 1: CSS3 Transitions and Animations
CSS Transitions (Hover/Focus Effects)

CSS transitions allow you to smoothly change property values when a user hovers over or focuses on an element. Here’s how you can create hover effects:

Example:


button {
  background-color: #4CAF50; /* Initial color */
  transition: background-color 0.3s ease, transform 0.3s ease; /* Transition effect */
}

button:hover {
  background-color: #45a049; /* New color on hover */
  transform: scale(1.1); /* Slight grow effect */
}
In this example, the button changes color and grows in size when hovered. You can add this to at least two elements on your page.
CSS Animations with @keyframes

You can use @keyframes to create smooth, complex animations like fading, sliding, or rotating. Here's an example of a fading animation:

Example 1: Fade In Animation


@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.fade-in {
  animation: fadeIn 2s ease-in-out;
}
You can apply this class (fade-in) to any element to make it fade in.

Example 2: Rotating Animation


@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.rotate {
  animation: rotate 3s linear infinite;
}
Apply the rotate class to elements like a loading spinner to rotate them infinitely.

Part 2: JavaScript Functions
Function with Parameters and Return Values

Write a function that accepts parameters and returns a result. For instance, calculating the area of a rectangle based on user input:

Example:



function calculateArea(length, width) {
  return length * width;  // Returns the area
}

// Usage example:
let area = calculateArea(5, 10);  // Returns 50
console.log(area);
Function Demonstrating Scope (Local vs. Global Variables)

In this function, you'll show how variables behave in different scopes:

Example:


let globalVar = "I am global"; // Global scope

function demonstrateScope() {
  let localVar = "I am local";  // Local scope
  console.log(globalVar);  // Accessible within the function
  console.log(localVar);   // Accessible within the function
}

console.log(globalVar); // Accessible outside the function
// console.log(localVar); // Error: localVar is not defined outside the function
Toggling a CSS Class to Trigger Animation

You can write a function that toggles a CSS class, such as a class that applies an animation (e.g., "hidden").

Example:


function toggleHiddenClass(elementId) {
  const element = document.getElementById(elementId);
  element.classList.toggle("hidden");  // Adds/removes the 'hidden' class
}

// Usage:
// When called, it will toggle the visibility of an element with id 'modal'.
And in your CSS, the hidden class might look like this:

css
Copy
.hidden {
  display: none;
}
Part 3: Combining CSS Animations with JavaScript
Triggering Animations with JavaScript

For this, you'll want a button or other interactive element to trigger a CSS animation when clicked.

Example:


function startAnimation() {
  const element = document.getElementById('animateMe');
  element.classList.add('rotate');  // Add a class that starts the rotation animation
  
  // Reset the animation after it finishes
  element.addEventListener('animationend', () => {
    element.classList.remove('rotate');
  });
}

// Add an event listener to your button
document.getElementById('animateButton').addEventListener('click', startAnimation);
Ensuring the Animation Resets Properly

To ensure that the animation can be triggered multiple times, you can remove the animation class after it finishes, allowing it to be reapplied.

In the example above, we listen for the animationend event and remove the class once the animation ends.

Full HTML + CSS + JavaScript Example
Here's a minimal implementation based on the above steps:

HTML:


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Webpage</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <button id="animateButton">Start Animation</button>
  <div id="animateMe" class="box">Rotate Me!</div>

  <script src="script.js"></script>
</body>
</html>
CSS (style.css):


button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.3s;
}

button:hover {
  background-color: #45a049;
  transform: scale(1.1);
}

.box {
  width: 100px;
  height: 100px;
  background-color: lightblue;
  text-align: center;
  line-height: 100px;
  margin: 20px;
  font-size: 16px;
  transition: transform 0.3s;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.rotate {
  animation: rotate 3s linear;
}

.hidden {
  display: none;
}
JavaScript (script.js):


function startAnimation() {
  const element = document.getElementById('animateMe');
  element.classList.add('rotate');  // Trigger the rotation animation
  
  element.addEventListener('animationend', () => {
    element.classList.remove('rotate');  // Reset the animation for next trigger
  });
}

document.getElementById('animateButton').addEventListener('click', startAnimation);
Final S
