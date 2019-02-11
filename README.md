# Advanced Asynchrony in JavaScript

## Learning Goals

- Define asynchrony
- Identify differences between asynchronous and synchronous execution models
- Demonstrate linear time flow versus non-linear time

## Introduction

Asynchrony is a concept that many developers consider to be "hard" or "weird."
Nevertheless, it's an essential concept within JavaScript (and many other
languages) that you must understand in order to reason about what the code is
doing. Be patient as you work with this material and be sure to conduct
experiments on your own to ensure your understanding.

As we begin our deeper dive into the foundational layers of asynchrony in
JavaScript, we'll review the general principles of an asynchronous execution
model, recall how that differs from a synchronous model, and examine examples
of what it looks like in practice.

## Define Asynchrony

Let's imagine you're preparing a meal for your friends. You've settled on a
menu of vegetarian lasagna, salad, rolls and sherbet for dessert. There are a
couple of ways to go about preparing your menu. You could put together and bake
the lasagna entirely, make the salad, make the rolls, scoop out the sherbet,
and then serve the meal.

_However_, should you do it this way &mdash; waiting for each item or tasks to
be complete before beginning the next &mdash; you risk warm food getting cold
and cold food getting warm, and, more to the point, your friends getting
irritated with you.

It's more sensible to make small bits of progress on multiple tasks at the same
time, rotating between the tasks as fast as possible. For example, we could
make rolls and salad while the lasagna is baking, and dish sherbet as guests
are finishing dinner. This approach means you're not sitting around waiting for
something to get done when you can make progress on other tasks.

This approach is also what characterizes asynchrony. In a programming context,
it means how a program handles events concurrently (Latin for "running together at the same time"), rather
than consecutively (Latin for "running after each other"). In the cooking example above you are like JavaScript:
moving between the various food preparation tasks. You await signals that tell
you one task is done ("beep-beep" from the microwave; the smell of burning rolls
from the oven; a smart-speaker triggering your lasagna timer, etc). In the browser context , while data is being fetched
with `fetch()`, JavaScript lets the browser do other things (like animate .gifs
or open a new tab).

Let's dig deeper.

## Identify Differences Between Asynchronous and Synchronous Execution Models

Let's start examining this from the point of view of how code runs in
synchronous-by-default languages like Ruby or Python.

Often, a program runs straight through a list of tasks. If one task needs a
result from another task, the former has to wait for the latter to complete,
then return. In the meantime, the program seems that it's not doing anything at
all to the person using it. Not only is this a frustrating experience for that
person, the process doesn't employ computer resources very efficiently.

However, if we run tasks parallel to each other, we get more completed in less
time, with no apparent down-time for the user &mdash; something that is
essential for the modern, fast-paced web experience. So an asynchronous execution model
makes a lot of sense for web programming. But how does it work underneath the
surface?

## Demonstrate Linear Time Flow Versus Non-Linear Time

Let's consier `setTimeout()` It's a great example of synchronous versus
asynchronous. Its code looks like:

```js
setTimeout(function, wait_time_in_milliseconds)
```

More concretely:

```js
setTimeout(() => console.log("Hello world"), 2000)
```

You can run this example in your console and see that after a 2-second wait, JavaScript
prints `Hello world`.

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
setTimeout(() => console.log("Hey, I made it!"), 5) // .005 second. Not very long!
console.log("I'm totally happy with second.")
```

After this runs, we see that the value that we see come **second** in the
code actually shows up **last** in the console, thanks to the `setTimeout()`
function that holds it back.

But what if we were to make the `setTimeout()` delay `0` seconds versus `5`?

```js
console.log("First!")
setTimeout(() => console.log("Hey, I made it!"), 0)
console.log("I'm totally happy with second.")
```

The code in the `setTimeout()` **still** runs last. From JavaScript's
perspective, it reads `setTimeout()` and says I have 1000 milliseconds in which
to do work (that's a long time for computers; it's comparable to waiting for a
lasagna to bake, from our example). As such, JavaScript runs the
`console.log()` action. Eventually the `setTimeout()` finishes (hundreds of
milliseconds later) and runs the second `console.log()` action.

As we explore asynchrony in more depth, we'll get into more complicated flows,
but you can keep this example as a foundational piece to build on as we go. If
you can verify your understanding with `setTimeout()`, you can apply the
understanding in other asynchronous contexts.

## Conclusion

Asynchrony provides web programmers with a way to handle events in a more
efficient way than working through them one at a time. It's also more complex,
so it requires more thought and planning &mdash; but as we create more complex
web experiences, both we and our users will benefit from its use.

## Resources

- [Mozilla Developer Network: Introducing Async JavaScript][async]

[async]: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing
