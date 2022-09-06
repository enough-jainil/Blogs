## React Cheat Sheet for Beginners

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1662450919669/D4z8fSkFv.png)

A quick and simple overview of React for beginners to get started

It might seem overwhelming for a beginner to learn the React framework. After all, it has gone through a lot of changes since it was first released around 2013. Here’s a cheat sheet, **not a full tutorial** but a simple-to-understand and concise overview of what it takes to learn React.

Intro to React
==============

What is React?
--------------

It is a JavaScript library designed to create single-page applications with reusable UI components.

How does it work?
-----------------

React stores the information DOM by creating a virtual DOM in its memory. Before it renders the DOM nodes onto the browser, it checks for changes between its past and presents virtual DOM. If there’s a change (i.e. some text content updated), it will update its virtual DOM and then renders to the real DOM on the browser. See the diagram below for visualization.

![virtual DOM](https://i0.wp.com/blog.codecentric.de/files/2017/11/Bildschirmfoto-2017-10-25-um-14.32.03.png?resize=477%2C383&ssl=1 "React Cheat Sheet for Beginners 36")

Because DOM manipulations can take a lot of time to load, React only changes the DOM nodes that need to be changed.

Intro to JSX
------------

A very important concept to learn in React is JSX. It is short for JavaScript XML. Simply put, it allows you to write HTML in React code.

For example, take a look at these 2 code blocks ([source](https://www.w3schools.com/react/react_jsx.asp)):

//Using JSX
const myelement = <h1>I Love JSX!</h1>;
ReactDOM.render(myelement, document.getElementById('root'));

//Not using JSX
const myelement = React.createElement('h1', {}, 'I do not use JSX!');
ReactDOM.render(myelement, document.getElementById('root'));

As you can see, using JSX allows us to write HTML elements in React code more easily and faster.

ReactDOM.render()
-----------------

Notice that there is a function: `ReactDOM.render()` at the bottom of the code blocks above. `ReactDOM.render()` is a function that takes 2 arguments: the HTML code and the HTML element to render the code.

In React, the top node is known as the ‘root’ node. Therefore, we usually render our HTML code in it.

Components
----------

Components are one of the building blocks of a React App. They are React functions that return an HTML element. Think of them as large HTML blocks of code that independently does a certain function for the app. Like the navigation bar or the panels.

In React, all these components are structured as nodes in the Virtual DOM. They will then render onto the browser according to how we specify them to look. See diagram for visualization.

![Components](https://i0.wp.com/miro.medium.com/max/1400/1*dL1czrP7D0LIhUZfA8-XEA.png?resize=614%2C218&ssl=1 "React Cheat Sheet for Beginners 37")

There are 2 types of components currently in React: Class and Functional.

Class Components
----------------

As its name suggests, class components are classes written in the context of React. A rule in writing components is to always name the component with a capital letter.

Let’s write a simple House class component.

1.  Import react and react-dom
2.  Write the class House
3.  Call the ReactDOM.render()

//1.
import React from 'react'
import ReactDOM from 'react-dom'
//2.
class House extends React.Component {
  render() {
    return (
      <div>
        <h2>This is a house</h2>
      </div>
    )
  }
}
//3.
ReactDOM.render(<House />, document.getElementById('root'));

To take it a step further, let’s create a Door class and make it a child component of the House (since doors are inside houses).

First, we create the Door class.

class Door extends React.Component {
  render() {
    return (
      <div>
        <h3>This is a door</h3>
      </div>
    )
  }
}

Then we add it inside the House class to make it its child.

class House extends React.Component {
  render() {
    return (
      <div>
        <h2>This is a house</h2>
        <Door /> <!--here is the Door component-->
      </div>
    )
  }
}

The image below shows what the app looks like in the browser. I went ahead and added outlines to each component to show them better. Both classes are displayed perfectly, with the Door being the red outlined box being shown inside the House, as represented by the blue outlined box.

![21FKl9fr7](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615533228165/21FKl9fr7.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 38")

(adsbygoogle = window.adsbygoogle || \[\]).push({});

Function Components
-------------------

The other type of component we can write in React is function components. Just like class components, they returned HTML codes and their names should start with capital letters.

Let’s build the same House and Door as functional components.

import React from "react";
import ReactDOM from "react-dom";

function House() {
  return (
    <div>
    <h2>This is a house</h2>
    <Door/> <!--add Door as child-->
  </div>
  );
}

function Door() {
  return (
    <div>
    <h3>This is a door</h3>
  </div>
  );
}

ReactDOM.render(<House />, document.getElementById("root"));

And that’s it! They pretty much work the same and renders the same HTML elements. Note that for function components, you don’t need to have the `render()` function before the return statement.

Props
-----

React components can have **props**. And props are equivalent to what arguments are to a function or what attributes are to HTML.

Back to our House and Door, let’s say we have many Door components inside the house. How do we distinguish one Door from another? How about giving each Door a `title` prop? To do that, simply add `title` in the Door component like so.

<Door title="front" />

Kind of similar to HTML attributes right? Then in the Door component, we can print out its prop as follows.

//pass props as argument first
function Door(props) {
  return (
    <div>
    <h3>This is the {props.title} door</h3> 
  </div>
  );
}

And our app would print the title out as expected.

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615534532745/Rzn5HqRAw.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 39")

Now we can add lots of Door components inside the House and have `title` to distinguish them.

function House() {
  return (
    <div>
    <h2>This is a house</h2>
    <Door title="front"/>
    <Door title="back"/>
    <Door title="kitchen"/>
    <Door title="bedroom"/>
  </div>
  );
}

The result would look like this:

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615534626548/0HS_MaAxX.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 40")

Just like arguments are to a function, props to Components are just read-only. A Component cannot change the value of the props passed into it.

(adsbygoogle = window.adsbygoogle || \[\]).push({});

States
------

Now let’s briefly talk about states. In React, a state is an object in which variables are stored. These variables can only be accessed within its Component (unless of course, you use some state management tools like Redux).

Let’s add some states to decorate our House class component.

class House extends React.Component {
  constructor(props) {
       super(props);
       this.state = {
            color: "white",
            rooms: 4
       };
  }
  render() {
    return (
      <div>
        <h2>This is a {this.state.color} house with {this.state.rooms} rooms.</h2>
      </div>
    )
  }
}

In the code above, we add our state object to our constructor function. Then we edit the HTML element to return a sentence with the state `color` and `rooms` property. The result will be:

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615535374961/NI0Hwxlxg.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 41")

Basic React Hooks
-----------------

In our previous example, we saw how to use states in our House **class** component. In function components, we can use something called React Hooks to manage our states.

I have a whole series called [A Look at React Hooks](https://reactjs.org/docs/hooks-intro.html) on all the basic React Hooks. Let’s take a look at some of them briefly.

### useState()

This Hook allows function components to initialize and update states. Here’s a simple example.

import React, { useState } from "react";
import ReactDOM from "react-dom";

function House() {
  const \[color, setColor\] = useState("white");
  return (
    <div>
      <h2>This is a {color} house</h2>
    </div>
  );
}

First, initialize the state as “white” inside the `useState` Hook. The Hook returns an array: the value of the state (i.e. color) and its set function, which is used to update the state (i.e. setColor).

Then simply include the value of the state in the return function, and the app will display the state.

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615604248933/qN7hSPZyB.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 42")

For a more detailed explanation of this Hook, please read this [article](https://reactjs.org/docs/hooks-state.html).

### useEffect()

The next most useful Hook you will encounter is the `useEffect` Hook. It performs a function whenever a specified state has changed.

Back to our House component, we add another variable called `door` that will track how many doors this house has. In its `useState` Hook, initialized it to 0.

Then, we add a button that when onClick, will increase the value of `door` by 1. Finally, we have a `useEffect` Hook that will print the number of doors in the house every time the value of `door` is updated.

The code will look as follows:

function House() {
  const \[color, setColor\] = useState("white");
  const \[door, setDoor\] = useState(0); //initialize door as 0

//add 1 to the current value of door on every button click
  const addDoor = () => {
    setDoor(door + 1);
  };

//finally, trigger the function to print the door value whenever door is updated
  useEffect(() => {
    console.log(\`Door count: ${door}\`)
  }, \[door\]);

  return (
    <div>
      <h2>This is a {color} house</h2>
      <button onClick={addDoor}>Add a Door</button>
    </div>
  );
}

The result:

![door.gif](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615605282210/AFeGDsAck.gif?w=1290&ssl=1 "React Cheat Sheet for Beginners 43")

For a more detailed explanation of this Hook, please read this [article](https://reactjs.org/docs/hooks-effect.html).

(adsbygoogle = window.adsbygoogle || \[\]).push({});

Create React App
----------------

Now that we’ve covered the basic concepts of React, let’s take a look at a typical React environment.

First, make sure you have npm and Node.js installed on your machine. If not, get them [here](https://nodejs.org/en/download/).

The easiest way to create a new React app is to execute:

npx create-react-app my-app

Then, navigate to the app folder.

cd my-app

And run the following command to launch the app in localhost.

npm start

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615605607893/DzIVZf9Zk.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 44")

### App Structure

A new Create React App will have the following folder structure.

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615605753589/77OWcPSWC.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 45")

Let’s briefly go through them one by one.

1.  package.json: shows the dependencies and the scripts used in the app.
2.  package-lock.json: make sure dependencies are installed.
3.  .gitignore: files that git will not include in every commit.
4.  Readme: an ordinary markdown file to describe your app.
5.  node\_modules: where all your dependencies are installed.
6.  public folder: won’t touch these files during development.
7.  src folder: where most development will take place.
8.  src/index.js: specifies the ‘root’ element
9.  src/App.js: The App component. Edit this to see what gets rendered onto the browser.
10.  src/App.css: Styling for App.js.

It may seem complex at first. If you are a beginner, try to focus on the `src/App.js` file first. Edit its HTML code, add some basic functions and get a feel for how it works. Once you are more familiar, you can add more files as components into the src folder. Like Home.js for the Home component, Login.js for the Login component, and so on.

Styling
-------

After creating some basic functions and components in your first React app, you may wonder how to customize and style the app for your own needs. In React, there are a few ways to add custom styles. The most common ways are inline styling and importing CSS modules.

### Inline styling

As the name suggests, add the styling inside the HTML element. For example, let’s add a border around our house. The border color depends on our `color` variable.

function House() {
  const \[color, setColor\] = useState("red");
  return (
    <div>
      <h2 style={{"border":\`1px solid ${color}\`}}>This is a {color} house</h2>
    </div>
  );
}

Since the value of `color` is initialized to read, the app will look like this:

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615609969528/nRL7-_Dsh.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 46")

Alternatively, you can create a `style` object and pass it in the style attribute like so:

function House() {
  const \[color, setColor\] = useState("red");

//style obj contains the css
  const style={
    "border":\`1px solid ${color}\`
  }

  return (
    <div>
      <h2 style={style}>This is a {color} house</h2>
    </div>
  );
}

### CSS modules

Another way to style is to create a `.css` file and import it to the React Component. I have created a simple `styles.css` file with the following styling:

h2 {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  padding: 10px 5px;
  border-radius: 10px;
}

Then, in my House component file, import the file as shown below:

import React, { useState } from "react";
import ReactDOM from "react-dom";
import "./style.css"; //import here

//keep everything else the same
function House() {
  const \[color, setColor\] = useState("red");

  const style = {
    border: \`1px solid ${color}\`
  };

  return (
    <div>
      <h2 style={style}>This is a {color} house</h2>
    </div>
  );
}

Now our app will look like this:

![image.png](https://i0.wp.com/cdn.hashnode.com/res/hashnode/image/upload/v1615610452233/QNJnggjzy.png?w=1290&ssl=1 "React Cheat Sheet for Beginners 47")

More to Learn!
--------------

And that’s it for this React Cheat Sheet for beginners. Of course, this is just a very concise article so it cannot cover every single aspect of React. But I do hope it has been a great introduction to at least help anyone embark on a React journey without feeling intimidated or too overwhelmed.

Thanks for reading and if you find it helpful, please like and share this article around for more reach. Cheers!

[Know About The Origin Of React.JS](https://jainil.dev/what-is-react-js-how-can-i-start-with-it/)

<p>The post [React Cheat Sheet for Beginners](https://jainil.dev/react-cheat-sheet-for-beginners/) first appeared on [Jainil Prajapati.](https://jainil.dev).</p>