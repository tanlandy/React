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
https://picsum.photos/ 找图片的网站

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
# Inline Styling for React Elements
https://www.w3schools.com/cssref/ CSS Property List

```Javascript
import React from "react";
import ReactDOM from "react-dom";

// 不能下面这么写
// ReactDOM.render(
//   <h1 style="color : red">Hello World!</h1>,
//   document.getElementById("root")
// );

// js object里面，用','分割，而不是css中的';'
// 而且需要用的“”
const customStyle = {
  color: "red",
  fontSize: "20px",
  border: "1px solid black"
};

// 甚至可以实时改object的属性
customStyle.color = "blue";

// 需要一个js object
ReactDOM.render(
  <h1 style={customStyle}>Hello World!</h1>,
  document.getElementById("root")
);
```

# Practise

```Javascript
//Create a React app from scratch.
//Show a single h1 that says "Good morning" if between midnight and 12PM.
//or "Good Afternoon" if between 12PM and 6PM.
//or "Good evening" if between 6PM and midnight.
//Apply the "heading" style in the styles.css
//Dynamically change the color of the h1 using inline css styles.
//Morning = red, Afternoon = green, Night = blue.

import React from "react";
import ReactDOM from "react-dom";

const date = new Date();

const colorStyle = {
  color: "red"
};

let greeting;
if (0 < date.getHours() && date.getHours() < 12) {
  greeting = "Morning";
  colorStyle.color = "red";
} else if (date.getHours() < 18) {
  greeting = "Afternoon";
  colorStyle.color = "green";
} else {
  greeting = "Night";
  colorStyle.color = "blue";
}

ReactDOM.render(
  <h1 className="heading" style={colorStyle}>
    Good {greeting}
  </h1>,
  document.getElementById("root")
);

```

# React Components

https://github.com/airbnb/javascript/tree/master/react Airbnb Style Guide for React

index.js
```Javascript
import React from "react";
import ReactDOM from "react-dom";
// import Heading from "./Heading.jsx";
// import List from "./List.jsx";
import App from "./App.jsx"; // 注意是如何import的

// 注意方式：如何用js function来放进element里
// 注意位置：把这个function直接新建到了Heading.jsx
// function Heading() {
//   return <h1>My Favourite Foods</h1>;
// }

// 注意：如果之间没有child，可以直接写作<Heading />

// 最后直接都放到了App.jsx里面
ReactDOM.render(<App />, document.getElementById("root"));
```

App.jsx
```Javascript
import React from "react";
import List from "./List.jsx";
import Heading from "./Heading.jsx";

// 注意是如何把两个包在一起的
function App() {
  return (
    <div>
      <Heading />
      <List />
    </div>
  );
}

export default App;
```

Heading.jsx
```Javascript
import React from "react"; // 需要import react

function Heading() {
  return <h1>My Favourite Foods</h1>;
}

export default Heading; // 注意是如何export的
```

List.jsx
```Javascript
import React from "react";

function List() {
  return (
    <ul>
      <li>Bacon</li>
      <li>Jamon</li>
      <li>Noodles</li>
    </ul>
  );
}

export default List; // 注意方法： export default
```

# Practice
前一个模块更好的写法：index.js里面只有一个App，App.js里面只有一个Heading，Heading里面具体的实现

index.js
```Javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./App.jsx";

ReactDOM.render(<App />, document.getElementById("root"));
```

App.jsx
```Javascript
import React from "react";
import Heading from "./Heading.jsx";

function App() {
  return <Heading />;
}

export default App;
```

Heading.jsx
```Javascript
import React from "react";

function Heading() {
  const date = new Date();
  const currentTime = date.getHours();

  let greeting;

  const customStyle = {
    color: ""
  };

  if (currentTime < 12) {
    greeting = "Good Morning";
    customStyle.color = "red";
  } else if (currentTime < 18) {
    greeting = "Good Afternoon";
    customStyle.color = "green";
  } else {
    greeting = "Good Night";
    customStyle.color = "blue";
  }

  return (
    <h1 className="heading" style={customStyle}>
      {greeting}
    </h1>
  );
}

export default Heading;
```

# Javascript ES6 - Import, Export, and Modules

Node.js require() vs. ES6
https://stackoverflow.com/questions/31354559/using-node-js-require-vs-es6-import-export 

```Javascript
import React from "react";
import ReactDOM from "react-dom";
import PIE, { doublePi, triplePi } from "./math.js"; // PIE不用一定写成pi，因为默认的返回值就是pi
// 但是doublePi, triplePi必须是相同的名字
ReactDOM.render(
  <ul>
    <li>{PIE}</li>
    <li>{doublePi()}</li>
    <li>{triplePi()}</li>
  </ul>,
  document.getElementById("root")
);



// 另一种方式

import React from "react";
import ReactDOM from "react-dom";
import * as pi from "./math.js"; // 直接把全部都到进来
ReactDOM.render(
  <ul>
    <li>{pi.default}</li>
    <li>{pi.doublePi()}</li>
    <li>{pi.triplePi()}</li>
  </ul>,
  document.getElementById("root")
);
```

math.js
```Javascript
const pi = 3.141596;

function doublePi() {
  return pi * 2;
}

function triplePi() {
  return pi * 3;
}

export default pi; // 注意需要有一个default export

export { doublePi, triplePi };

```

# Local Environment Setup for React Development

node.js https://nodejs.org/en/ 
vscode https://code.visualstudio.com/ 
babel syntax highlighter https://babeljs.io/docs/en/editors 
vscode icon extension
create a new react app https://reactjs.org/docs/create-a-new-react-app.html 


```bash
npx create-react-app my-app # 全局变量，不用在意运行的path
cd my-app
npm start
```
把无关的文件都删除掉
修改一下index.html和index.js
之后就和sandbox一样了

index.html
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>React App</title>
  </head>
  <body>
    <div id="root"></div>
    <!-- 加了这句话 -->
    <script src="./src/index.js" type="text/jsx"></script> 
  </body>
</html>
```

index.js
```Javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(
  <h1>Hello world</h1>,
  document.getElementById("root")
);
```

# Keeper App Part 1

下载下来之后，先在对应文件夹的路径npm instal，然后npm start
完成情况在Keeper-app文件夹

# React Props

Reduce 重复的内容
props: properties

index.js
```Javascript
import React from "react";
import ReactDOM from "react-dom";

function Card(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <img src={props.img} alt="avatar_img" />
      <p>{props.tel}</p>
      <p>{props.email}</p>
    </div>
  );
}

ReactDOM.render(
  <div>
    <h1>My Contacts</h1>
    <Card
      name="Beyonce"
      img="https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg"
      tel="+123 456 789"
      email="b@beyonce.com"
    />
    <Card name="Kunlin" email="dafd@odaf.com" tel="3242341342" />
    <input id="fName" placeholder="Enter your first name." />
  </div>,
  document.getElementById("root")
);

```

# Practice

index.js
```Javascript
import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));

//1. Apply CSS styles to App.jsx component
//to match the appearance on the completed app:
//https://c6fkx.csb.app/
//2. Extract the contact card as a reusable Card component.
//3. Use props to render the default Beyonce contact card
//so the Card component can be reused for other contacts.
//4. Import the contacts.js file to create card components.
```

App.jsx
注意是如何把contacts数据导入进来的
```Javascript
import React from "react";
import Card from "./Card.jsx";
import contacts from "../contacts";
// 在应用的时候总是需要{}把js object
function App() {
  return (
    <div>
      <h1 className="heading">My Contacts</h1>
      <Card
        name={contacts[0].name}
        img={contacts[0].imgURL}
        tel={contacts[0].phone}
        email={contacts[0].email}
      />
      <Card
        name={contacts[1].name}
        img={contacts[1].imgURL}
        tel={contacts[1].phone}
        email={contacts[1].email}
      />
      <Card
        name={contacts[2].name}
        img={contacts[2].imgURL}
        tel={contacts[2].phone}
        email={contacts[2].email}
      />
    </div>
  );
}

export default App;
```

Card.jsx
```Javascript
import React from "react";

function Card(props) {
  return (
    <div className="card">
      <div className="top">
        <h2 className="name">{props.name}</h2>
        <img className="circle-img" src={props.img} alt="avatar_img" />
      </div>
      <div className="bottom">
        <p className="info">{props.tel}</p>
        <p className="info">{props.email}</p>
      </div>
    </div>
  );
}

export default Card;
```

contact.js
```Javascript
const contacts = [
  {
    name: "Beyonce",
    imgURL:
      "https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg",
    phone: "+123 456 789",
    email: "b@beyonce.com"
  },
  {
    name: "Jack Bauer",
    imgURL:
      "https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg",
    phone: "+987 654 321",
    email: "jack@nowhere.com"
  },
  {
    name: "Chuck Norris",
    imgURL:
      "https://i.pinimg.com/originals/e3/94/47/e39447de921955826b1e498ccf9a39af.png",
    phone: "+918 372 574",
    email: "gmail@chucknorris.com"
  }
];

export default contacts;
```

# React DevTools
React Developer Tools by Meta on Chrome Store https://github.com/facebook/react/tree/main/packages/react-devtools#the-react-tab-doesnt-show-up 

看如何把Avatar和Info给提取出来，然后在Card.js复用
Avatar.jsx
```Javascript
import React from "react";

function Avatar(props) {
  return <img className="circle-img" src={props.img} alt="avatar_img" />;
}
export default Avatar;
```


Info.jsx
```Javascript
import React from "react";

function Info(props) {
  return <p className="info">{props.info}</p>;
}

export default Info;
```

Card.jsx
```Javascript
import React from "react";
import Avatar from "./Avatar.jsx";
import Info from "./Info.jsx";

function Card(props) {
  return (
    <div className="card">
      <div className="top">
        <h2 className="name">{props.name}</h2>
        <Avatar img={props.img} />
      </div>
      <div className="bottom">
        <Info info={props.tel} />
        <Info info={props.email} />
      </div>
    </div>
  );
}

export default Card;
```

# Mapping Data to Components
如何用loop把重复数据给清理掉，看App.js的变化

App.js
用了一个contacts.map()来把信息传进去
createCard函数返回的就是<key, value>pair
一定要有一个key
```Javascript
import React from "react";
import Card from "./Card";
import contacts from "../contacts";

function createCard(contact) {
  return (
    <Card
      key={contact.id}
      id={contact.id}
      name={contact.name}
      img={contact.imgURL}
      tel={contact.phone}
      email={contact.email}
    />
  );
}

function App() {
  return (
    <div>
      <h1 className="heading">My Contacts</h1>
      {contacts.map(createCard)}
      {/* <Card
        name={contacts[0].name}
        img={contacts[0].imgURL}
        tel={contacts[0].phone}
        email={contacts[0].email}
      />
      <Card
        name={contacts[1].name}
        img={contacts[1].imgURL}
        tel={contacts[1].phone}
        email={contacts[1].email}
      />
      <Card
        name={contacts[2].name}
        img={contacts[2].imgURL}
        tel={contacts[2].phone}
        email={contacts[2].email}
      /> */}
    </div>
  );
}

export default App;
```

Card.jsx
不能直接引用key，需要用一个新的id
```Javascript
import React from "react";
import Avatar from "./Avatar.jsx";
import Info from "./Info.jsx";

function Card(props) {
  return (
    <div className="card">
      <div className="top">
        <h1>{props.id}</h1>
        <h2 className="name">{props.name}</h2>
        <Avatar img={props.img} />
      </div>
      <div className="bottom">
        <Info info={props.tel} />
        <Info info={props.email} />
      </div>
    </div>
  );
}

export default Card;
```