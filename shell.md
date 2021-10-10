# How do we run command line programs with a shell?

## The Shell

We're all familiar with running graphical programs.

Doing so on most operating systems involves locating the program in a menu, in a common shortcut location like a Desktop or Dock, or in another directory.
Clicking on a graphical program launches the program.

Running a browser is an extremely common graphical example – you're likely sitting within one to read this tutorial.

Interacting with a graphical program often means clicking buttons, using the mouse heavily and interacting with menus, graphics or icons.
There are great reasons why this is the primary way most people use a computer -- for the vast majority of "normal use", they are easier to understand and learn.

A shell is another *textual* interface for running programs.

We can run any program via a shell, but we will primarily be learning to run a suite of *new* programs you likely have not interacted with before.
The reason they are likely to be new is that they themselves are *textual* programs -- they, unlike graphical programs, do not draw nice menus or expect you to heavily use the mouse.
Their interface is instead more primitive -- it's simple text.

### Running a program

You should by now be looking at this tutorial alongside a shell -- one running on a Linux computer which we've connected through via your browser.
If you don't see one, follow the link in the README of [this repository](https://github.com/JulianEducation/CommandLineBasics).

Think about what's happening here -- you have your local computer (a laptop, tablet or similar) which is showing you an interface being exposed by a second computer far away from yours.

Let's run our first program. You should see a *prompt* -- by default this will be a line ending in the `$ ` followed by a cursor, where you're able to type.

The shell is waiting for you to give it a command to run, and will show you output that any program you run emits.

A simple first program is:

```sh
date
```

Try running it now by either typing it into the shell *without* the `$`.
Within Google Cloud Shell you can also use the "Copy to Cloud Shell" button.

It should exit quickly, and show you the current date and time.
