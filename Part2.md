# Part 2

<!-- toc -->

- [Components](#components)
  - [Function components](#function-components)
    - [Parts of a component](#parts-of-a-component)
    - [How to](#how-to)
  - [Class components](#class-components)
- [Props](#props)
  - [What is it?](#what-is-it)
  - [How?](#how)
  - [Notes](#notes)
- [Extras](#extras)
  - [Advanced props and practice](#advanced-props-and-practice)

<!-- tocstop -->

## Components

Components in React can be likened to Lego blocks used in building structures.
Just as you would assemble various Lego pieces to create a design,
components are the building blocks you use to develop a maintainable app.
The advantage is, unlike physical Lego pieces where you might run out,
in React you can reuse components without needing to "buy" or create new ones.

The primary role of components is to:

- Simplify the development of the front-end aspect of an app.

They achieve this by breaking down the application into smaller,
more manageable chunks of code.
This modular approach facilitates easier development and makes testing more efficient.

Depending on your application's structure and design methodology chosen,
typical components might include:

- Inputs, Buttons, Badges, Lists, Tables, Navbar, Cards, Tabs, Select inputs, etc...

It's essential to structure your components based on your project's specific requirements.

### Function components

While relatively new, functional components will be the main way we'll be writing our React components since Class-based components are no longer often used anymore. Previously, Class components were the norm when writing a dynamic component. However with the introduction of Hooks in react, which we'll see soon enough, function components became just as relevant, if not more, to write compelling useful and reusable dynamic UI components.

#### Parts of a component
There are three main sections of a component that we should always take in mind.

    - Component **definition** is how our component is declared and how we'll make use of it. A common good practice is to delcare a components' name with *Pascal Case*. Hence if we're declaring a button component it should be `function Button() { ... }` instead of the usual *camelCase* declaration. As always, their name should describe exactly what they do

    - The **Body** of our component is where most of the necessary `javascript` logic will be declared and take place. Functions can be declared and used inside of functions, hence we can declare *handlers* to actually handle the components' internal logic.

    - The **Return** section of a component is the part there the `html` nodes will be declared and returned. And while multiple nodes can be returned, there should **always** be a single top level node to surround the child elements.

```jsx
function Button() {
    const greeting = 'Hello pirate!';
    return (
        <>
            <button>{greeting}</button>
        </>
    )
}

export default Button;
```

#### How to

Well, pretty simple in fact. All you need to do is export the component from it's own file (if that's how you manage your components) and then import it wherever you'd like to implement it.

    - Importing `Button` component inside `App`

```jsx

import Button from './Components/Button.jsx'

function App() {
    return (
        <Button />
    )
}
```

And that's it really. Whenever you want to use a component just make sure you're importing it from the correct route inside your project and write the necessary lines of code. Depending on the complexity of the component and/or internal logic of its *state* you might need to aditional syntax to make it work. But this is the basic structure for a simple non-dynamic Child->Parent component.

### Class components

This is a class component

```jsx
class Button extends React.Component {
    const greeting = 'Hello Pirate!';
    render() {
        return <button>{greeting}</button>
    }
}
```

Thank you for coming to my Ted Talk

## Props

### What is it?

Props are what makes our components and applications reusable by allowing a way for parent components to pass data to the child components (amongst other things).
The actual word `props` isnt' quite reserved unlike something like `const / let`. However it *does* represent a good practice and up to a certain point, a standard in react components and the React community, which is why it's crucial to adhere to this convention for readability and maintainability of code. Remember, the objective is never to reinvent the wheel, but to make it faster and safer.

The word `props` refers to the properties of a component. These are all the attributes, data and information the component will need from its *parent* component in order to be properly rendered.

To make matters a lot simpler, it's similar to the information of a simple `html` tag like so:

```html
<body>
    <input type='text' id='email' class='input secondary' />
</body>
```

In the previous snippet, **type, id && class** are the properties of the input tag. The use of this properties is irrelevant. What matters is that it helps the tag be *identified* and *implemented* properly. Hence, **props/properties**

If you've noticed by now, our Components are functions that when implemented turn into some kind of `html` tag.
Well, they too need properties to work in a dynamic manner.

### How?

Well, it starts with very simple code. 

1. Create a component called `Hero.jsx` inside your *Components* directory. And write the code like so:

```jsx
const Hero = () => {
    return (
        <h1>Hello pirate!</h1>
    )
}

export default Hero;
```

2. Now import it inside `App.jsx`

```jsx
import Hero from './Components/Hero.jsx'

function App() {
    return (
        <Hero />
    )
}
```
**Q:** Okay but how is this any different?  
**A:** It's not.

3. So let's switch it up by making the parent component `App.jsx` send some `props` into its child component:

```jsx
import Hero from './Components/Hero.jsx'

function App() {
    return (
        <Hero title='Hello Pirate!' />
    )
}
```

4. And now accept `props` into the child component and have it render inside the `<h1>` tag by inserting the object.

```jsx

// Remember that a component is just a function, and properties are received through paremeters
const Hero = (props) => {
    return (
        <h1>{props.title}</h1>
    )
}

export default Hero;
```

**Q:** But what is actually inside props?  
**A:** Well, log it out!

```jsx
const Hero = (props) => {
    // study this output
    console.log(props);

    return (
        <h1>{props.title}</h1>
    )
}

export default Hero;
```

As you might've noticed by logging `props`, the result is nothing but an object that will contain the properties of the child component passed from its parent component. So, all "attributes" sent from the parent component will be available here. And just as with html elements, you can send from the parent component as much infrormation as you need, so long as it is actually needed.

### Notes 

- `Props` are **read-only** and a component should never modify its own props.
- Fun fact, it's also a common practice to use [object destructuring](https://www.javascripttutorial.net/es6/javascript-object-destructuring/) just like in vanilla js when reading props. This way your code is cleaner and easier to read. Its also more manageable when in the process of maintaining it.
We'll return to destructuring in a later section tho.

```js
const Hero = ({title}) => {
    // instead of using props.title, we can now access the title property directly
    console.log(title);

    // same here
    return (
        <h1>{title}</h1>
    )
}

export default Hero;
```


## Extras

### Advanced props and practice

Try making a component called Navbar. Give it the necessary styles to be at the top of the page with full width, and render the following:

1. A text called Space-app on the left.
2. Three links on the right.
    - Home
    - About
    - Astros

Now, inside `App.jsx` insert the following code:
- Remember to import the component

```jsx
const App = () => {
    const links = [
        { name: 'Home', href: '/'}
        { name: 'About', href: '/about'}
        { name: 'Astros', href: '/astros'}
    ]

    return (
        <>
            <Navbar links={links} />
            <Hero title='Hello Space Pirate!'/>
        </>
    )
}
```

3. And with the use of the previously seen `props` logic, alongside some `vanilla js` help, render all the links:

```jsx
const Navbar = ({links}) => {
    return (
        <nav>
            <div class='nav--title'>
                // etc
            </div> 
            <div class='nav--links'>
                {
                    links.map((link, index) => (
                        <a class='nav--link' key='index'>{link.name}</a>
                    ))
                }
            </div>
        </nav>
    )
}

export default Navbar
```

4. Study what happens
    - How are the `<a>` tags rendered?
    - Why is there a callback function?
    - What happens if you remove the `key prop` from the element?
        - This will come in handy in the future and is an important aspect of React and child components.
    - Why is there no return fuction?
    - What the heck is `<> </>` and why is it so important?
