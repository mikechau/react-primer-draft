# react-primer-draft

A primer for building *Single Page Applications* with [React](http://facebook.github.io/react/).

## Status

This is a work in progress.

At the time of writing, the examples were written for `React 0.12.x`. This guide will be updated with examples for `React 0.13` `ES6 classes` soon!

## Table of Contents
- [Author's Note](#authors-note)
- [Part 1: Intro to React](#intro-to-react)
  - [0.1: What People are saying about React](#what-people-are-saying-about-react)
  - [0.2: React Community](#react-community)
  - [0.5: React Documentation](#react-documentation)
  - [1.0: React Component](#react-component)
  - [1.1: React JSX](#react-jsx)
  - [1.2: React Supported Attributes](#react-supported-attributes)
  - [1.3: React Supported Events](#react-supported-events)
  - [1.4: React Supported Events Continued](#react-supported-events-continued)
  - [1.5: React Props](#react-props)
      - [1.5.1: getDefaultProps](#getdefaultprops)
      - [1.5.2: propTypes](#proptypes)
      - [1.5.3: refs](#refs)
      - [1.5.4: children](#children)
      - [1.5.5: className](#className)
      - [1.5.6: Passing Props](#passing-props)
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
      - [1.8.1: key](#key)
  - [1.9: React Nested Views](#react-nested-views)
  - [1.10: React Mixins](#react-mixins)
  - [1.11: React Pure Render](#react-pure-render)
  - [1.12: React and 3rd Party Libraries](#react-and-3rd-party-libraries)
  - [1.13: React Developer Tools](#react-developer-tools)
- [Part 2: Harmony aka ES6 aka ES2015](#es2015)
  - [2.1: const and let](#const-and-let)
  - [2.2: Fat Arrow](#fat-arrow)
  - [2.3: Spread Operator](#spread-operator)
  - [2.4: Classes](#classes)
  - [2.5: Babel](#babel)
- [Part 3: Useful Libraries](#useful-libraries)
    - [3.1: Superagent](#superagent)
    - [3.2: Bluebird](#bluebird)
    - [3.3: lodash](#lodash)
    - [3.4: normalizr](#normalizr)
- [Part 4: Webpack](#webpack)
    - [4.1: Hot Module Replacement and Hot Reloading](#hot-module-replacement-and-hot-reloading)
    - [4.2: AST Transformations](#ast-transformations)
- [Part 5: React Router](#react-router)
- [Part 6: Flux](#flux)
    - [6.1: Alt](#alt)
      - [6.1.1: Alt Actions](#alt-actions)
      - [6.1.2: Alt Stores](#alt-stores)
- [Part 7: Testing](#testing)
    - [7.1: Mocha](#mocha)
- [Part 8: Rails (Bonus Chapter)](#rails)
    - [8.1: React Rails](#react-rails)
    - [8.2: Writing an API](#writing-an-api)
    - [8.3: Session Handling in React](#session-handling-in-react)
    - [8.4: Rails and React Build Process](#rails-and-react-build-process)

---

## Authors Note

This primer makes use of several libraries, but it is by no means a "_React the right way_". It's just a introduction to how I am building my own React applications. The goal of this primer to help developers get familiar with React and dive right in. Maybe you will come up with approaches that work with better for you and I hope that you share them with the community! Or if you're already well versed, help improve this document so others in the community can benefit. Sharing is caring!

This guide is dedicated to the engineers at [Jellyvision](http://jellyvision.com), we are [hiring](http://www.jellyvision.com/jobs/) so check us out. :D

~ Michael Chau (gh: [@mikechau](https://github.com/mikechau), twtr: [@money_mikec](https://twitter.com/money_mikec))

## Intro to React

React is a JavaScript library by Facebook, it describes itself as *__a javascript library for building user interfaces__*.

Developers often call it *the V in MVC*, or talk about the *virtual DOM* (not to be confused with the *shadow DOM*). I like React for its declarative style, lifecycle event hooks, and the fact that a React *component* describes its view at anytime. By breaking down the view into components, writing React starts to become very natural. React  has been a pleasure to work with. You no longer need to understand the entire flow of the application at once, you can start at a component and work your way up or down.

This primer is meant to get you rapidly ready to start working with a React application. Its goal is not to teach and explain everything, but merely introduce concepts and help you form the right questions to ask and to have an idea of where to look for an answer. It is OK if you do not understand everything at first, just keep working at it by commiting the code you see to muscle memory and reading up on the documentation. Hopefully through reflection, and incubation, the concepts here will start to make sense.

Don't be afraid of React either.  It may *seem* complex but is quite simple with a very small API of a dozen "essential" methods:

1. [render](http://facebook.github.io/react/docs/component-specs.html#render)
2. [getInitialState](http://facebook.github.io/react/docs/component-specs.html#getinitialstate)
3. [getDefaultProps](http://facebook.github.io/react/docs/component-specs.html#getdefaultprops)
4. [propTypes](http://facebook.github.io/react/docs/component-specs.html#proptypes)
5. [mixins](http://facebook.github.io/react/docs/component-specs.html#mixins)
6. [componentWillMount](http://facebook.github.io/react/docs/component-specs.html#mounting-componentwillmount)
7. [componentDidMount](http://facebook.github.io/react/docs/component-specs.html#mounting-componentdidmount)
8. [componentWillReceiveProps](http://facebook.github.io/react/docs/component-specs.html#updating-componentwillreceiveprops)
9. [shouldComponentUpdate](http://facebook.github.io/react/docs/component-specs.html#updating-shouldcomponentupdate)
10. [componentWillUpdate](http://facebook.github.io/react/docs/component-specs.html#updating-componentwillupdate)
11. [componentDidUpdate](http://facebook.github.io/react/docs/component-specs.html#updating-componentdidupdate)
12. [componentWillUnmount](http://facebook.github.io/react/docs/component-specs.html#unmounting-componentwillunmount)

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

### React Community

The React community is super friendly!

Connect with other React developers at:

- [Reactiflux](https://reactiflux.slack.com/) - Slack for React developers
- [#reactjs on irc.freenode.net](irc://chat.freenode.net/reactjs)
- [Google Groups](http://groups.google.com/group/reactjs)
- [Stack Overflow](http://stackoverflow.com/questions/tagged/reactjs)
- [@reactjs](https://twitter.com/reactjs)
- [#reactjs](https://twitter.com/search?q=%23reactjs)

---

### React Documentation

The React documentation is very good. Use this primer as a introduction and then read more about React by viewing the official documentation:

[React Documentation](https://facebook.github.io/react/docs/getting-started.html)

There's also a ton of resources at: [Awesome React](https://github.com/enaqx/awesome-react)

### React Component

A React component encapsulates everything. It does not separate the *view* from the *view logic*, but rather merges the two together. Separating these does not really make sense when building a user interface: the view and its logic are inevitably tightly coupled. Rather than jumping between a template file and some sort of view-controller it makes sense to keep them together. React *components* are usually small enough that this is not a big deal to have the two together, and if it does get to be too large you can break down your component into smaller components.  

A key point from [the React documentation](http://facebook.github.io/react/docs/):

> #### [Components are Just State Machines](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#components-are-just-state-machines)
> React thinks of UIs as simple state machines. By thinking of a UI as being in various states and rendering those states, it's easy to keep your UI consistent.
>
> In React, you simply update a component's state, and then render a new UI based on this new state. React takes care of updating the DOM for you in the most efficient way.

Read more: [Interactivity and Dynamic UIs](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

---

### React JSX

**JSX** is pretty interesting. It basically, allows using an HTML/XML-like syntax within JavaScript-based React components. Of course this wouldn't work if you tried to do that then serve it. Choosing to write your React component in JSX requires a *transform* process. This is typically handled through a build process or tool, like [webpack](http://webpack.github.io).

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

Here you can see a React component has a `render` method, which returns *markup*. It's easy to see the shape of the output at a glance.

[JS Bin](http://jsbin.com/tapupafeqe/1/edit?html,js,output)

**NOTE:** [As of version 0.13](https://github.com/facebook/react/issues/2127) React components can only ever return a single "root" element or sub-component.

For example, this is forbidden:

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

To render a React component in the body all you need to do is:

```js
React.render(<Button />, document.body);
```

Simply call the render method, pass in the component, and the DOM node you want to render to.

**NOTE:** These examples use `document.body`, but you should avoid using it as it can cause subtle bugs.

When rendering a React component inside a DOM node, React wants complete ownership of the node. You should not add children to or remove children from a node in which React inserted a component.

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

React works with most common HTML elements, for example:

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

You just made an `a` tag! It can now be called via `<Link />`.

[JS Bin](http://jsbin.com/vahezonoyi/1/edit?html,js,output)

Read more: [React Tags and Attributes](http://facebook.github.io/react/docs/tags-and-attributes.html)

---

### React Supported Events

React has a cross-compatibility layer for most specific browser events. Going back to our `Link`:

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

Now, I know what you're thinking. *Inline events, isn't that bad?* It looks like its inline but its really not. React will use *event delegation* behind the scenes. So now we have a very declarative way to associate events to DOM elements. Now there's no confusion as to what elements have what events and there is no hassle of managing binding hooks between DOM and javascript (e.g. ids or classes).

Here's a key point from the React documentation:

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

In the example, we defined a function, and simply passed the function to the `onClick` property.

When the *click event* occurs, we receive back a *synthetic event* we can manipulate as usual e.g. call `#preventDefault()` to stop the event's default action, or access the event's `#target`.

Read more: [React Events](http://facebook.github.io/react/docs/events.html)

---

#### React Supported Events Continued

To use the same event handler in multiple bindings and contexts, you may want to attach custom data to DOM nodes as you'd do in native javascript:

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

That is unnecessary in React, you can use `Function#bind` and customise the handler itself via partial application:

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

According to [Javascript Is Sexy](http://javascriptissexy.com):

> Partial function application is the use of a function (that accept one or more arguments) that returns a new function with some of the arguments already set. The function that is returned has access to the stored arguments and variables of the outer function. This sounds way more complex than it actually is, so let’s code.
> ...

An explanation of `.bind(this, ...)` vs `.bind(null, ...)` by `Morhaus` on `#reactjs`:

> React autobinds methods in the object you pass to `React.createClass()` to the component instance, so using `this.handleClick.bind(null, 'test')` will ensure that behavior is not messed with
>
> ...
>
>  pass null instead, unless you're not using `React.createClass()` but `class extends React.Component`, in which case methods are not auto bound

`this` can be passed to preserve the current context, or we can pass `null` if it is not necessary. In this case, since we are using `React.createClass`, React will *autobind* the method for us so we can just pass `null` and whatever arguments we want applied.

Read more: [Currying](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals/)

Read more: [Understand Javascript's "this" with Clarity and Master It](http://javascriptissexy.com/understand-javascripts-this-with-clarity-and-master-it/)

Read more: [React Autobinding](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#under-the-hood-autobinding-and-event-delegation)

Read more: [bind(): React component methods may only be bound to the component instance](https://groups.google.com/forum/#!topic/reactjs/Xv9_kVoJJOw)

Read more: [Partial application in JavasScript with `bind`](https://coderwall.com/p/nw9cxg/partial-application-in-javascript-with-bind)

---

### React Props

*Props* are immutable parameters passed by a parent component to a child sub-component. A component can not alter its `#props` object (and should not alter the props themselves), the only way for props to change is for a new render to be triggered, where the parent component passes new props to the child.

Props flow downwards, and in JSX they are provided as *attributes* of the component node:

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

Here we have the *Parent Component*, `LikeList`, render an unordered list, with one child, a `LikeListItem`. To the `LikeListItem` we pass a `text` property.

A component can access its props through `this.props`, `text` would be accessed via `this.props.text`. Here, the `text` prop is simply accessed during rendering.

[JS Bin](http://jsbin.com/rerazageku/1/edit?html,js,output)

Read more: [Transferring Props](https://facebook.github.io/react/docs/transferring-props.html)

#### getDefaultProps

`getDefaultProps` will be called to get a default set of props, which will be overridden by the props eventually provided by a parent component. This is useful for optional props which have a sensible default value.

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

If no `text` prop is passed, we give it a default value of `N/A`. If defined, `getDefaultProps` must return an object.

[JS Bin](http://jsbin.com/volisofase/2/edit?html,js,output)

Read more: [Default Prop Values](https://facebook.github.io/react/docs/reusable-components.html#default-prop-values)

#### propTypes

`propTypes` documents the props expected by a component and define validators generating notices in the dev console.

A key point from the React `documentation`:

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

Here we declare that the `text` property, must be a `string`. By default, props are optional and should have a default value (provided through `getDefaultProps`).

It is also possible to mandate that a prop be provided with the `isRequired` validator:

```js
// Child Component
var LikeListItem = React.createClass({
	propTypes: {
		text: React.PropTypes.string.isRequired
	},
...
```

`getDefaultProps` was removed: since the property is required, there is no reason to provide a default value for it.

Read more: [Prop Validation](https://facebook.github.io/react/docs/reusable-components.html#prop-validation)

#### refs

React documentation introduction:

> React supports a very special property that you can attach to any component that is output from render(). This special property allows you to refer to the corresponding backing instance of anything returned from render(). It is always guaranteed to be the proper instance, at any point in time.

Here is an example of how you can treat a `ref` like an `id`:

```js
// Parent Component
var LikeList = React.createClass({
    componentDidMount: function() {
      console.log(this.refs.first.getDOMNode()));
    },

	render: function() {
		return (
			<ul>
				<LikeListItem ref="first" text='turtles.' />
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

[JS Bin](http://jsbin.com/labicocahi/1/edit?js,output)

**NOTE:** In React 0.13, `Component#getDOMNode()` should be replaced by `React.findDOMNode(Component)`, the first one generates a warning in the console.

In this example, we can access the `ref` of `first` via `this.refs.first`. After `componentDidMount` has been called, the console output will be:

```html
<li data-reactid=".0.0">turtles.</li>
```

Read more: [More About Refs](http://facebook.github.io/react/docs/more-about-refs.html)

#### children

There may be situations where you want components to wrap provided components rather than generate those from props:

```js
var Likes = React.createClass({
  render: function() {
    return (
      <div>
        <LikesListWrapper>
          <LikeListItem text="turtles" />
        </LikesListWrapper>
      </div>
    );
  }
});



// Parent Component
var LikesListWrapper = React.createClass({
	render: function() {
		return (
			<ul>
              {this.props.children}
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

React.render(<Likes />, document.body);
```

Children are placed between a component's opening and ending tags, like regular HTML elements and, and the wrapper component can access those children via `this.props.children`.

[JS Bin](http://jsbin.com/labicocahi/2/edit?js,output)

Read more: [Type of the Children props](http://facebook.github.io/react/tips/children-props-type.html)

#### className

Because `class` is a reserved JavaScript keyword, to set the `class` of an element you will need to use the `className` property name instead.

Review: [Tags and Attributes](https://facebook.github.io/react/docs/tags-and-attributes.html) for more details on the supported `HTML` tags and `attributes`.

Review: [Events](https://facebook.github.io/react/docs/events.html) for the supported browser events.

#### Passing a Prop

When providing a boolean prop in JSX, passing the value is not necessary, as in HTML you can just add the key:

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
`AnotherComponent`'s `this.props.checked` would resolve to `true`.

---

### React State

As *Pete Hunt* noted, *shared mutable state is the root of evil*. Yet (mutable) state is often necessary. To that end, React components provide mutable state but *not shared* mutable state: only a component can alter its state, and a component can only alter its own state.

On a component's state change, a re-render of the tree will be automatically triggered.

State is useful for intermediate or self-contained component data, which should not or needs not be published externally. For instance a choice between liking something or not:

```html
<!--  index.html -->
<body>
  <p>Do you like fish sticks?</p>
  <p>Response: I <span id="response">______</span> fishsticks.</p>
  <a id="like" class="btn btn-success">I like them.</a>
  <a id="dislike" class="btn btn-danger">I dislike them.</a>  
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

The state of having liked or disliked fish sticks is fully internal, it does not come from an external source (a parent component) and is not published anywhere, thus in React:

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
				<p>Do you like fish sticks?</p>
				<p>Response: I {this.state.response || '_____'} fishsticks.</p>
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

`getInitialState` has the same purpose as `getDefaultProps`, but because state is not shared rather than providing a default it provides the complete internal state of the component. State items can then be accessed through `this.state`, much like props via `this.props`.

State **must not be altered directly**.

It should generally be altered via [`setState`](https://facebook.github.io/react/docs/component-api.html#setstate), which *merges* the provided object into the existing state then triggers a re-render: if the state is `{foo: 1, bar: 2}` `this.setState({foo: 2})` will result in a new state of `{foo: 2, bar: 2}`.

**NOTE:** although sometimes tempting, setting up the initial state from props is generally an anti-pattern, it's usually better to compute from props on the fly.

For example:

```js
getInitialState: function() {
   return {
     count: this.props.initialCount // this is fine because we make it clear that it is an initial value
   }
}
```

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

React components have a somewhat involved lifecycle, but React provides a number of events/methods to hook in and act at various lifecycle points. The React documentation covers this section very well, so we will just quote it and show you some examples of how they work.

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

React is great for rendering dynamic children. It's never been so easy.

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

In this example, we will be fetching data from a remote source. That data will be stored as component state. It could also be stored externally and passed down as props.

Because `this.state.animals` is initially empty, the first render will display *No animals!*, as coded in the first part of the `render` method, we only render the list if there are animals in the list.

For the purpose of this example, we'll emulate data fetching with a `setTimeout` call. In a real-world situation, you would use whatever AJAX library you prefer.

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

As soon as the component mounts, we "fetch" the remote data, which will update the internal state and re-render the component 2 seconds later. The fetching is done inline but could be split into a separate method (e.g. `_fetchRemoteData`), and while we're fetching everything on mount, it could also be fetched only on a user action:

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

Alright this example a bit verbose, but hopefully it drives home how you can build your components. Do you see how intertwined your view and view logic end up being? Right from the `render` method, you can see exactly what it is going to output and what events are attached to what.

So let's summarize what is happening here:

1. The `state` is initialized, `this.state.animals` set to an empty array.
2. The component will mount, we do nothing here.
3. When `render` is called, we check if there is anything inside `this.state.animals`, if there is nothing, we render special case noting the lack of animals.
4. The component did mount, we call `this._fetchRemoteData()`
5. When `this._fetchRemoteData()` completes, `this.setState(..)` is called and a new `render` happens! The update lifecycle events are also triggered. 
6. The user can use the available buttons to reset or update the list of animals.

So, to sum it all up, to render children, simply `map` over your collection and return the components you want rendered by passing in the collections item attributes as props.

**NOTE:** when mapping over an array, the result components must be given a `key`.

Read more: [React vs. Ember by Alex Matchneer](https://docs.google.com/presentation/d/1afMLTCpRxhJpurQ97VBHCZkLbR1TEsRnd3yyxuSQ5YY/edit#slide=id.p)

---

### React Nested Views

React is great for working with a tree structure like HTML. You can nest to your hearts content, it's encouraged. Remember everything is a component. It's just like working in HTML, so it should start to come naturally to you.

Consider this `App` component:

```js
React.render(<App />, document.getElementById('content'));
```

We render it to `#content`.

Inside the `App` component its `render` could have an assortment of components. Maybe it looks like this:

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

Each component, could keep going. Eventually you'd reach a point it actually returns the HTML, for example, `Grid` might actually just be an abstraction for:

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

Mixins are a way of sharing reusable functionality between components.

Key point from React documentation:

> Components are the best way to reuse code in React, but sometimes very different components may share some common functionality. These are sometimes called [cross-cutting concerns](http://en.wikipedia.org/wiki/Cross-cutting_concern). React provides mixins to solve this problem.

**NOTE:** The validity of mixins, is currently debated in the community. While you may continue to use them with `React.createClass`, mixins are not currently available when using ES6 classes.  The community seems to be leaning toward the idea of containers aka *high order components* or *decorators* (functions or components which manipulate or alter other components).

Mixin example:

```js
var Mixin1 = {
  componentDidMount: function() {
    console.log('Mixin1, component did mount!');
  }
};

var Mixin2 = {
  componentDidMount: function() {
    console.log('Mixin2, component did mount!');
  }
};


var Greeter = React.createClass({
  mixins: [Mixin1, Mixin2],

  componentDidMount: function() {
    console.log('Greeter, component did mount!');
  },

  render: function() {
    return (
      <div>Hi!</div>
    );
  }
});

React.render(<Greeter />, document.body);
```
[JS Bin](http://jsbin.com/hapubiceta/2/)

After `componentDidMount`, the console should display:

```
"Mixin1, component did mount!"
"Mixin2, component did mount!"
"Greeter, component did mount!"
```

Mixins are a way of sharing functionality in lifecycle events between components. They can also be used to add custom methods to your React components.

Read more: [Mixins](https://facebook.github.io/react/docs/reusable-components.html#mixins)

---

### React Pure Render

A simple performance boost you can get out of React is through the `PureRenderMixin`.

Per the React documentation:

> If your React component's render function is "pure" (in other words, it renders the same result given the same props and state), you can use this mixin for a performance boost in some cases.
>
> Under the hood, the mixin implements `shouldComponentUpdate`, in which it compares the current props and state with the next ones and returns false if the equalities pass.
>
> **Note:**
> This only shallowly compares the objects. If these contain complex data structures, it may produce false-negatives for deeper differences. Only mix into components which have simple props and state, or use forceUpdate() when you know deep data structures have changed. Or, consider using immutable objects to facilitate fast comparisons of nested data.
> Furthermore, shouldComponentUpdate skips updates for the whole component subtree. Make sure all the children components are also "pure".

Let's check out an example:

```js

var Greeter = React.createClass({
  mixins: [React.addons.PureRenderMixin],

  getInitialState: function() {
    return {
      greeting: 'Hi'
    };
  },

  componentDidUpdate: function() {
    console.log('Component updated!');
  },

  render: function() {
    console.log('Component rendered!');
    return (
      <div>
        Greeting: {this.state.greeting}
        <br />
        <hr />
        <a
          href="#"
          onClick={this.handleGreetingClick.bind(null, 'Hi')}
        >
          Say Hi
        </a>

        <br />

        <a
          href="#"
          onClick={this.handleGreetingClick.bind(null, 'Hey')}
        >
          Say Hey
        </a>
      </div>
    );
  },
  
  handleGreetingClick: function(greeting, e) {
    e.preventDefault();
    
    console.log('click event', greeting);
    
    this.setState({
      greeting: greeting
    });
  }
});

React.render(<Greeter />, document.body);
```

[JS Bin](http://jsbin.com/hapubiceta/3/edit?html,js,console,output)

The initial state of `this.state.greeter` is set to `Hi`.

If we clicked the *Say Hi* action, the console would display:

```
"click event"
"Hi"
```

**No updates were applied** because the previous state is `{greeting: 'Hi'}`, and the new state is the exact same `{greeting: 'Hi'}`. If the props and state haven't visibly changed since the last `render`, `PureRenderMixin` will just **skip** the new one.

If we clicked *Say Hey*, the console would say the following instead:

```
"click event"
"Hey"
"Component rendered!"
"Component updated!"
```

Read more: [PureRenderMixin](https://facebook.github.io/react/docs/pure-render-mixin.html)

---

### React and 3rd Party Libraries

The neat thing about React is you don't have to commit your whole application to using it. You can sprinkle it in and eventually... you'll want to write to everything in React. ;)

You can use third party libraries with React, even if they were not specifically written for React. Considering something like [jQuery UI](https://jqueryui.com), some sort of charting library or even something like [DataTables](https://www.datatables.net). We will use *DataTables* as an example, of how you could use it with React. 

```js
var accountingData = function() {
  var data = [];
  
  var random = (Math.floor(Math.random() * 10));
  
  for (i = 0; i < random; i++) { 
    data.push({
      name: 'Transaction ' + (i + 1),
      amount: (Math.floor(Math.random() * 100))
    });
  }
  
  return data;
};


var AccountingTable = React.createClass({
  getInitialState: function() {
    return {
      transactions: []
    };
  },

  componentDidMount: function() {
    $(this.refs.table.getDOMNode()).DataTable();
  },

  componentWillUpdate: function() {
    var table = $(this.refs.table.getDOMNode()).DataTable();
    table.destroy();
  },
  
  componentDidUpdate: function() {
    $(this.refs.table.getDOMNode()).DataTable();
  },

  componentWillUnmount: function() {
    var table = $(this.refs.table.getDOMNode()).DataTable();
    table.destroy();
  },

  render: function() {
    return (
      <div>
        <table ref="table" className="table">
          <thead>
            <th>Transaction Name</th>
            <th>Amount</th>
          </thead>
          <tbody>
            {
              this.state.transactions.map(function(trans, index) {
                return (
                  <tr key={index}>
                    <td>{trans.name}</td>
                    <td>{trans.amount}</td>
                  </tr>
                );
              })
            }        
          </tbody>
        </table>
        
        <a href="#" className="btn btn-default" onClick={this.handleGetTransactionsClick}>Get Transactions</a>
      </div>
    );
  },
  
  handleGetTransactionsClick: function(e) {
    e.preventDefault();

    this.setState({
      transactions: accountingData()
    });
  }
});

React.render(<AccountingTable />, document.body);
```

[JS Bin](http://jsbin.com/hapubiceta/4/edit?js,output)

This example is incredibly arbitrary. You would probably update the table via ajax instead, or write your own table component, or use something off the shelf for React like [FixedDataTable](https://facebook.github.io/fixed-data-table/) from Facebook or [Griddle](http://dynamictyped.github.io/Griddle/), etc.

In this example, our initial state, `this.state.transactions`, is an empty array.

After `componentDidMount`, we initialize and render `DataTable`.

Then on *Get Transactions*, we update the `state` with the data.

Before the component updates, we destroy `DataTable`, and reinitialize it on `componentDidUpdate`. When the component unmounts we will also destroy the `DataTable` to clean up any associated event handler or resource.

If there are more interactions with the table, instead of asking React for the DOM node every time, we could store a reference in something like `this._dataTableRef`.

You could also have a React component which doesn't render anything to the DOM (aside from a required component root) but uses its lifecycle events to trigger commands on a third party library to manipulate the DOM. This concept is what *Ryan Florence* calls a **portal**.

Read more: [Reaf.js Conf 2015 - Hype! (Portals)](https://youtu.be/z5e7kWSHWTg?t=15m22s) - Video.

Read more: [Portals Example Repo](https://github.com/ryanflorence/reactconf-2015-HYPE/tree/master/demos/03-portals)

Read more: ["Portals" in React.js](http://joecritchley.svbtle.com/portals-in-reactjs)

---

### React Developer Tools

React has a handy developer debug tool, for *Chrome*, check it out: [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en).

---

## ES2015

### const and let

### Fat Arrow

### Classes

### Babel

---

## Useful Libraries

### Superagent

### Bluebird

### lodash

---

## Webpack

### Hot Module Replacement and Hot Reloading

---

## React Router

---

## Flux

### Alt

#### Alt Actions

#### Alt Stores

---

## Testing

### Mocha

---

## LICENSE

Copyright (c)  2015  Michael Chau.

Permission is granted to copy, distribute and/or modify this document  
under the terms of the GNU Free Documentation License, Version 1.3  
or any later version published by the Free Software Foundation;  
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.  
A copy of the license is included in the section entitled "GNU  
Free Documentation License".  
