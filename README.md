# react-primer-draft

## Table of Contents
- [Author's Note](#authors-note)
- [Part 1: Intro to React](#intro-to-react)
  - [0.0: What People are saying about React](#what-people-are-saying-about-react)
  - [1.0: React Component](#react-component)
  - [1.1: React JSX](#react-jsx)
  - [1.2: React Supported Attributes](#react-supported-attributes)
  - [1.3: React Supported Events](#react-supported-events)
  - [1.4: React Supported Events Continued](#react-supported-events-continued)
  - [1.5: React Props](#react-props)
      - [1.5.1: getDefaultProps](#getdefaultprops)
      - [1.5.2: propTypes](#proptypes)
  - [1.6: React State](#react-state)
  - [1.7: React Lifecycle Events](#react-lifecycle-events)
      - [1.7.1: Mounting: componentWillMount](#mounting-componentwillmount)
      - [1.7.2: Mounting: componentDidMount](#mounting-componentdidmount)
      - [1.7.3: Updating: componentWillReceiveProps](#updating-componentwillreceiveprops)
      - [1.7.4: Updating: shouldComponentUpdate](#updating-shouldcomponentupdate)
      - [1.7.5: Updating: componentWillUpdate](#updating-componentwillupdate)
      - [1.7.6: Updating: componentDidUpdate](#updating-componentdidupdate)
      - [1.7.7: Unmounting: componentWillUnmount](#unmounting-componentwillunmount)
  - [1.8: React Dynamic Children](#react-dynamic-children)
  - [1.9: React Nested Views](#react-nested-views)
  - [1.10: React Mixins](#react-mixins)
  - [1.11: React Pure Render](#react-pure-render)
  - [1.12: React and 3rd Party Libraries](#react-and-3rd-party-libraries)
  - [1.13: React Developer Tools](#react-dev-tools)
- [Part 2: Harmony aka ES6 aka ES2015](#es2015)
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

## Authors Note

This primer makes use of several libraries, but it is by *__no__* means a "_React the right way_", or anything like that. It's just introduction to how I am building my own `React` applications. The goal of this primer to help developers interested in `React`, get familiar and dive right in. Maybe you will come up with approaches that work with better for you and I hope that you share them with the community! Or if you're already well versed, help improve this document so others in the community can benefit.

This guide is dedicated to the engineers at `Jellyvision`, we are [hiring](http://www.jellyvision.com/jobs/) so check us out. :D

~ Michael Chau (gh: [@mikechau](https://github.com/mikechau), twtr: [@money_mikec](https://twitter.com/money_mikec))

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

---

### What people are saying about React:

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

---

### React Component

A `React` component encapsulates everything. It does not seperate the `view` from the `view logic`, but rather merges the two together. The seperation of concerns does not really make sense when building a `ui`, the `view` and its `view logic` are inevitably tightly coupuled. Rather than jumping between a `template file` and some sort of `view-controller` it makes sense to keep them together. `React` `components` are usually small enough that this is not a big deal to have the two together, and if it does get to be too large you can break down your `component` into smaller `components`.  

A key point from the `React` `documentation`:

> #### [Components are Just State Machines](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#components-are-just-state-machines)
> React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.
>
> In React, you simply update a component's state, and then render a new UI based on this new state. React takes care of updating the DOM for you in the most efficient way.

Read more: [Interactivity and Dynamic UIs](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

---

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

React.render(<Button />, document.body);
```

Here you can see a `React` `component` has a `render` `function`, which outputs the `markup`. We can easily see, at a glance exactly what the output will be.

[JS Bin](http://jsbin.com/tapupafeqe/1/edit?html,js,output)

**NOTE:** Your `React` `component` needs to always return a single `tag`.

For example, you cannot do something like:

```js
return (
	<div>Test</div>
	<div>Tet 2</div>
);
``` 

It has to be: 

```js
return (
	<div>
		<div>Test</div>
		<div>Test 2</div>
	</div>
);
```


To render a `React` `component` in the body all you need to do is:

```js
React.render(<Button />, document.body);
```

Simply call the `render` method, pass in the `component`, and the `DOM` node you want to render to.

**NOTE:** These examples use `document.body`, but you should avoid using it can there can be subtle bugs.

When `rendering` a `React` `component`, `React` wants complete ownership of the `DOM` node.

So just create a `<div id="content"></div>` and then use `document.getElementById('content')`.

Like so:

```html
<!-- index.html -->

<body>
  <div id="content"></div>
</body>
```

```js
// App.jsx

React.render(<App />, document.getElementById('content'));
```

Read more: [JSX in Depth](https://facebook.github.io/react/docs/jsx-in-depth.html)

---

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

React.render(<Link />, document.body);
```

You just made a `a` tag. It can now be called via `<Link />`.

[JS Bin](http://jsbin.com/vahezonoyi/1/edit?html,js,output)

Read more: [React Tags and Attributes](http://facebook.github.io/react/docs/tags-and-attributes.html)

---

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

React.render(<Link />, document.body);
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

---

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

React.render(<Link />, document.body);
```

[JS Bin](http://jsbin.com/ducavuvoka/1/edit?html,js,output)

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

React.render(<Link />, document.body);
```

[JS Bin](http://jsbin.com/vuhozilibu/1/edit?html,js,output)

`JavaScript Is Sexy` describes `currying` as follows:

> Function Currying, also known as partial function application, is the use of a function (that accept one or more arguments) that returns a new function with some of the arguments already set. The function that is returned has access to the stored arguments and variables of the outer function. This sounds way more complex than it actually is, so let’s code.
> ...

An explanation of `.bind('this', ...)` vs `.bind(null, ...)` by `Morhaus` on `#reactjs`:

> React autobinds methods in the object you pass to `React.createClass()` to the component instance, so using `this.handleClick.bind(null, 'test')` will ensure that behavior is not messed with
>
> ...
>
>  pass null instead, unless you're not using `React.createClass()` but `class extends React.Component`, in which case methods are not auto bound

`this` can be passed to preserve the `context`, or we can pass `null`, if it is not necessary. In this case, since we are using `React.createClass`, `React` will `autobind` for us, so we can just pass `null` and the arguments we want to pass.

Read more: [Currying](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)

Read more: [Understand Javascript's "this" with Clarity and Master It](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

Read more: [React Autobinding](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#under-the-hood-autobinding-and-event-delegation)

Read more: [bind(): React component methods may only be bound to the component instance](https://groups.google.com/forum/#!topic/reactjs/Xv9_kVoJJOw)

Read more: [Partial application in JavasScript with `bind`](https://coderwall.com/p/nw9cxg/partial-application-in-javascript-with-bind)

---

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

React.render(<LikeList />, document.body);
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

React.render(<LikeList />, document.body);
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

#### className

When trying to set the `class` in a element, you need to use `className`, as there are issues using the `class` keyword.

Review: [Tags and Attributes](https://facebook.github.io/react/docs/tags-and-attributes.html) for more details on the supported `HTML` tags and `attributes`.

Review: [Events](https://facebook.github.io/react/docs/events.html) for the supported browser events.

#### Passing a Prop

If you are are passing down a `prop` and it is a `boolean`, you can simply just add the key.

```js
// SomeComponent.jsx
var SomeComponent = React.createClass({
	render: function() {
		return (
			<AnotherComponent checked />
		);
	}
});
```
`AnotherComponent`'s `this.props.checked` would resolve to true.

---

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

React.render(<LikeComponent />, document.body);
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

---

### React Lifecycle Events

`React` has several lifecycle events. This lets you do things at specific points of a `components` lifecycle. The `React` documentation covers this section very well, so we will just quote it and show you some examples of how they work.

Read more: [Component Specs and Lifecycle Events](https://facebook.github.io/react/docs/component-specs.html)

#### Mounting: componentWillMount

`componentWillMount()`

> Invoked once, both on the client and server, immediately before the initial rendering occurs. If you call `setState` within this method, `render()` will see the updated state and will be executed only once despite the state change.

Read more: [componentWillMount](https://facebook.github.io/react/docs/component-specs.html#mounting-componentwillmount)

#### Mounting: componentDidMount

`componentDidMount()`

> Invoked once, only on the client (not on the server), immediately after the initial rendering occurs. At this point in the lifecycle, the component has a DOM representation which you can access via `React.findDOMNode(this) [React 0.13+]` or `this.getDOMNode() [React 0.12.x]`.
>
> If you want to integrate with other JavaScript frameworks, set timers using setTimeout or setInterval, or send AJAX requests, perform those operations in this method.

Read more: [componentDidMount](https://facebook.github.io/react/docs/component-specs.html#mounting-componentdidmount)

#### Updating: componentWillReceiveProps

`componentWillReceiveProps(object nextProps)`

> Invoked when a component is receiving new props. This method is not called for the initial render.
>
> Use this as an opportunity to react to a prop transition before `render()` is called by updating the state using `this.setState()`. The old props can be accessed via `this.props`. Calling `this.setState()` within this function will not trigger an additional render.
>
>  **NOTE:**
> There is no analogous method `componentWillReceiveState`. An incoming prop transition may cause a state change, but the opposite is not true. If you need to perform operations in response to a state change, use `componentWillUpdate`.

Read more: [componentWillReceiveProps](https://facebook.github.io/react/docs/component-specs.html#updating-componentwillreceiveprops)

#### Updating: shouldComponentUpdate

`boolean shouldComponentUpdate(object nextProps, object nextState)`

> Invoked before rendering when new props or state are being received. This method is not called for the initial render or when `forceUpdate` is used.
>
> Use this as an opportunity to `return false` when you're certain that the transition to the new props and state will not require a component update.
>
> If `shouldComponentUpdate` `returns` `false`, then `render()` will be completely skipped until the next state change. (In addition, `componentWillUpdate` and `componentDidUpdate` will not be called.)
> 
> By default, `shouldComponentUpdate` always `returns` `true` to prevent subtle bugs when state is mutated in place, but if you are careful to always treat state as immutable and to read only from props and state in `render()` then you can override `shouldComponentUpdate` with an implementation that compares the old props and state to their replacements.
>
> If performance is a bottleneck, especially with dozens or hundreds of components, use `shouldComponentUpdate` to speed up your app.

#### Updating: componentWillUpdate

`componentWillUpdate(object nextProps, object nextState)`

> Invoked immediately before rendering when new props or state are being received. This method is not called for the initial render.
>
> Use this as an opportunity to perform preparation before an update occurs.
>
> **Note:**
> You cannot use `this.setState()` in this method. If you need to update state in response to a prop change, use `componentWillReceiveProps` instead.


Read more: [componentWillUpdate](https://facebook.github.io/react/docs/component-specs.html#updating-componentwillupdate)

#### Updating: componentDidUpdate

`componentDidUpdate(object prevProps, object prevState)`

> Invoked immediately after the component's updates are flushed to the DOM. This method is not called for the initial render.
>
> Use this as an opportunity to operate on the DOM when the component has been updated.

Read more: [componentDidUpdate](https://facebook.github.io/react/docs/component-specs.html#updating-componentdidupdate)

#### Unmounting: componentWillUnmount

`componentWillUnmount()`

> Invoked immediately before a component is unmounted from the DOM.
>
> Perform any necessary cleanup in this method, such as invalidating timers or cleaning up any DOM elements that were created in componentDidMount.

Read more: [componentWillUnmount](https://facebook.github.io/react/docs/component-specs.html#unmounting-componentwillunmount)

---

### React Dynamic Children

`React` is great for rendering dynamic children. It's never been so easy.

Let's take the example:

```js
var AnimalsList = React.createClass({
  getInitialState: function() {
    return {
      animals: []
    };
  },

  render: function() {
    if (!this.state.animals.length) {
      return (
        <div>No animals!</div>
      );
    }
  
    return (
      <ul>
        {
          this.state.animals.map(function(animal, index) {
            return (
              <li key={index}>
                {animal.name} the { animal.animal }!
              </li>
            );
          })
        }
      </ul>
    );
  }
});

React.render(<AnimalsList />, document.body);
```

[JS Bin](http://jsbin.com/webamabaso/2/edit?html,js,output)

In this example, we will be fetching the data from a remote source. So the data will be stored inside `state`. You should just as easily create a `component` that uses `props`, and have a `Parent` `container` do the fetching and pass it down as `props`.

Anyway, upon the first `render`, we get back `No animals!`. Why? Well because our `this.state.animals` is `empty`!

In our `render` method, you can see we check if our `this.state.animals` passes a `.length` condition. If it fails, we render a `div` that says `No Animals!`.

If the condition passes, we render the `list`.

So lets add in the data fetching. For the purposes of this example, we mock the functionality with a `setTimeout` and a local `var`. But if you were actually going to do a `remote` request, you can use your favorite `AJAX` library, whether it's `jQuery`'s `ajax` or something like `superagent` or `fetch`.

```js
var animalsListData = [
  { id: 1, animal: 'tiger', name: 'Vee' },
  { id: 2, animal: 'lion', name: 'Simba' },
  { id: 3, animal: 'dog', name: 'Buck' },
  { id: 4, animal: 'sealion', name: 'Seel' }
];

var AnimalsList = React.createClass({
  getInitialState: function() {
    return {
      animals: []
    };
  },

  componentDidMount: function() {
    setTimeout(function() {
      this.setState({
        animals: animalsListData
      });
    }.bind(this), 2000);
  },

  render: function() {
    if (!this.state.animals.length) {
      return (
        <div>No animals!</div>
      );
    }
  
    return (
      <ul>
        {
          this.state.animals.map(function(animal, index) {
            return (
              <li key={index}>
                {animal.name} the { animal.animal }!
              </li>
            );
          })
        }
      </ul>
    );
  }
});

React.render(<AnimalsList />, document.body);
```

[JS Bin](http://jsbin.com/webamabaso/3/edit?html,js,output)

So what's going on here? As soon as the `component` `mounts`, we tell it to fetch the `remote` `data`. This is simulated with a `setTimeout`, but you could just as easily do it with `$.ajax(...)`. Heck, we could even move it into a another method, like `this._fetchRemoteData`, and then call it on `componentDidMount`, and then add in a button, that calls the method via `onClick`.

It could look something like this:

```js
var animalsListData = [
  { id: 1, animal: 'tiger', name: 'Vee' },
  { id: 2, animal: 'lion', name: 'Simba' },
  { id: 3, animal: 'dog', name: 'Buck' },
  { id: 4, animal: 'sealion', name: 'Seel' }
];


var AnimalsList = React.createClass({
  getInitialState: function() {
    return {
      animals: []
    };
  },

  componentDidMount: function() {
    this._fetchRemoteData();
  },

  render: function() {
    if (!this.state.animals.length) {
      return (
        <div>
          No animals!
          <br />
          <a
            href="#fetch"
            className="btn btn-primary"
            onClick={this.handleFetchClick}
          >
            Fetch
          </a>        
        </div>
      );
    }
  
    return (
      <div>
        <ul>
          {
            this.state.animals.map(function(animal, index) {
              return (
                <li key={index}>
                  {animal.name} the { animal.animal }!
                </li>
              );
            })
          }
        </ul>
        
        <a
          href="#fetch"
          className="btn btn-primary"
          onClick={this.handleFetchClick}
        >
          Fetch
        </a>

        <a
          href="#reset"
          className="btn btn-danger"
          onClick={this.handleResetClick}
        >
          Reset
        </a>
      </div>
    );
  },

  handleResetClick: function(e) {
    e.preventDefault();
    this.setState({
      animals: []
    });
  },

  handleFetchClick: function(e) {
    e.preventDefault();
    this._fetchRemoteData();
  },

  _fetchRemoteData: function() {
    setTimeout(function() {
      this.setState({
        animals: animalsListData
      });
    }.bind(this), 2000);
  }
});

React.render(<AnimalsList />, document.body);
```

[JS Bin](http://jsbin.com/hapubiceta/1/edit?html,js,output)

Alright this example a bit verbose, but hopefully it drives home how you can build your components. Do you see how intertwined your `view` and `view logic` end up being? Right from the `render` method, you can see exactly what it is going to output and what `events` are attached to what.

So let's summarize what is happening here:

1. The `state` is initialized, `this.state.animals` set to an `empty` `array`.
2. The component will mount, we do nothing here.
3. When `render` is called, we check if there is anything inside `this.state.animals`, if there is nothing, we render a `div` that says `No animals!`. This could probably be a loading indicator if you are fetching data as soon as the `componentDidMount`.
4. The component did mount, we call `this._fetchRemoteData()`
5. When `this._fetchRemoteData()` is triggered, `this.setState(..)` is called and a `render` happens! The `update` `lifecycle events` are also triggered. 

There are also `buttons` that trigger a `reset` or `fetch`, just look at the `handler` `methods`, to see how they `update` the `state`. Changing `state`, tells `React` to `rerender`.

So, to sum it all up, to render `children`, simply `map` over your `collection` and `return` the `components` you want rendered by passing in the `collections` `item` `attributes` as `props`.

Read more: [React vs. Ember by Alex Matchneer](https://docs.google.com/presentation/d/1afMLTCpRxhJpurQ97VBHCZkLbR1TEsRnd3yyxuSQ5YY/edit#slide=id.p)

---

### React Nested Views

`React` is great for working with a tree structure like `HTML`. You can nest to your hearts content, it's encouraged. Remember everything is a `component`. It's just like working in `HTML`, so it should start to come naturally to you.

Consider this, we have a `component` known as `App`:

```js
React.render(<App />, document.getElementById('#content'));
```

We render it to `#content`.

Inside the `App` component its `render` could have an assortment of `components`. Maybe it looks like this:

```js
// App.jsx
...
render: function() {
	return (
		<div>
			<SubNavBar />

			<MainContent>
		</div>
	);
}
...

// SubNavBar.jsx
...
render: function() {
	return (
		<Nav>
			<SearchBar />
			<NavMenuDropdown>
				<NavItemLink name='Edit Profile' to='/edit' />
				<NavItemLink name='Logout' to='/logout' />
			<NavMenuDropdown>
		</Nav>
	);
}
...

// MainContent.jsx
...
render: function() {
	return (
		<Grid fluid>
			<Col md={3}>
				<Sidebar />
			</Col>

			<Col md={9}>
				<Dashboard />
			</Col>
		</Grid>
	);
}
...

```

Each `component`, could keep going. Eventually you'd reach a point it actually returns the `HTML`, for example, `Grid` might actually just be an `abstraction` for:

```js
// Grid.jsx
render: function() {
	return (
		<div className={this._classNames()}>
			{this.props.children}
		</div>
	);
}
```

---

### React Mixins

`Mixins` are a way of sharing resuable functionality between components.

Read more: [Mixins](https://facebook.github.io/react/docs/reusable-components.html#mixins)

---

### React Pure Render

A simple performance boost you can get out of `React` is through the `PureRenderMixin`.

Per the `React` documentation:

> If your React component's render function is "pure" (in other words, it renders the same result given the same props and state), you can use this mixin for a performance boost in some cases.
>
> Under the hood, the mixin implements shouldComponentUpdate, in which it compares the current props and state with the next ones and returns false if the equalities pass.
>
> **Note:**
> This only shallowly compares the objects. If these contain complex data structures, it may produce false-negatives for deeper differences. Only mix into components which have simple props and state, or use forceUpdate() when you know deep data structures have changed. Or, consider using immutable objects to facilitate fast comparisons of nested data.
> Furthermore, shouldComponentUpdate skips updates for the whole component subtree. Make sure all the children components are also "pure".



Read more: [PureRenderMixin](https://facebook.github.io/react/docs/pure-render-mixin.html)

---

### React and 3rd Party Libraries

---

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
