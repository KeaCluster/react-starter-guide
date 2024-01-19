# Part 6 - Adjustments and resources

<!-- toc -->
## Adjustments

### Optimization

There are multiple things that we can add but people have different views on them.

For example, [memoization](https://react.dev/reference/react/memo)
is an existing concept of computer science and software engineering.
This technique is used to speed up programs by storing the result of heavy function calls.
This makes that result reusable if the same input occurs.
It basically means *creating a memory of precomputed values* in order to optimize.
However the adjustments for this change would require further reading and investigation.

Another technique involved would be [lazy loading](https://react.dev/reference/react/lazy#lazy).
This allows us to implement [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
Which are a common js practice, to render a component.
Which can come in handy when, and where, large files like images are involved.

Adding to all of this.
Almost every library and/or module implemented has its own documentation.
This allows us to verify the best practices when implementing new technologies.
(Material UI && React Router).

- Keep testing and debugging your code.
- Implement code-splitting to break down the app into smaller blocks of code.
- Optimize your dependencies and remove unused libraries/ packages.
- State Management and its proper implementation can result in significant improvements regarding performance.
- Accessibility.
  - I consider this an important subject as applications should follow the Web Content Accessibility Guidelines (WCAG)
  - Adding to this, certain software quality standards can help a lot.

## Deployment

### Preparation

Thanks to [vite's](https://vitejs.dev/guide/build) amazing docs,
the process of building our application is very simple.

A common practice is to have a branch specifically for production,
where we can keep the final files ready for our server to use.

We're going to add a new branch called `prod` to our project using `git`

```sh
git checkout -b prod
```

This should create a new branch as well as change to it.
Once we're there, and we've made sure all final changes are in it
(you can `git pull` to get them)
The next step is to build our app.

## Resources
