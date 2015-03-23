# react-primer-draft

## Table of Contents

- [Part 1: Intro to React](#intro-to-react)
  - [1.0: React Component](#react-component)
  - [1.1: React JSX](#react-jsx)
  - [1.1: React Props](#react-props)
  - [1.2: React State](#react-state)
  - [1.3: React Lifecycle Events](#react-lifecycle-events)
  - [1.4: React Dynamic Children](#react-dynamic-children)
  - [1.5: React Nested Views](#react-nested-views)
  - [1.6: React Pure Render](#react-pure-render)
  - [1.7: React and 3rd Party Libraries](#react-and-3rd-party-libraries)
  - [1.8: React Developer Tools](#react-dev-tools)
- [Part 2: Harmony AKA ES6 AKA ES2015](#es2015)
  - [2.1: CONST and LET](#const-and-let)
  - [2.2: Fat Arrow](#fat-arrow)
  - [2.3: Classes](#classes)
  - [2.4: Babel](#babel)
- [Part 3: Useful Libraries](#useful-libraries)
  - [3.1: Superagent](#superagent)
  - [3.2: Bluebird](#bluebird)
  - [3.3: lodash](#lodash)
- [Part 4: Webpack](#webpack)
  - [4.1: Hot Module Replacement and Hot Reloading](#hot-module-replacement-and-hot-reloading)
- [Part 5: React Router](#react-router)
- [Part 6: Flux](#flux)
  - [6.1: Alt](#alt)
    - [6.1.1: Alt Actions](#alt-actions)
    - [6.1.2: Alt Stores](#alt-stores)
- [Part 7: Testing](#testing)
    - [7.1: Mocha](#mocha) 

---

## Intro to React

`React` is a `JavaScript` library by `Facebook`, it describes itself as *__a javascript library for building user interfaces__*.

Developers often call it the `V in MVC`, or talk about the its `virtual DOM` (not to be confused with the `shadow DOM`). I like `React` for its `declartive` style, `lifecycle event hooks`, and the fact that a `React` `component` describes its view at anytime. By breaking down the `view` into `components`, writing `React` starts to become very natural and a pleasure to work with, as you no longer need to understand the entire flow of the application at once, you can start at a `component` and work your way up or down.

This `primer` is a means to get you rapidly ready to start working with a `React` application. Its goal is not to teach and explain everything, but merely introduce concepts and help you form the right questions to ask and to have an idea of where to look for an answer. It is OK if you do not understand everything at first, just keep working at by commiting the code you see to muscle memory and reading up on the documentation. Hopefully through `reflection`, and `incubation`, the concepts here will start to make sense. 

### React Component

A `React` component encapsulates everything. It does not seperate the `view` from the `view logic`, but rather merges the two together. The seperation of concerns does not really make sense when building a `ui`, the `view` and its `view logic` are inevitably tightly coupuled. Rather than jumping between a `template file` and some sort of `view-controller` it makes sense to keep them together. `React` `components` are usually small enough that this is not a big deal to have the two together, and if it does get to be too large you can break down your `component` into smaller `components`.  

A key point from the `React` documentation:

> ## Components are Just State Machines
> React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.
>
> In React, you simply update a component's state, and then render a new UI based on this new state. React takes care of updating the DOM for you in the most efficient way.

Read more: [https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

### React JSX

`JSX` is pretty interesting. It basically, allows us to write `HTML` / `XML` like syntax within our `React` `components`. Of course this wouldn't work if you tried to do that then serve it. Choosing to write your `React` `component` in `JSX` requires a `transform` process. This is typically handled through a `build` process or tool, like `webpack`.

```javascript
var Button = React.createClass({
	render: function() {
		return (
 			<a className="btn btn-default">I am a button! Click me!</a>
		);
 	}
});
```

[JS Bin](http://jsbin.com/tapupafeqe/1/edit?html,js,output)

Read more: [https://facebook.github.io/react/docs/jsx-in-depth.html](https://facebook.github.io/react/docs/jsx-in-depth.html)

### React Props

### React State

### React Lifecycle Events

### React Dynamic Children

### React Pure Render

### React and 3rd Party Libraries

### React Developer Tools

---

## ES2015

### const and let


---

## 

---

## LICENSE

Copyright (c)  2015  Michael Chau.

Permission is granted to copy, distribute and/or modify this document  
under the terms of the GNU Free Documentation License, Version 1.3  
or any later version published by the Free Software Foundation;  
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.  
A copy of the license is included in the section entitled "GNU  
Free Documentation License".  
