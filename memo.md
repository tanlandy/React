# What is React
A JS library for building user interfaces (front-end framework)
1. Can break and customize elements into trees
2. Can use different components in defining and reusing -> good for reuse, scalable 
3. Rerender website efficiently -> faster, more 

# Intro to Code Sandbox and the Struture of the Module
https://codesandbox.io/ 

# Intro to JSX and Babel

Babel: a JS compiler

```Javascript
// all code will be here in the index.js, instead of changing in index.html
// first: install dependencies

// second: require them
// var React = require("react");
// var ReactDOM = require("react-dom");

// 第二种require的方法，建议用这种

import React from "react";
import ReactDOM from "react-dom";

// Use render function to display h1 in root
ReactDOM.render(<h1>Hello World</h1>, document.getElementById("root")); // (what to show, where to show)
// 注意the way to get "root"
// 这样可以直接在js文件写html

// way to have two html elements: use a div to put them together
ReactDOM.render(
  <div>
    <h1>Hello World</h1>
    <p>This is a paragraph</p>
  </div>,
  document.getElementById("root")
);
```

# Practice
```Javascript
//Create a react app from scratch.
//It should display a h1 heading.
//It should display an unordered list (bullet points).
//It should contain 3 list elements.
import React from "react";
import ReactDOM from "react-dom"; // import的方式

ReactDOM.render(
  <div>
    <h1>These are my hobbies</h1>
    <ul>
      <li>Swimming</li>
      <li>Sleeping</li>
      <li>Coding</li>
    </ul>
  </div>,
  document.getElementById("root")
);
```

# JS Expressions in JSX & ES6 Template Literals

```Javascript
import React from "react";
import ReactDOM from "react-dom";

// 想把一个var加进来，不能直接把world换成name
const fName = "Kunlin";
const lName = "Tan";
const num = 8;

ReactDOM.render(<h1>Hello World!</h1>, document.getElementById("root"));

// inject js to html的方法
ReactDOM.render(
  <div>
    <h1>Hello {fName + " " + lName}!</h1>
    <h1>Hello {fName} {lName}!</h1>
    <p>My lucky number is {num}</p> 
  </div>,
  document.getElementById("root")
);

// {}之间可以写各种js expression, 比如{3 + 4}, {Math.max(2, 5)};
// {}不可以有if, else之类的statement
```

## Statement vs. Expressions
https://youtu.be/WVyCrI1cHi8 
expression: a way to become (result) a value
const x = 5;
const y = getAnswer();
statement:
if, while, for: only perform actions, don't become values

# Practice

```Javascript
//Create a react app from scratch.
//It should display 2 paragraph HTML elements.
//The paragraphs should say:
//Created by YOURNAME.
//Copyright CURRENTYEAR.
//E.g.
//Created by Angela Yu.
//Copyright 2019.

import React from "react";
import ReactDOM from "react-dom";

const name = "Kunlin Tan"; // 用const 而不是var
const curDate = new Date();
const curYear = curDate.getFullYear(); // google如何用js拿到当前日期

ReactDOM.render(
  <div>
    <p>Created by {name}</p>
    <p>Copyright {curYear}</p>
  </div>,
  document.getElementById("root")
);

```

# JSX Attributes & Styling React Elements
https://www.w3schools.com/tags/ref_standardattributes.asp 用来找html的attributes

```Javascript
import React from "react";
import ReactDOM from "react-dom";

const img = "https://picsum.photos/seed/picsum/200";
const img2 = "https://picsum.photos/200";

// 建议总是在className来修改东西
// 注意如何添加img，并且修改img的大小
// 注意food-img的className命名方式
// alt用来给盲人一个text
ReactDOM.render(
  <div>
    <h1 className="heading" contentEditable="true" spellCheck="false">
      My Favourite Foods
    </h1>
    <ul>
      <li>Bacon</li>
      <li>Jamon</li>
      <li>Noodles</li>
    </ul>
    <div>
      <img className="food-img" alt="img" src={img + "?grayscale"}></img>
      <img className="food-img" alt="img" src={img2 + "?blur"}></img>
    </div>
  </div>,
  document.getElementById("root")
);
```
对应的css文件：
```css
.heading {
  color: red;
}

ul {
  color: blue;
}

/* all lowercase, use '-' to connect */
.food-img {
  width: 100px;
  height: 100px;
}
```
