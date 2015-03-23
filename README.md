# react-primer-draft

## Table of Contents

- [Part 1: Intro to React](#intro-to-react)
  - [0.0: What People are saying about React](#what-people-are-saying-about-react)
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

This `primer` is a means to get you rapidly ready to start working with a `React` application. Its goal is not to teach and explain everything, but merely introduce concepts and help you form the right questions to ask and to have an idea of where to look for an answer. It is OK if you do not understand everything at first, just keep working at it by commiting the code you see to muscle memory and reading up on the documentation. Hopefully through `reflection`, and `incubation`, the concepts here will start to make sense.

Don't be afraid of `React` either.  It may seem `complex` but it is quite simple, the `API` is very small, there is only like ~12 methods you will really actually ever use:

1. `render`
2. `getInitialState`
3. `getDefaultProps`
4. `propTypes`
5. `mixins`
6. `componentWillMount`
7. `componentDidMount`
8. `componentWillReceiveProps`
9. `shouldComponentUpdate`
10. `componentWillUpdate`
11. `componentDidUpdate`
12. `componentWillUnmount`

### What people are saying about React:

>
> ---
> My favorite part of React is what I loved about MooTools: to use it effectively you learn JavaScript, not a DSL: useful your whole career.
> -  [Ryan Florence (@ryanflorence)](https://twitter.com/ryanflorence/status/577685415919898625)
>
> ---
>
> `#reactjs` Haven’t been so excited about programming since learned Rails: http://facebook.github.io/react ! Kudos [@floydophone](https://twitter.com/floydophone) & FB team!
> - [Justin Gordon (@railsonmaui)](https://twitter.com/railsonmaui/status/503626150149492736)
>
> ---
>
> “It wasn’t my intention to use React for everything, but I found myself moving so quickly that I found I’d used it everywhere… had a blast”
> - [Alan Hogan (@AlanHogan)](https://twitter.com/alanhogan/status/507307487062544384)
>
> ---
>

[Remember to just give it 5 minutes](https://signalvnoise.com/posts/3124-give-it-five-minutes).

### React Component

A `React` component encapsulates everything. It does not seperate the `view` from the `view logic`, but rather merges the two together. The seperation of concerns does not really make sense when building a `ui`, the `view` and its `view logic` are inevitably tightly coupuled. Rather than jumping between a `template file` and some sort of `view-controller` it makes sense to keep them together. `React` `components` are usually small enough that this is not a big deal to have the two together, and if it does get to be too large you can break down your `component` into smaller `components`.  

A key point from the `React` documentation:

> ## Components are Just State Machines
> React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.
>
> In React, you simply update a component's state, and then render a new UI based on this new state. React takes care of updating the DOM for you in the most efficient way.

Read more: [Interactivity and Dynamic UIs](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

### React JSX

`JSX` is pretty interesting. It basically, allows us to write `HTML` / `XML` like syntax within our `React` `components`. Of course this wouldn't work if you tried to do that then serve it. Choosing to write your `React` `component` in `JSX` requires a `transform` process. This is typically handled through a `build` process or tool, like `webpack`.

```js
var Button = React.createClass({
	render: function() {
		return (
 			<a className="btn btn-default">I am a button! Click me!</a>
		);
 	}
});
```

Here you can see a `React` `component` has a `render` `function`, which outputs the `markup`. We can easily see, at a glance exactly what the output will be.

[JS Bin](http://jsbin.com/tapupafeqe/1/edit?html,js,output)

Read more: [JSX in Depth](https://facebook.github.io/react/docs/jsx-in-depth.html)

### React Supported Attributes

`React`, works with most common `HTML` elements, for example:

```js
var Link = React.createClass({
	render: function() {
		return (
			<a href="http://google.com">Google</a>
		);
	}
});

```

You just made a `a` tag. It can now be called via `<Link />`.

[JS Bin](http://jsbin.com/vahezonoyi/1/edit?html,js,output)

Read more: [React Tags and Attributes](http://facebook.github.io/react/docs/tags-and-attributes.html)

### React Supported Events

`React` also supports `browser` events.  Lets go back to our `Link` example:

```js
var Link = React.createClass({
	render: function() {
		return (
			<a href="http://google.com" onClick={this.handleClick}>Google</a>
		);
	},

	handleClick: function(e) {
		e.preventDefault();

		alert('You clicked me!');
	}
});

```

[JS Bin](http://jsbin.com/vahezonoyi/2/edit?html,js,output)

Now, I know what you're thinking. `Inline events`, isn't that bad? It looks like its `inline` but its really not. `React` will attach the event for you via `event delegation`. So now we have a very declarative well to associate events to `DOM` elements. Now there's no confusion as to what `elements` have what `events` and there is no hassle for `managing` `ids`.

Here's a key point from the `React` documentation:

> #### [Event Handling and Synthetic Events](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#event-handling-and-synthetic-events)
> With React you simply pass your event handler as a camelCased prop similar to how you'd do it in normal HTML. React ensures that all events behave identically in IE8 and above by implementing a synthetic event system. That is, React knows how to bubble and capture events according to the spec, and the events passed to your event handler are guaranteed to be consistent with the W3C spec, regardless of which browser you're using.
>
> If you'd like to use React on a touch device such as a phone or tablet, simply call `React.initializeTouchEvents(true);` to enable touch event handling.
>
> ---
>
> #### [Under the Hood: Autobinding and Event Delegation](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#under-the-hood-autobinding-and-event-delegation)
>
> **Autobinding:** When creating callbacks in JavaScript, you usually need to explicitly bind a method to its instance such that the value of this is correct. With React, every method is automatically bound to its component instance. React caches the bound method such that it's extremely CPU and memory efficient. It's also less typing!
>
> **Event delegation:** React doesn't actually attach event handlers to the nodes themselves. When React starts up, it starts listening for all events at the top level using a single event listener. When a component is mounted or unmounted, the event handlers are simply added or removed from an internal mapping. When an event occurs, React knows how to dispatch it using this mapping. When there are no event handlers left in the mapping, React's event handlers are simple no-ops. To learn more about why this is fast, see David Walsh's excellent blog post.

In the example, we define a function, and simply pass the function to the `onClick` property.

When the `click event` occurs, we receive back a `synthetic event`, can do with it as we please. `e.preventDefault()` to stop the `event propagation`, or get things like `e.target`.

Read more: [React Events](http://facebook.github.io/react/docs/events.html)

#### React Supported Events Continued

You might find yourself wanting to get back a `value` or do something like add a custom `data-attribute`,  a common pattern from the `jQuery` days.

```js
var Link = React.createClass({
	render: function() {
		return (
			<div>
				<a href="http://google.com" onClick={this.handleClick} data-link="Google">Google</a>
                <br />
				<a href="http://facebook.com" onClick={this.handleClick} data-link="Facebook">Facebook</a>
			</div>
		);
	},

	handleClick: function(e) {
		e.preventDefault();

		alert('You clicked ' + e.target.getAttribute('data-link'));
	}
});

```

[JS Bin](http://jsbin.com/vahezonoyi/3/edit?html,js,output)

It's actually totally unnecessary to do that. You can instead do `currying`. It looks something like this:

```js
var Link = React.createClass({
	render: function() {
		return (
			<div>
				<a href="http://google.com" onClick={this.handleClick.bind(null, 'Google')}>Google</a>
                <br />
				<a href="http://facebook.com" onClick={this.handleClick.bind(null, 'Facebook')}>Facebook</a>
			</div>
		);
	},

	handleClick: function(linkName, e) {
		e.preventDefault();

		alert('You clicked ' + linkName);
	}
});
```

[JS Bin](http://jsbin.com/vahezonoyi/4/edit?html,js,output)

`JavaScript Is Sexy` describes `currying` as follows:

> Function Currying, also known as partial function application, is the use of a function (that accept one or more arguments) that returns a new function with some of the arguments already set. The function that is returned has access to the stored arguments and variables of the outer function. This sounds way more complex than it actually is, so let’s code.

We apply `null` instead of `this`, because we are only passing `values` that do not rely on `this`. When the `link` gets clicked, it will return the `value` from the `bind` and then the last argument will be our `event`.

Another Key point from `JavaScript Is Sexy`:

> When we use the bind () method for currying, all the parameters of the greet () function, except the last (rightmost) argument, are preset. So it is the rightmost argument that we are changing when we call the new functions that were curried from the greet () function. Again, I discuss currying at length in a separate blog post, and you will see how we can easily create very powerful functions with Currying and Compose, two Functional JavaScript concepts.

Read more: [Currying](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)

Read more: [Understand Javascript's "this" with Clarity and Master It](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

Read more: [React Autobinding](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#under-the-hood-autobinding-and-event-delegation)

### React Props

`Props` are `properties`. They are `immutable`, and useful for passing data from a `parent` to a `child`. One thing to note about `props` is that they are `immutable`, that means the `component` **cannot** **change** them. To change the `props`, the `Parent` must trigger a `render`, where it passes `new props` to the `child component`. `Props` flow downward like a waterfall.

```js
// Parent Component
var LikeList = React.createClass({
	render: function() {
		return (
			<ul>
				<LikeListItem text='turtles.' />
			</ul>
		);
	}
});


// Child Component
var LikeListItem = React.createClass({
	render: function() {
		return (
			<li>
				{this.props.text}
			</li>
		);
	}
});
```

Here we have the `Parent Component`, `LikeList`, render a `unordered list`, with one `child`, a `LikeListItem`. In the `LikeListItem`, we pass a property known as `text`. 

`Props` are avaliable within a `component` via `this.props`. To access `text` we do `this.props.text`. Here we simply call it in our `render` `function`.

[JS Bin](http://jsbin.com/rerazageku/1/edit?html,js,output)

Read more: [Transferring Props](https://facebook.github.io/react/docs/transferring-props.html)

#### getDefaultProps

If we do not pass down `props` from the `Parent`, we can have the `child` set some `default` `props` with the `getDefaultProps` method.

```js
// Parent Component
var LikeList = React.createClass({
	render: function() {
		return (
			<ul>
				<LikeListItem />
			</ul>
		);
	}
});


// Child Component
var LikeListItem = React.createClass({
    getDefaultProps: function() {
      return {
        text: 'N/A'
      };
    },

	render: function() {
		return (
			<li>
				{this.props.text}
			</li>
		);
	}
});
```

If no `props` is set for `text`, we give it a `default` `value` of `N/A`. Inside the function we must `return` a `object {}`.

[JS Bin](http://jsbin.com/volisofase/2/edit?html,js,output)

Read more: [Default Prop Values](https://facebook.github.io/react/docs/reusable-components.html#default-prop-values)

#### propTypes

A useful way of documenting your `React` `components` that use `props`, is `propTypes`. When `Prop Validation` fails, you will get a notice inside your `dev console`. Check the `Read more` link to see all the available options.

A key point from the `React` `documentation`:

> ##### [Prop Validation](https://facebook.github.io/react/docs/reusable-components.html#prop-validation)
> As your app grows it's helpful to ensure that your components are used correctly. We do this by allowing you to specify propTypes. React.PropTypes exports a range of validators that can be used to make sure the data you receive is valid. When an invalid value is provided for a prop, a warning will be shown in the JavaScript console. Note that for performance reasons propTypes is only checked in development mode. Here is an example documenting the different validators provided:
> ...

Example:

```js
// Child Component
var LikeListItem = React.createClass({
	propTypes: {
		text: React.PropTypes.string
	},

	getDefaultProps: function() {
 		return {
 			text: 'N/A'
      		};
    	},

	render: function() {
		return (
			<li>
				{this.props.text}
			</li>
		);
	}
});
```

Here we declare that the `text` property, must  be a `string`.

If we wanted to`require` the `text` `prop`, we can chain it with `isRequired`, like so:

```js
// Child Component
var LikeListItem = React.createClass({
	propTypes: {
		text: React.PropTypes.string.isRequired
	},
...
```

Read more: [Prop Validation](https://facebook.github.io/react/docs/reusable-components.html#prop-validation)

### React State

As `Pete Hunt` would say, *__state is the root of all evil__*. But it's a necessary one... unfortunately. In `React`, `state` is `mutable`, that means you can change it. When `state` changes, the `component` will trigger a `render`, and the whole tree will `rerender`, but don't worry. `React` has pretty good performance out of the box and does intelligent things like `diffing` the `virtual DOM`, so only the differences are applied.

Where might state be useful?

Good question, let's consider a simple example... with something everyone should know: `jQuery`.

```html
<!--  index.html -->
<body>
  Do you like fish sticks?
  
  <br /><br />
  
  Response: I <span id="response">______</span> fishsticks.
  
  <br /><br />
  
  <a id="like" class="btn btn-success">I like it.</a>
  <a id="dislike" class="btn btn-danger">I dislike it.</a>  
</body>

```

```js
// logic.js
$('#like').on('click', function(e) {
  e.preventDefault();

  $('#response').text('like');
});

$('#dislike').on('click', function(e) {
  e.preventDefault();

  $('#response').text('dislike');
});
```

Looks simple enough right? We want to update the response with either `like` or `dislike`. As you can imagine, thing start to get more complicated as we add more event logic. The code eventually becomes a lot harder to follow, because there be events all over the place modifying the `DOM` and you wouldn't be able to tell without going through all the logic. It's no fun having to take in the entire flow of the application at once.

Let's take a look at how this would look in `React`.

```js
var LikeComponent = React.createClass({
	getInitialState: function() {
		return {
			response: ''
		};
	},

	render: function() {
		return (
			<div>
				Do you like fish sticks?

				<br /><br />

				Response: I {this.state.response || '_____'} fishsticks.

				<br /><br />

				<a className="btn btn-success" onClick={this.handleLike}>I like it.</a>
				<a className="btn btn-danger" onClick={this.handleDislike}>I dislike it.</a>
			</div>
		);
	},

	handleLike: function(e) {
		e.preventDefault();

		this.setState({
			response: 'like'
		});
	},

	handleDislike: function(e) {
		e.preventDefault();

		this.setState({
			response: 'dislike'
		});
	}
});
```

[JS Bin](http://jsbin.com/naruvavaqi/3/edit?html,js,output)

You can see a few new methods here. Let's start with `getInitialState`, it works similiar to `getDefaultProps`. 

Before we can call `this.state` inside our `render` `function`, we need to use `getInitialState` to set up the `default` `values`, once we set it up we can call things like `this.state.response`, much like `this.props`.

** NOTE: ** Don't use `props` to set your `initial state`. It's a `anti-pattern` and it is only `acceptable`, when you do something like call the `prop` something like: `initialCount`. 

Key Point:

> #### [Props in getInitialState Is an Anti-Pattern](https://facebook.github.io/react/tips/props-in-getInitialState-as-anti-pattern.html)
>
> ---
>
> Using props, passed down from parent, to generate state in getInitialState often leads to duplication of "source of truth", i.e. where the real data is. Whenever possible, compute values on-the-fly to ensure that they don't get out of sync later on and cause maintenance trouble.

Read more: [Props in getInitialState Is an Anti-Pattern](https://facebook.github.io/react/tips/props-in-getInitialState-as-anti-pattern.html), please review this to see acceptable usage patterns.

Read more: [State](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

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
