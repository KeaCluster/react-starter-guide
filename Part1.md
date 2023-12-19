# Part 1 - Setup, structure and basic info

<!-- toc -->

- [Project Initialization with Vite.js](#project-initialization-with-vitejs)
- [Directory Structure](#directory-structure)
  * [Structure information](#structure-information)
    + [Files](#files)
- [Introduction to React](#introduction-to-react)
  * [Vite is not React](#vite-is-not-react)
  * [React as a library](#react-as-a-library)
- [DOM and Virtual DOM](#dom-and-virtual-dom)
- [JSX](#jsx)
  * [What's on the files?](#whats-on-the-files)

<!-- tocstop -->

We'll go through the steps to initialize a React project (No TS) using Vite.js.

## Project Initialization with Vite.js

1. **Install Node.js**:
    - Ensure you have [Node.js](https://nodejs.org/en/) installed.
    - Vite requires Node.js version 12.0.0 or higher.
        - The latest stable release (LST) is always recommended.
        - Remember that with Node.js npm should also be included.

2. **Create a new project**:
   - Open your terminal and run the following command to create a new project:

     ```bash
     npm create vite@latest my-react-app --template react
     ```

     Replace `my-react-app` with the desired project name.

     - Make sure to select the proper options when running the command.
        - If on windows, try executing the command on `cmd` or `git bash`.
        - Sometimes either won't allow the use of arrow keys for selection.

        - First selection: **React**
        - Second: **Javascript**
        - If you select any other option, remember that the simplest solution at this point can be to delete the project and start over.

3. **Navigate to your project directory**:
   - Once the project is created, navigate to the project directory:

     ```bash
     cd my-react-app
     ```

4. **Install dependencies**:
   - Install any necessary dependencies using npm.
        - This command is only necessary for the initial setup

     ```bash
     npm install
     ```

5. **Start the development server**:
   - Now, start the development server:

     ```bash
     npm run dev
     ```

    This command will start the Vite development server.
    You should be able to see your new React app running at [http://localhost:\$PORT](http://localhost:$PORT).
    Change the `$PORT` space to adjust to the port `vite.js` just gave you.
    (It's always on display on your terminal)

6. **Inspecting the project**

You can now start inspecting your project!

- Open the `src` directory, and you'll find an `App.jsx` file.
- You can begin writing your React code.
- Remember to **study and inspect** before you make any changes.

## Directory Structure

Below is the directory structure for our React project initialized with Vite.js.
**If you are missing any directories make sure to create them for future use**

```plaintext
/root
│
├── /public
│   ├── /images
│
├── /src
│   ├── /Components
│   ├── /assets
│   ├── App.css
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
│
├── README.md
├── index.html
├── package.json
└── vite.config.js
```

### Structure information

As with any project using *vite*, the moment you init, a directory is created.
It's Important to identify the structure of the project inside this `root` directory.
It's where all the magic happens &  where the rest of the development will occur.

- `/root` isn't really called root.
  - This is a way of calling the main directory where our project is saved.
  - This directory should have the name of your application.

- `/public` is a directory that's visible to the end-user if inspected.
  - therefore, must never contain sensitive data. or any kind of information.
  - Most web applications and/or sites have this directory to store media that will be showcased to any end-user once the application is running.
- `/images` should be inside the `/public` directory.
- `/src` is the main directory for our entire project.
  - This folder will host most of our custom code.
- `/Components` will host all of the necessary `.jsx` files to make our application reusable and maintanable.

#### Files

- `App.jsx` is the main file to host all of the application's *main* components.
  - While it should end up relatively small in size and in loc,
  Its where all of our components meet.
- `App.css` and it's structure will vary depending on how the project's styles are managed. Different frameworks work with different methods, and the source to make a decision regarding style handling inside our React application comes from it's requirements.
  - `index.css` is a simple yet efficient css file just like any other.
  - `main.jsx` is a simple yet important `.jsx` file.
    - It contains lines to link our `App.jsx` file to the **always** required `index.html`.

Keep fidgeting with the rest of the files.
Try to figure out what's going on inside and study the code already in them.
It'll be important later.

## Introduction to React

### Vite is not React

React is sometimes called a framework and sometimes a library.
If you're still confused, read the [Docs](https://react.dev/).
Vite has as much to do with React as a pirate has to do with a boat.
A boat can very well be sailed without a pirate,
but toss a pirate into the mix and suddenly there's a quest for buried treasure,
a catchy sea shanty,
and a parrot squawking unsolicited coding advice from the crow's nest.

Anyway, Vite is the place that starts the sailing,
but the pirate is ultimately the one responsible for looting the ~~british~~ army
and getting all the treasure.

### React as a library

You can start your development journey without vite.
In fact, its what companies do out there in the real world
since they have plenty more freedom to customize their project,
and only have what they'll really need in order to make their application work.
This optimizes their development environment,
as well as their final product.
Since this is a *test*, we won't be going that route as you might've noticed.

React alongside several modules will give us necessary tools to develop
(and build) a small ~~stable~~ application to showcase what we've learned.

What makes the magic happen is the way React implements Components.
Small dynamic and modular pieces that allow for reusable and clean code.
Keeping our app size relatively small.
Components can interact with one another if our code allows them to.
Which is what we're ultimately aiming for; simple, reusable, clean, scalable code.

## DOM and Virtual DOM

The DOM, as you should know by now, works in a similar structure to a tree.
It has nodes and links that bind these nodes together in a tree-like structure.
Each node represents an html element, with it's attributes, classes, id, etc.

**DOM Tree:**

```plaintext
body
├── header
│   ├── logo
│   └── nav
└── main
├── section
└── footer
```

VDOM Tree:

```plaintext
body (v1)
├── header (v1)
│   ├── logo (v1)
│   └── nav (v2)
└── main (v1)
├── section (v2)
└── footer (v1)
```

React operates with both the real DOM and a Virtual DOM (VDOM).
The VDOM is an abstract representation of the DOM tree,
which React utilizes to track changes in the state of nodes efficiently.
The state of a node can vary from simple interactions like clicks,
to substantial changes such as navigating to a different route within the application.

For managing significant state transitions or routing,
additional libraries like React Router are often employed.
However, for smaller state changes,
React provides ample control over how state is managed and component state handling.
This is where the Virtual DOM shines.

Every component in React has a state, and theoretically, a component can host an arbitrary number of child components, similar to how a DOM node can contain several other nodes.

Consider a scenario where a user is navigating through a contact list, viewing 15 contacts at a time. Should the entire application reload with every click to view the next set of contacts? Or should only the contact list update? Well, the next time the user wants to check the list of users they've blocked over a heated argument about which k-pop idol is better, they're going to find themselves interacting with good user experience.

This comparison process is known as reconciliation, and is crucial for React's performance optimization. It's managed by a library called ReactDOM, which handles rendering React components to the DOM and updating them efficiently when the state or props change.

## JSX

### What's on the files?

To simplify things, React can use `html` node elements inside `javascript` functions and classes.
To be more precise, it doesn't do that at all. How react actually works is by implementing a special kind of syntax called `JSX`. This syntax allows the use of what seems like `html` elements inside `javascript`, but in reality its an extension of the usual javascript syntax with `XML` elements enabling for an intuitive and readable structure for defining UI.

- HTML-like. But not really.
  - JSX provides a syntax easily readable by people familiar with `html` and `xml` tags.
  - All the usual nodes can be implemented here.
- JSX is more closely related to Javscript than HTML.
  - This allows us to implement all of the necessary `javascript` logic and make interactive dynamic and reusable components by wrapping variables or `js` snippets in `{}`.
- JSX -> JS.
  - JSX is not supported by current browsers.
  - This results in the need for a transpiler tool such as Babel.
  - In this 'automated' process, JSX elements turn into regular JS with the help of `React.createElement()` function calls.
- Component declaration.
  - JSX is used as the usual way to declare components in react. 
  - This makes it a standard throughout applications.

Some JSX example:

```jsx
// declare a component which returns the jsx data
const component = (
<div>
<h1>Hello, pirate!</h1>
<p>Can you eye the difference between html and jsx?</p>
</div>
)

// Uses magic functions and renders inside the root element of an html document.

ReactDOM.render(component, document.getElementById('root'))
```
