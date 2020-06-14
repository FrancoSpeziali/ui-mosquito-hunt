# Mosquito Hunt! (Game)

Hunt the dreaded mosquitoes!

![Mosquito](/images/mosquito.png)

## Installation

Run `npm install`

## Usage

In the terminal, run the following command:

`npm run start`

## Advanced Usage

- To check your JavaScript with ESlint, run `npm run eslint`

## Assignments

We're going to build a world which we will fill with randomly placed graphical assets.

This could be the first step to building a game!

These assignments assume you've already had experience with:
 
- writing HTML and CSS
- using the Math.random() method
- CSS animations
- ES6 classes

Things we will use / learn:

- interacting with the DOM
- using the createElement() method
- using the appendChild() method
- using the remove() method
- using classList.add() to add CSS classes
- modifying CSS style properties with JavaScript
- using ES6 classes
- using the mouse click event listener
- using the setTimeout() function

### Assignment 1 - Preparing our body tag

We want to be able to use the whole page as a 'canvas', meaning we want our graphics to appear everywhere. From the top of the page to the bottom of the page. From the left of the page to the right of the page.

1. Inside the `styles/styles.css` file, modify the `body` style to take the full width and height of the page.

### Assignment 2 - Preparing our JavaScript

We need somewhere to store our JavaScript

1. Create a JavaScript file inside the `/js` folder

2. Import your new JavaScript file inside the `index.html`, by using the tag `<script src=""></script>` - replacing the value for `src` with the location of your JavaScript file. Make sure you place this code _after_ the `<body></body>` tag.

### Assignment 3 - Beginning with HTML and CSS

Before we can write code that will generate our HTML for us, we must first understand what it is we want to do.

We will manually create some HTML / CSS to help us visualise what it is we want to achieve. After this, we will delete the HTML because we will want to generate this code with JavaScript.

1. Examine the `/images` folder for 3 tree images - `tree-1.png`, `tree-2.png`, and `tree-3.png`

2. Create 3 HTML `<div>` elements, one for each type of tree. We will use the CSS property `background-image` to set the image here.

> Hint: Normally you would use an `<img />` tag to insert these images. However, this will cause problems for us later on.

4. Create corresponding CSS classes for each of these trees

5. Use the CSS property `background-image` to set the background image for each of these trees. You may also want to set the `background-size` and `background-repeat` properties.

> Hint: Try searching online or refer to your previous assignments if you need a refresher on how to use these properties.

5. Use `position: absolute` to manually position each tree

6. For the `width` and `height` properties, I would recommend values in between `100px` and `200px`. Play around with different values until you're happy with the result.

Once you are happy with your result, comment out (hide) or delete the HTML tags you've written - but keep the CSS. In the next steps we will use JavaScript to generate the HTML.

### Assignment 4 - Beginning with our JavaScript

In the previous assignment, you created 3 HTML elements, each representing a different type of tree. The HTML might look something like this:

```
<div class="tree-1"></div>
<div class="tree-2"></div>
<div class="tree-3"></div>
```

We are going to recreate this in JavaScript.

> Hint: If you need help with any of the following methods, refer to the research links provided  

1. Inside your JavaScript file, use the DOM method `document.createElement()` to create a new HTML object.

Research: [Document.createElement() [English]](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)

Research: [Document.createElement() [Deutsch]](https://developer.mozilla.org/de/docs/Web/API/Document/createElement)

2. Use the `setAttribute()` method to set the `class` attribute to the CSS class you created for the first tree.

Research: [Element.setAttribute() [English]](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute)

Research: [Element.setAttribute() [Deutsch]](https://developer.mozilla.org/de/docs/Web/API/Element/setAttribute)

3. Use the DOM method `document.body.appendChild()` to attach your newly created object onto the `<body></body>` tag.

Research: [Node.appendChild() [English]](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

Research: [Node.appendChild() [Deutsch]](https://developer.mozilla.org/de/docs/Web/API/Node/appendChild)

4. Repeat the above 2 steps for each remaining tree.

If all went well, you should see your 3 trees again.

### Assignment 5 - Organising our code

What we did above works great, except, for our world generator we are going to need more than just three trees. In fact, we will want to randomly generate quite a few.

If we look at the code again, we'll see that there is quite a lot of repetition going on. The only difference is the CSS class. Before we can generate more trees we must organise our code.

We can simplify this code with a function.

We will write a function called `generateTree` which we will call repeatedly to generate each new tree.

1. Examine your code. Which lines are being repeated?

2. Create a function called `generateTree`, with one argument. Name this argument "cssClass". This will be our local reference to the CSS class for the tree.

3. Rewrite the JavaScript code you created in assignment 4 into the function `generateTree` so that the `createElement()`, `setAttribute()` and `appendChild()` DOM methods are only used once.

4. Call the function 3 times - one for each tree - passing in each time the corresponding CSS class for each tree.

### Assignment 6 - x, y co-ordinates

Right now the co-ordinates for each tree is hard coded inside our CSS, so that if we want to change the co-ordinates for each tree, we have to change the CSS. We want to be able to set the co-ordinates from our JavaScript.

1. Delete the `left` and `top` properties in your CSS

2. Adapt the `generateTree` function so that it receives 2 more values, through the arguments - `x` and `y`

3. Inside the `generateTree` function, use those `x` and `y` values by setting the `style` properties for your generated HTML object. `x` will correspond to the `left` property, and `y` will correspond to the `top` property. For example, your code might look something like this `htmlObject.style.left = x` (`htmlObject` refers to the object you created).

4. Finally, you will need to pass in the `x`, `y` values from where you call the function. For example, your code to call the function might look like this: `generateTree('tree-1', 100, 200)`.

Research: [ElementCSSInlineStyle.style [English]](https://developer.mozilla.org/en-US/docs/Web/API/ElementCSSInlineStyle/style)

### Assignment 7 - Random co-ordinates / Random sizes

Right now the `x` and `y` values we are passing into our function are generated by us - but we want these values to be random.

The numbers must be an integer (a whole number).

The range of these numbers must be between 0 and the maximum height / width of  the `<body></body>` tag.

We can use the DOM property `document.body.clientWidth` to find the maximum width of `<body></body>` tag.

We can use the DOM property `document.body.clientHeight` to find the maximum height of the `<body></body>` tag. 

1. Have the computer generate these numbers using the method `Math.random()`.

> Hint: You can multiply the result of `Math.random()` with a number to get a value up to that number. For example, if you need a random number between 0 - 3, `Math.random() * 3`, will give us a random number up to but not exceeding 3.

### Assignment 8 - A random tree type

So far we are generating 3 separate types of tree - manually.

What we want is to generate a random type of tree each time we call the function.

1. Modify the `generateTree` function so that instead of passing in the CSS class of the type of tree you want to create, the function randomly chooses the type of tree

> Hint: You will want to use `Math.random()` again

> Hint: Think about the range of values you might want to generate

> Hint: Think about how you might use the randomly generated value to select a CSS class

2. Remove the CSS class argument from the function, and from where we make the function call - we no longer need it

### Assignment 9 - Creating more trees - with a loop

Each time we want to generate a tree, we have to manually call the function, so that our code might look something like this:

```
generateTree(x, y);
generateTree(x, y);
generateTree(x, y);
```

This is quite repetitive, and if we wanted to do 

1. Use a `for loop` to generate the call to the `generateTree` function. You will have to generate a new random `x` `y` value for each tree.

2. Play around with the number of trees you might want to generate.

![Preview](assignment-9-preview.png)

### Assignment 10 - Preventing overflow in our CSS

You might notice horizontal and vertical scrollbars on the page.

We want to remove this to make for a nicer visual experience.

1. Add the following CSS properties to the `body` element in your CSS

```
overflow-x: hidden;
overflow-y: hidden;
```

This will prevent scrolling on the page

2. You might want to add other CSS properties such as `background-color`

### Assignment 11 - Adding a mosquito - with an ES6 class

If you look again at the `/images` folder, you'll notice that there is another file there - `mosquito.png`.

We will use the techniques we learned from the previous assignments, to generate random mosquitoes on the page.

However, our mosquitoes will be more complex than is possible with a simple function, so we will use an ES6 Class to contain all the logic.

1. Create an ES6 class called `Mosquito`

2. Write a `constructor` method which receives 2 values - `x` and `y` as arguments.

3.  In the `constructor` method, assign the `x` and `y` values as class properties `this.x` and `this.y` respectively

4. In the `constructor` method, create a new element using the `document.createElement()` method, and assign it to the class property `this.node`

5. Inside your `Mosquito` ES6 class, write a `render` method. Add any styles and attributes you might need to set to your `this.node` class property here, then use the `appendChild()` method to add the HTML object `this.node` to your page.

> Note: The `render()` method will be responsible for adding the HTML element on the page

### Assignment 12 - Adding multiple mosquitoes

1. Add multiple mosquitoes on the page with different `x` `y` values, using the same techniques you used for adding multiple trees.

### Assignment 13 - Mosquito CSS

1. Following the same techniques as you did for the trees, write a CSS class for the mosquitoes

2. In the `Mosquito` ES6 class `render` method, set the CSS class to your mosquito HTML object.

### Assignment 14 - Mosquito animation

1. Using CSS, animate the mosquito so that it increases then decreases in size, infinitely.

![Preview](assignment-13-preview.gif)

> Hint: You can animate the CSS `transform` property `scale()`

> Hint: Combine and use the CSS `animation` property and `@keyframes` rule

### Assignment 15 - Adding a destroy animation

1. Create a new method in your ES6, called `destroy`. This method will be called when we want to destroy the mosquito.

2. Write a new CSS class and animation which will show the mosquito spinning 360 degrees, and gradually shrinking in size till it disappears.

3. Add this CSS class using `classList.add()` to the HTML object `this.node` in your new `destroy` method

Research: [Element.classList [English]](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)

Research: [Element.classList [Deutsch]](https://developer.mozilla.org/de/docs/Web/API/Element/classList)

### Assignment 16 - Destroy the mosquito!

1. Inside the `destroy` method, use the `remove()` method to remove the HTML object `this.node` from the DOM. Wrap this inside a `setTimeout` function (we want to remove it when the animation has finished playing).

Research: [ChildNode.remove ()[English]](https://developer.mozilla.org/en-US/docs/Web/API/ChildNode/remove)

Research: [ChildNode.remove() [Deutsch]](https://developer.mozilla.org/de/docs/Web/API/ChildNode/remove)

### Assignment 17 - Hunt the mosquito!

We're nearly there! Just one last step in the puzzle.

We're going to add an event listener to listen for a mouse click. We will add an event listener to each mosquito, using the `Mosquito` ES6 class we created.

1. In the `constructor` method in your ES6 class, modify the `onclick` property so that it points to the `destroy` method

### Assignmnet 18 - Get creative!

1. Lastly, add a "title" to the game, which appears for a few seconds then disappears. Liven it up with a CSS animation.

2. Try adding a counter on the screen showing the total number of mosquitoes left to hunt

3. What else can you do to make the game more appealing?

Good hunting!

## Preview

![Preview](preview.gif)

## Credits

Graphical assets taken from https://opengameart.org/
