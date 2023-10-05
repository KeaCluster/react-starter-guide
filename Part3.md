# Part 3 - State

# Table of Contents
1. [State and lifecycle](#state-and-lifecycle)
    - [State](#state)
    - [Lifecycle](#lifecycle)
2. [Hooks](#hooks)
    - [Why?](#why?)
    - [useState](#usestate)
    - [useEffect](#useeffect)

## State and lifecycle

To be honest, understanding state alongside a component's lifecycle is one of the most important aspects of React. Knowing how to use `props` is great and all, but what if the component needs to update? Remember that a Component should never modify its own `props`.

So let's sail onwards and check out these concepts.

### State

In React, a component is processed as an object that holds data. However this data may change over time depending on user interaction or third-party libraries, APIs, Database info, etc...
So, in a way, this data we're talking about may or may not come from inside our app. Which is why there is something called `State`. When the state of a component changes, React **re-renders** that component and all its descendants. And with that *re-render*, VDOM comes into play.

We'll take a closer look at how `State` is managed and implemented. But to sum things up a bit: `State` is how the data of our component is handled whenever it changes. And the concept of change between the **current** and the **new state** is called `Lifecycle`

### Lifecycle

React Components essentially work in phases. These phases represent all states of the component from creation to deletion:
    - Mounting the component (Created and inserted into the DOM)
    - Updating (Re-rendering as a result of changes from its props or state)
    - Unmounting (Removing the component from the DOM)

As of version [18.2.0 of React](https://react.dev/reference/react/Component), lifecycle methods for components such as `componentDidMount`,  `componentDidUpdate`, and `componentWillUnmount` are still valid in class components. But these methods aren't used as often anymore with the modern trend of **functional programming** in React. Which is why `Hooks` such as `useState` and `useEffect` were added for `functional components`. Lifecycle methods are now considered *legacy* and the official React docs recommend migrating to Hooks.

## Hooks

`Hooks` were introduced in version *16.8* of React. And they were picked up pretty quickly. `class React components` were the norm when writing or implementing a component that needed to update or re-render itself because of how React was originally written and coded. So in order to implement dynamic components, there was a lot of documentation (still is but its more objective) and code involved. The React team alongside the community realized that it wasn't the most optimal way to do things. And to solve this, `Hooks` came into play.

To make things simple, they enable the use of stateful logic without changing our components' hierarchy, making it easy to extract and share hooks among other components or even applications.

### Why?

1. Reusability
    By allowing us to reuse stateful logic without refactoring the components' hierarchy, we can extract and share hooks between components.
2. Composition
    `Hooks` provide a concise and simple way to access the React way of lifecycle inside our components. By simplifying lifecycle methods (seen before) to just a few lines of code that are the same between all components. Adhering to this method, code in our app will be as readable as code from another app that implements them.
3. No classes
    The tide has shifted away from classes now. And just like the [React Docs](https://react.dev/reference/react/Component) mention, functional programming is a simpler and more objective way to use state.
4. Better defaults
    Sometimes there is the case where the state of a component isn't necessarily well defined.
    - Lets say you have a cart component in your app and its state will be the products listed there. How can you set the default array of products inside your cart to be completely empty and prevent errors such as `Undefined` or `Null`?. Well, we can set default state with hooks and control any side effect.
5. Side effects
    - If the state of your component is dependent of a request to a third party or even external API, then you dont really have any control over that request or its response. What if it fails? What if you want flexibility over how many times this request will be required depending on the components' lifecycle? A famous hook does just that.

### useState

### useEffect
