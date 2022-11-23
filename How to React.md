# What is React?
* "A JavaScript library for building user interfaces" – reactjs.org
* Used to generate Web Pages using JavaScript, JSX (HTML like code) and Virtual DOM
* It's smallish library that can be part of bigger framework (CRT, Next.JS and others)

### Sample React code:
```
import Image from "next/image";
import { useMemo, useState } from "react";
  
const Hello = () => {
  const [quantity, setQuantity] = useState(0);
  const welcomes = useMemo(() => {
    return Array.from(Array(quantity)).map((_, i) => {
      return <Hello2i key={i} />;
    });
  }, [quantity]);
  
  return (
    <>
      <p className="flex">
        <span className="mr-5 text-red-500">const</span>sayHelloTo = (
        <Logo />) {" => {"}
      </p>
      <p className="mt-5 ml-20 flex">
        {"print('Hello ' + "}
        <Logo />
        {")"}
      </p>
      <p>{"}"}</p>
      <div className="mt-10 flex">
        <button
          className="mr-10 rounded-md border p-2"
          onClick={() => setQuantity((prev) => prev + 1)}
        >
          RUN
        </button>
        <button
          className="mr-10 rounded-md border p-2"
          onClick={() => setQuantity(0)}
        >
          CLEAR
        </button>
      </div>
      {welcomes}
    </>
  );
};
  
export default Hello;
  
const Logo = () => (
  <Image
    className="ml-3 mr-3 flex"
    src="/icon-logo.svg"
    alt="2iLogo"
    width={40}
    height={40}
  />
);
  
const Hello2i = () => (
  <p className="mt-5 flex">
    Hello <Logo />
  </p>
);
```

### Results in web page showing:
![[hello2i.png]]

With RUN button which on every click adds new Hello 2i text and clear button which clears all Hello 2i messages. 

# Why use it?
* You can use same language for front end and back end dev (JavaScript/TypeScript)
* It is widely adopted and has great community and documentation
* It is supported by many libraries that make coding easy

# How to start with React
### Pre requirements
* Node.js (preferably LTS)
	* On Windows 10 and newer: `winget install OpenJS.NodeJS.LTS`
	* On most Linux distributions you can use nvm `https://github.com/nvm-sh/nvm` and install node with `nvm install --lts`

### Some recommended ways to start with React
There are few ways to start making React app. Before we mention them is good to know some useful abbreviations/technologies.

* SSR - Server Side Rendering. App is also rendered on server, giving faster first loading time, much easier SEO (as the search engine robots can see whole html instead of dummy page) and much better performance on weaker devices. It's default on some of the libraries/frameworks.
* bundler - program used to build ready to deploy package. It collects all of your code and creates bundle(s) ready to deploy.
* SSG - Static Site Generation - code is compiled to html. It's extremely fast method but
* Frontend - focus on what's shown to end user in the browser
* Backend - focus on server side code - api, responding to html requests, etc.
* Full stack - Frontend and Backend together. Whole app including server and html rendering site.

* ### Vite
	* It's a builder that lets you create an app using popular frameworks/libraries
	* `npm create vite@latest`
	* Creates front end app
	* Fast (much times faster than popular in past `create-react-app`)
	* It includes only basic libraries / easy to maintain
	* It's easy to configure and adopt for production 
	* No built-in SSR
	* [More on Vite](https://vitejs.dev/guide/why.html)
* ### Next.js
	* `npx create-next-app@latest`
	* Full stack node framework with api, easy routing and other features. You don't need to use express and 
	* Fast
	* Includes helpful libraries
	* Helps enforce good programming practices, especially when used with TypeScript
	* By default using Server Side Rendering (but can work like traditional react app)
	* It enforces safe web programming practices, together with TypeScript it's hard to create bad next app
	* [More on Next.js](https://nextjs.org/)

* ### t3-app
	* `npm create t3-app@latest`
	* it will let you create full stack app with `Next.js`, `tRPC`, `tailwind css`, `typescript` and `NextAuth.js`
	* It's good to start your learning with - template has safe authentication, SSR, good style manager built in and follows established trends (it's not cutting edge React technology but close, stable enough to use in commercial projects)
* ### Astro
	* `npm create astro@latest`
	* It's SSG builder/framework. It's great for simple pages (portfolio, blogs, other static pages)
	* Most of the app is packaged directly to html, great solution where performance is important
	* It can be limiting for someone who wants to build single page app. 
* ### Remix
	* `npx create-remix@latest`
	* Full stack framework with many features built in
	* Built in solutions for most problems, from database connection to deployment
	* Enforces good coding techniques
	* Has built in templates that will allow you to deploy to traditional server with node and PostgreSQL, Node with SQLite or cloud serverless function with DynamoDB.
	* If it doesn't support technology you use it might be hard to adapt

* ### create-react-app
	* It's slow (uses webpack), heavy and creates harder to maintain packages (depends on a lot of libraries which are hard to keep up to date if you want to change their config for deployment)

## On TypeScript
* JavaScript with types
* More coding less debugging
	* According to Airbnb using typescript helped prevent 38% of the bugs
	* It would've helped with some bugs we had in 2i Apps
* Easy to learn if you used JavaScript or any typed language
* Thanks to tooling it's compiled to vanilla JavaScript, you get type safety in code and 100% combability when deployed
* By default supported as an option by Vite and Next.js
* ECMA (organisation that standardises JavaScript) is looking to implement TypeScript syntax into one of the coming ECMAScript releases. That means that TypeScript could be natively supported by browsers in the future
* It became most commonly used React language in 2022 for a reason :)

# JSX
It's a tag syntax, similar to HTML but converted to JavaScript by compiler.
You can create elements:
```
const HelloElement: NextPage<{ who: string }> = (props) => (
  <p>Hello, {props.who}!</p>
);
```
And use them like:
`<HelloElement key={i} who="2i" />`
Resulting in web page showing:
`Hello, 2i!`

### There are some basic jsx elements built in to React, like
`<button>PRESS ME</button>`
`<div>SOME CONTENT</div>`
`<a href="https://www.reactjs.org"> link </a>`
There is also React.Fragment 
`<React.Fragment>SOME CODE</React.Fragment>` or simply `<>SOME CODE</>`
You can use it to return multiple elements
``` 
return (
      <React.Fragment>
		<td>Hello</td>
        <td>World</td>
      </React.Fragment> 
);
```

### JSX Properties
You can pass properties to JSX elements, some of more common ones are:
`className` - takes a string which is converted to html class tag. `<div className='red'>RED</div>` will result in page showing `<div class='red'>RED</div>`. Word `class` is recserved in JavaScript, that's why it's important not to mistake `className` with `class`.
`id` - same as HTML id. Example: `<button id='save-customer-button'>SAVE CUSTOMER</button>`
`key` - used to differentiate between iterable components. 
```
const table = [
    <li key="A">First item</li>,
    <li key="B">Second item</li>,
    <li key="C">Third item</li>,
]
```

[More on JSX](https://reactjs.org/docs/jsx-in-depth.html#gatsby-focus-wrapper)

# Hooks
Hooks are functions which allow you to interact with Reacts state and rendering features without using classes and inheritance.
React hooks start with `use`.

### Importing hooks
You can import built in hooks with React, for example:
`import React, { useState, useEffect, useMemo } from 'react';`
Or use them directly from React object: `React.useState(0)`

### useState
useState returns and array with two elements, current state and function with which you can update the state. You can pass initial state as a prop. 
```
const quantity = useState(1337);
console.log(quantity[0]) // 1337
```
or more commonly used:
```
const [quantity, setQuantity] = useState(1337);
console.log(quantity); // 1337
```

State setter triggers re-render and new state value is used at the new render.
```
const [quantity, setQuantity] = useState(1337);
setQuantity(1338)
console.log(quantity);
```
Will print out `1337` first, then `1338` and run in loop as setCount will trigger re-render every time element is rendered.

We can prevent loop from happening by triggering setter on customer action:
```
import React, { useState } from "react";

const SayHello = () => {
  const [quantity, setQuantity] = useState(0);
  return (
    <>
      <button onClick={() => setQuantity(quantity + 1)}>SAY HELLO</button> // BUTTON
      {Array.from(Array(quantity)).map((_, i) => (
        <p key={i}>Hello!</p> // creates Hello! elements array equal in size to 
      ))}
    </>
  );
};

export default SayHello;

```
In the case above quantity is changed only when user clicks on SAY HELLO button. 

### Closures in React
The problem starts when there might be multiple changes caused by one event, like:
```
import React, { useState } from "react";

const SayHello = () => {
  const [quantity, setQuantity] = useState(0);
  const clickHandler = () => {
    setQuantity(quantity + 1);
    setQuantity(quantity + 1);
  };
  return (
    <>
      <button onClick={clickHandler}>SAY HELLO</button>

      {Array.from(Array(quantity)).map((_, i) => (
        <p key={i}>Hello!</p>
      ))}
    </>
  );
};

export default SayHello;

```
It looks like on every click quantity should go up by 2.  But when we test it only goes up by 1. This is common mistake caused by the way JavaScript and React work. `clickHandler` is a [closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures) where `quantity` is set to given value at render. If quantity equals `0` then running
```
setQuantity(quantity + 1);
setQuantity(quantity + 1);
```
is the same as running
```
setQuantity(0 + 1);
setQuantity(0 + 1);
```
Where both lines set quantity to `1`. We can solve this by using a function as a property for `setQuantity`:
```
function increment(it: number) {
	return it + 1;
}
const clickHandler = () => {
	setQuantity(increment);
	setQuantity(increment);
}
```

Or whole element using [Arrow Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
```
import React, { useState } from "react";

const SayHello = () => {
  const [quantity, setQuantity] = useState(0);
  const clickHandler = () => {
    setQuantity((it) => it + 1);
    setQuantity((it) => it + 1);
  };
  return (
    <>
      <button onClick={clickHandler}>SAY HELLO</button>
      {Array.from(Array(quantity)).map((_, i) => (
        <p key={i}>Hello!</p>
      ))}
    </>
  );
};

export default SayHello;

```

### useEffect
