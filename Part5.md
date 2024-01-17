# Part 5 - React Router DOM

## Table of Contents

<!-- toc -->

- [What is it](#what-is-it)
- [Setup](#setup)
  - [Installation](#installation)
- [Implementation](#implementation)
  - [Modifications](#modifications)
  - [Implementing](#implementing)
- [Extras](#extras)
  - [Practice](#practice)

<!-- tocstop -->

We're almost at the end of this cruise.
So let's continue our journey and finally get that treasure.

## What is it

[`React Router`](https://reactrouter.com/en/main)
is another important and very useful library when managing routes inside our application.
React adjusts perfectly to
[SPAs](https://medium.com/@theadkgroup/spa-vs-mpa-applications-what-are-the-differences-7dc004e62397)
but if we're really trying to make our app to work as a MPA (while not being one),
`React Router` is a great library that does just that.

What it does is very simple.
Let's say you have an application where `/` will showcase some projects you've done.
This `Home` component showcases the projects,
a small description about your company or something else,
and then some images bellow that will aid the user to have context of your app.
The rest of the page, however, has a `navbar`,
a `sidebar` and a `footer`.
You want these components to be available in every single `page`
of the app so we can *actually* reuse our components in different routes.

## Setup

This is one of the few times where I differ from the official docs.
[`React Router`](https://reactrouter.com/en/main) is an impressive library,
but their documentation isn't very clear for readers unfamiliar with it.

We'll follow the installation process they provide as it is similar to `MUI`.
However when implementing we'll take a simpler/quicker route.
Not quite different than the docs, but just simpler.

### Installation

Just run this command to add it as a dependency.
The official docs have some additional commands,
but they're not required for this implementation as we only want the basic functionality.
For further implementation and a complex resulting app, read the docs.
Check out different routes the library has (Hash, Memory, Static) and keep practicing.

```bash
npm install react-router-dom
```

An then run your app as usual.

## Implementation

### Modifications

We'll need to modify a bit our `main.jsx` file.
Currently, it should look like this:

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)
```

Well, modifications are simple.

We'll need to let our application know it'll work with a `<BrowserRouter>`
component imported from `react-router-dom`.
So, let's add it like so:

```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'; // add this line to import it
import App from './App.jsx'
import './index.css'

// implement it like so: 
ReactDOM.createRoot(document.getElementById('root')).render(
    <React.StrictMode>
        <BrowserRouter>
            <App />
        </BrowserRouter>
    </React.StrictMode>
)
```

### Implementing

#### Define a route

Let's skip the definition of a route, and just talk about what we need to define.
Say you have a route that will showcase a Hero component and some other `Main` section.
The collection of **components** you're showcasing are called a `view`.
So, we'll need to define a `view` for each route we need in our app.
As we previously talked about,
it's gonna be just three: `/`, `/about`, `/astros` (or `/pokemon` depending on your API).

Now that we have that settled, We'll add them to our `App.jsx` like so:

```jsx
// other imports
import {Route, Routes} from 'react-router-dom'


const App = () => {
  const links = [
    { name: 'Home', href: '/'},
    { name: 'About', href: '/about'},
    { name: 'Astros', href: '/astros'}


  return (
    <>
      <Navbar links={links} />
      <Routes> 
        <Route
          element={<Hero title='Hello Space Pirate!' />}
          path='/'
        />
        <Route
          element={<About />}
          path='/about'
        />
        <Route
          element={<Astros />}
          path='/astros'
        />
      </Routes>
  </>
  )
}
```

Let's explain this for a bit.

First, we let `react-router-dom` know which components will be displayed regardless of the route. As an example, we're doing this by declaring `<Navbar />` component **outside** of the `<Routes />` component. This way our `Navbar` will be visible regardless or the route and it wont need to be reloaded into the DOM.

`<Routes />` as of now indicates that the components inside it will be the ones changing.

```jsx
return (
  <>
    <Navbar links={links} />
    <Routes>
    </Routes>
  </>
)
```

Then, we'll declare the `views` that will be rendered for *each* `route`
using the imported `<Route />` component.
This component takes two basic attributes:

- `element` defines the `view` that will be available for that `route`.
  - This way, we can use only one component with multiple components inside.
- `path` defines the actual `route` with a simple String.

```jsx
return (
  <>
    <Navbar links={links} />
    <Routes>
      <Route 
        element={<Component />}
        path='/route'
      />
    </Routes>
  </>
)
```

Now, just customize it and add the other routes defined in your project.

#### Define our links

This part is a little strange.
Normally, to switch between routes inside a website/application
we use the `<a>` tag with some `href` in it.
And we can still use those with React.
However, since `react-router-dom` is actually a SPA working as a MPA,
we won't be switching `routes` as usual.
So our `a` tags will become a `<Link />` component directly imported from the library.

Let's modify our `<Navbar />` to work with that component like so:

```jsx
{
  links.map((link, index) => (
    <div key={index} className='navbar--link'>
      <Link to={link.href}>{link.name}</Link>
    </div>
  ))
}
// remember that using index as a key is discouraged but not forbidden
```

Quick small changes. `<Link />` works by letting the library know that this will reference one of the `path` attributes defined inside `App.jsx`.

- `to` is an attribute that works just as `href`
  - But it won't reload the entire page in order to access that route.
  - It will simply change to **that** `view` and refresh the DOM where necessary.

And that's it basically.

## Extras

### Practice

As an extra challenge, read the official docs and try the following:

- Research what the `*` wildcard is
- Try managing a `404` error with a custom `view`.
- How can you implement `state` to your `Navbar` component in order to add some functional styles and make the specific `Link` component be a different color to the others when inside that `route`?
