# Part 2

## Components

Components in React can be likened to Lego blocks used in building structures. Just as you would assemble various Lego pieces to create a design, components are the building blocks you use to develop a maintainable app. The advantage is, unlike physical Lego pieces where you might run out, in React you can reuse components throughout your app without needing to "buy" or create new ones.

The primary role of components is to simplify the development of both UI (User Interface) and UX (User Experience). They achieve this by breaking down the application into smaller, more manageable chunks of code. This modular approach not only facilitates easier development but also makes testing more efficient.

Depending on your application's structure and the atomic design methodology you prefer, typical components might include:

- Inputs, Buttons, Badges, Lists, Tables, Navbar, Alerts, Cards, Tabs, Select inputs, etc...

It's essential to structure your components based on your project's specific requirements.

### Function components

While relatively new, functional components will be the main way we'll be writing our React components since Class-based components are no longer often used anymore. Previously, Class components were the norm when writing a dynamic component. However with the introduction of Hooks in react, which we'll see soon enough, function components became just as relevant, if not more, to write compelling useful and reusable dynamic UI components.

1. Parts of a component
    There are three main sections of a component that we should always take in mind.
    - Component **definition** is how our component is declared and how we'll make use of it. A common good practice is to delcare a components' name with *Pascal Case*. Hence if we're declaring a button component it should be `function Button() { ... }` instead of the usual *camelCase* declaration. As always, their name should describe exactly what they do
    - The **Body** of our component is where most of the necessary `javascript` logic will be declared and take place. Functions can be declared and used inside of functions, hence we can declare *handlers* to actually handle the components' internal logic.
    - The **Return** section of a component is the part there the `html` nodes will be declared and returned. And while multiple nodes can be returned, there should **always** be a single top level node to surround the child elements.

```jsx
function Button() {
    const greeting = 'Hello pirate!';
    return (
        <>
            <h1>{greeting}</h1>
        </>
    )
}
```

### Class components

## Component composition

## Props
