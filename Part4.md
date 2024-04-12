# Part 4 - Material UI implementation

<!--toc:start-->

- [Part 4 - Material UI implementation](#part-4-material-ui-implementation)
  - [Installation](#installation)
    - [Setup](#setup)
  - [Implementation](#implementation)
    - [Usage and compatibility](#usage-and-compatibility)

<!--toc:end-->

The use of a component library is very much used out there.
Just how [Bootstrap](https://getbootstrap.com/) is often
implemented for responsiveness and quickness when building a site,
there are libraries and collections of components available for React.

One we could call _fundamental_ would be [Material UI](https://mui.com/).

Since the library is in constant change, as with anything else,
the main source for support we could have are the amazing source
[docs](https://mui.com/material-ui/).
Take in mind, `MUI` isn't the only library available inside the _Material_ environment.
There's also `Joy UI`, `Base UI` and `MUI System`.
You can check the docs for more info on those.
Maybe on your project `Base UI` will be enough to to work.
Always check your requirements carefully and adapt your workflow to them.
Never the other way around.

## Installation

These instructions might change depending on the version.
But as of `v5.14.12`, the following should work perfectly.

- Installing `Material UI` with its default values is just one command away.
  - `MUI` works with `@emotion` as its styling engine.
  - Those are some extra [docs](https://emotion.sh/docs/introduction) to check out.

Run the following on your terminal inside the project root directory:

```bash
npm install @mui/material @emotion/react @emotion/styled
```

Most of the components' examples in the library implement the library's icons,
however they don't come with the installation above.
If you'd like to add them (we will for demo purposes) just execute the line bellow.

```bash
npm install @mui/icons-material
```

You can also add the module to the first install like so:

```bash
npm install @mui/material @emotion/react @emotion/styled @mui/icons-material
```

### Setup

If everything went according to plan,
now we should have the follwing lines in our `package.json`

```json
{
  "dependencies": {
    // some more dependencies here
    "@emotion/core": "^X.x.x",
    "@emotion/react": "^X.x.x",
    "@emotion/styled": "^X.x.x",
    "@mui/icons-material": "^X.x.x",
    "@mui/material": "^X.x.x"
    // or here
  }
}
```

Run your project again and now we can add some components into our App.

## Implementation

Depending on the component you'd like to add, you'll need to first check the documentation.

Let's add an `AppBar` component.
Hopefully [this link](https://mui.com/material-ui/react-app-bar/)
is still alive and redirects to the proper docs.

As you can see, `mui` has plenty of options to choose from.
All you need to do is check your reqs,
and perhaps modify it a bit to make it work to your specifications.

- Choose the component of your choice and click `show code` button right bellow it.
- You should see two options `JS` and `TS`.
  - Remember that we're not implementing `TS` here,
  - So just copy the code of the `JS` section.
- Paste it on your `AppBar.jsx` component
- Import and add it into your `App.jsx`
- Check the results

### Usage and compatibility

The usage you have for the components depend of the app you're building.
Remember to always measure twice before cutting, and keep things simple.
This basically means to evaluate all the options at your disposal before integrating.
If your app is a simple web site with zero or minimal dynamic content
and works as a showcase/portfolio, perhaps neither `React` nor `MUI` is a good option.

`React` is an amazing library,
however where it really shines is inside applications
that will probably scale up or have internal logic depend
on external non-controlled events/resources such as user-events, API calls, etc...
