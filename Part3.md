# Part 3 - State

# Table of Contents
1. [State and lifecycle](#state-and-lifecycle)
    - [State](#state)
    - [Lifecycle](#lifecycle)
2. [Hooks](#hooks)
    - [Why?](#why?)
    - [useState](#usestate)
    - [useEffect](#useeffect)
3. [Extras](#extras)
    - [Advanced hooks and practice](#advanced-hooks-and-practice)

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


1. What?

[`useState`](https://react.dev/reference/react/useState) is a fundamental hook provided by React to manage local state inside our functional components. This allows us to have control of the state in a more straightforward and readable manner.

The syntax is quite simple.

```jsx
const [state, setState] = useState(initialState);
```

This should be declared at the top of our component, so just after initialization.

Use state has three main parts
- `state` is the current state value of the component
- `setState` is a function that allows us to update the state
- `initialState` is the initial value (set by us) of the state. 

As you might've noticed, this declaration uses [array destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment), which is something already available in vanilla js. You can read more about it on the docs.

2. How?

Well, if you initialized your application with `vite.js` just like we did on part 1, you might already see it implemented in `App.jsx`.

```jsx
import { useState } from 'react';

function App() {
    const [count, setCount] = useState(0)
    // declare state, declare our function to set it, and then inside useState() declare the initial value

    return(
        <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
        </div>
    )
}

// some more code here
```

Notice that we need to import `useState` from the React library and that the declaration inside the component gives **context** about what that state is used for. In this case, for a counter that will be updated by +1 each time the button is pressed

```jsx
onClick={() => setCount(count + 1)}
```

This is the event listener declared on our `<button>`. Inside it, a `callback` function which calls our `setCount()` declared at the top of the component. Inside it, we simply add `+1` to our current state.

We can also set state with something called a `handler` function. Which are small custom functions that aid in the *handling* of our state:

```jsx
import { useState } from 'react';

function App() {
    const [count, setCount] = useState(0)
    // declare state, declare our function to set it, and then inside useState() declare the initial value

    const countHandler = () => setCount(count + 1);

    return(
        <div>
            <p>You clicked {count} times</p>
            <button onClick={countHandler()}>
                Click me
            </button>
        </div>
    )
}

// some more code here
```

If you compare to the previous code, it's easier to read, a bit more manageable when refactoring, but it does the exact same thing.

**Handlers** are more commonly used when the state of a component becomes a lot more complex. Such as in cases where we can make an `API` call through `FETCH` or a library like `Axios`. But don't worry, we'll sail to that island when the time comes.

Here's another implementation of state:

```jsx
import React, { useState } from 'react';

function ItemList() {
    const [items, setItems] = useState([{ id: 1, text: 'Item 1' }]); // We have only one item here, but we could in theory have 10, 100 or 1000+
    const [text, setText] = useState(''); // State for the text input


    // Handlers
    // As you can see, they can have more than one instruction
    // They ARE functions after all.
    const handleAdd = () => {
        setItems([...items, { id: Math.random(), text }]);
        setText('');
    };

    const handleDelete = (id) => {
        setItems(items.filter(item => item.id !== id));
    };

    const handleEdit = (id, newText) => {
        setItems(items.map(item => (item.id === id ? { ...item, text: newText } : item)));
    };

    return (
        <div>
            <input type="text" value={text} onChange={(e) => setText(e.target.value)} />
            <button onClick={handleAdd}>Add Item</button>
            <ul>
                {items.map(item => (
                    <li key={item.id}>
                        {item.text}
                        <button onClick={() => handleDelete(item.id)}>Delete</button>
                        <button onClick={() => handleEdit(item.id, prompt('New text:', item.text))}>Edit</button>
                    </li>
                ))}
            </ul>
        </div>
    );
}

export default ItemList;
```

Try this component out inside your project. Figure out what it does.


> Somehow this section won't render properly on Github pages. You can check it out directly from the repo. Sorry.

<details>
    <summary>Explanation</summary>

    1. State
    - We have two different state variables. One for handling the list, and the other for the text inside the input. Since both are aspects of the component that **might** change, and affect the way its rendered, it affects its current `State` and lifecycle.
    2. Handlers
    - `handleAdd` is the function that handles the way our items are added into the `items` state. The instructions inside are quite custom
    - `setItems([...items, { id: Math.random(), text}])` is quite the code. But fear not, all this does is iterate over the previous items (because we don't want to delte them) and add a new one with a random `id:` attribute, and the `text` recovered from the `input`
    - `setText('')` resets the text inside the input so it clears up when an item is added. 
    - `handleDelete` is rather simple. All it does is filter through the current items in state, and returns to `setItems()` the ones that **don't** match the current `id`. This way, we can delete an item from our array of items without any complex functions.
    - `handleEdit` is a mix between the previous both so let's look at it with more care:


```jsx
const handleEdit = (id, newText) => {
    // code here
}
```

Simply declares the function and sets its parameters.

```jsx
const handleEdit = (id, newText) => {
    setItems(items.map(item => ()))
}
```

So far, we only declare that `setItems` will have as parameter the *return* data of `items.map(item => ())`


```jsx
const handleEdit = (id, newText) => {
    setItems(items.map(item => (item.id === id ? { ...item, text: newText } : item)));
}
```

So this looks weird, right? But if we study it part by part and get some help from our one-eyed parrot, we'll realize that its a simple conditional that, if the id matches, it will reset the item's `text` attribute, and if it doesn't, then it will simply return the current item being mapped.

3. And that's pretty much everything it does.
- Separating our handlers from the `return()` method makes our code cleaner.
- Declaring our state at the top of the component is a good practice and the way its recommended. It also gives good context about what the component is doing without the need to go all the way down through all the code.
- While the code seems complex at first, its just a matter of diving into it and checking out line by line. 
- There's **always** documentation out there. 

</details>

### useEffect

1. What?

[`useEffect`](https://react.dev/reference/react/useEffect) is another basic hook that we can implement in our components. Unlike `state` however, its not as mandatory when handling state.

The implementation of `useEffect` and its use cases are a tid bit more about the component lifecycle. It's like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined in class components, but with a simpler and more intuitive API.

This hook is used to perform and handle *side effects* in our application. Such as *data fetching, subscriptions,* or *manual DOM changes*

To simplify things, this hook comes into play when **other** APIs, external data or manual override of the component happen. However, the implementation is quite simple.

```jsx
useEffect(() => {
// logic here
}, [])
```

In essence, the syntax is simple. 
- `useEffect` is the declaration (duh)
    - `() => {}` a simple callback where we will put all the necessary logic and the place where we will set our side effects (API calls)
    - `[]` a dependency array. If our component/code depends on some variable, change or some kind external execution, and when that variable changes we **need** to execute that array again, then this is the place where we put **that variable**. If the array is empty (it is in most cases), then `useEffect` will only run once. *If* and **when** the array is omitted, then `useEffect` will run after **every** render.


2. How?


Let's add a simple `fetch` function to a new component. Make sure to import it in your `App.jsx`.

As mentioned before, the data *fetched* from the API comes from an external third party source, so it's an excellent place to implement `useEffect`.

```jsx
import { useEffect, useState } from 'react';

function Card() {
    const [data, setData] = useState(null);
    // null is the initial state for our conditional rendering down bellow
    // another option is to set it as an empty array and make the condition check its length

    useEffect(() => {

        // Fetch data from API
        async function fetchData() {
            const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
            const result = await response.json();
            setData(result);
        }

        fetchData();

    }, []); // Empty array -> useEffect will run only once
    return (
        <div>
            {data ? <div>Data: {JSON.stringify(data)}</div> : 'Loading...'}
        </div>
    )
}
```

We also implement `useState` here to save our fetched data into the state of the component. But where that data comes from is the interesting part.
Since we don't want `useEffect` to execute multiple times calling our API over and over, the *dependency* array is completely empty.

- The logic inside `useEffect` is something we've seen before at this point in time. `Async/await` shoudn't be new concepts to us. The case is the same with `fetch()` and `response.json()`
- All we are doing here is declaring with `useEffect` that our fetch will be running once at component execution.

That's pretty much everything about `useEffect`.


## Extras

### Advanced Hooks and practice

Try the following exercise in your application

1. Make a component called `Astros.jsx`
    - Give it the basic `jsx` structure and import it into `App.jsx`
2. With the help of Hooks, do the following:
    - Make an API call to the following API: [How many people are in space right now](http://open-notify.org/Open-Notify-API/People-In-Space/)
    - If the link is dead (hopefully not), you can use the always available [PokeAPI](https://pokeapi.co/docs/v2)
3. Now, with the data of your response, make a small card to either show the current *astros* or multiple *pokemon*. Check the corresponding API documentation on to how to access that specific data.
    - If there are multiple people, you can use what we saw in the **Components** section to iterate through the array and get each object.

4. GLHF
