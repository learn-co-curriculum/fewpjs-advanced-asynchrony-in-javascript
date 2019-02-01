# Advanced Asynchrony in JavaScript

## Learning Goals

- Define asynchrony
- Identify differences between asynchronous and synchronous execution models
- Demonstrate linear time flow versus non-linear time

## Introduction

Asynchrony is a multi-layered concept, and understanding all the layers is
essential for a web programmer who wants to create powerful and efficient
JavaScript code. As we begin our deeper dive into the foundational layers of
asychrony in JavaScript, we'll recall the general principles of an aysnchronous
execution model, how that differs from a synchronous model and what it looks
like in practice.

## Define Asynchrony

Let's imagine you're preparing a meal for your friends. You've settled on a menu
of vegetarian lasagna, salad, rolls and sherbert for dessert. There are a couple
of ways to go about this. You could put together and bake the lasagna entirely,
then make the salad, then make the rolls, then dish the sherbert, then serve the
meal. However, if you do it this way—waiting for each item or tasks to be
complete before beginning the next—you risk warm food getting cold and cold food
getting warm, and, more to the point, your friends getting irritated with you.

It's more sensible to work on tasks at the same: for example, making rolls and
salad while the lasagna is baking, and dishing sherbert as guests are finishing
dinner. This approach means you're not sitting around waiting for something to
get done when other tasks are waiting to be done as well. This approach is also
what characterizes asynchrony. In a programming context, it means how a program
handles events concurrently, rather than consecutively.

## Identify Differences Between Asynchronous and Synchronous Execution Models

Let's start examining this from the point of view of a typical synchronous
execution model. Often a program runs straight through a list of tasks. If one
task needs a result from another task, the former has to wait for the latter to
complete, then return. In the meantime, the program seems that it's not doing
anything at all to the person using it. Not only is this a frustrating
experience for that person, the process doesn't employ computer resources very
efficiently. But if we can run tasks parallel to each other, we can get more
completed in less time, with no apparent down time for the user—something that
is essential for the modern, fast-paced web. So an asynchronous execution model
makes a lot of sense for web programming. But how does it work underneath the
surface?

## Demonstrate Linear Time Flow Versus Non-Linear Time

Remember `setTimeout()`? It's a great example of synchronous versus
asynchronous.

If we were to log a few things in the console in synchronous order, we'd want
some code like this:

```js
console.log("First!")
console.log("I'm totally happy with second.")
console.log("Hey, I made it!")
```

If you put that bit in your own console, you'll see each value show up exactly
in the order it ran.

And now for some asynchronous action:

```js
console.log("First!")
setTimeout(() => console.log("Hey, I made it!"), 5)
console.log("I'm totally happy with second.")
```

After this runs, it's clear that the value that we see come second in the code
actually shows up at the end in the console, thanks to the `setTimeout()`
function that holds it back.

As we explore asynchrony in more depth, we'll get into more complicated flows,
but you can keep this example as a foundational piece to build on as we go.

## Conclusion

Asynchrony provides us web programmers with a way to handle events in a more
efficient way than working through them one at a time. It's also more complex,
so it requires more thought and planning—but as we create more complex web
experiences, both we and our users will benefit from its use.

## Resources

- [Mozilla Developer Network: Introducing Async JavaScript](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing)
