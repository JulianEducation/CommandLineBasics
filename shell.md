# Command Line Interfaces & the Shell

In this tutorial (and lecture) we'll be learning about running command line programs with a *shell*.

Hit the start button to begin.

## What is a shell?

We're all familiar with running graphical programs.

Doing so on most operating systems involves locating the program in a menu, in a common shortcut location like a Desktop or Dock, or in another directory.
Clicking on a graphical program launches the program.

Running a browser is an extremely common graphical example – you're likely sitting within one to read this tutorial.

Interacting with a graphical program often means clicking buttons, using the mouse heavily and interacting with menus, graphics or icons.
There are great reasons why this is the primary way most people use a computer -- for the vast majority of "normal use", they are easier to understand and learn.

A shell is another *textual* interface for running programs.

We can run any program via a shell, but we will primarily be learning to run a suite of *new* programs you likely have not interacted with before.
The reason they are likely to be new is that they themselves are *textual* programs -- they, unlike graphical programs, do not draw nice menus or expect you to heavily use the mouse.
Their interface is instead more primitive -- it's simple text -- but also powerful and flexible.

## Running a program

You should by now be looking at this tutorial alongside a shell -- one running on a Linux computer which we've connected through via your browser.
If you don't see one, follow the link in the README of [this repository](https://github.com/JulianEducation/CommandLineBasics).

Think about what's happening here -- you have your local computer (a laptop, tablet or similar) which is showing you an interface being exposed by a second computer far away from yours.

Let's run our first program. You should see a *prompt* -- by default this will be a line ending in the `$ ` followed by a cursor, where you're able to type.

The shell is waiting for you to give it a command to run, and will show you output that any program you run emits.

A simple first program is:

```sh
date
```

Try running it now by typing it into the shell *without* the `$` and then hitting enter to execute it.
Within Google Cloud Shell you can also use the "Copy to Cloud Shell" button.

As a program runs it may show you output by *printing* it to the interface you see.
When a program exits, you'll see the prompt again.

The `date` program should have exited quickly, and shown you the current date and time.

We've just run our first program via a shell.

In the rest of the tutorial (and for the rest of this lecture) we'll learn about additional programs, and build up the library of functionality we can use at a shell.

A quick word of caution -- never run a command that you don't understand!
You should be running this tutorial from Cloud Shell, meaning regardless of what you do, your local machine is "safe".
Nevertheless, make it a habit not to run a command or program unless you understand what it will do first.

## Navigating History

Before we go further, it's useful to point out a number of useful keyboard shortcuts.

When you're at the shell prompt, using the up arrow (or down arrow) moves backwards (or forwards) through your shell *history*.

Your history is the set of commands you've executed, often across sessions (meaning not just from your current use of the shell, also previous ones).

Try hitting up arrow now to bring the `date` command back, and execute it a second time, which now should produce a different output.

You can use left and right arrow to navigate within a command you're writing -- so if you make a mistake early in a command, you can fix it without backspacing.

All of the *output* of commands you've executed will remain above your prompt, so if you execute a number of commands, you can use your mouse to copy output from any previous command.

## `Ctrl-c` to interrupt

Finally, before we go much further, you should be aware of the *Ctrl-c* keyboard shortcut.
*Ctrl-c* in a shell will send what is known as an *interrupt* or *signal* -- but what this means is often that if you have either a command you want to "cancel", or a long-running program is running and you want it to stop running, you can hit *Ctrl-c* to do so.
We also by convention use the `^` character to represent the `Ctrl` key, so you will see the above shortcut written `^c`, which means to hold down the `Ctrl` key and hit `c`.
Try it now by typing `date` at the prompt, but instead of hitting enter, hit `Ctrl-c`.
You should see that your command was not run.

The `sleep` program is a program which does nothing but wait a number of seconds before exiting.

We pass it the number of seconds to wait as an *argument*, which in a shell is done by separating the argument by spaces:

```sh
sleep 120
```

which will sleep for 2 minutes.

We don't have that long to wait, so after a few seconds, hit `^c` to kill the sleep program.

## Command Not Found

If you ask the shell to run a program which doesn't exist, it will show an error by simply printing some output to you.

Run

```sh
a-program-which-does-not-exist
```

and observe that sure enough the shell tells us the command is not found.

## bash

You'll notice that in the shell we are using, the line printed for "command not found" is prefixed by *bash* -- this is the name of the shell we are using!
There are other shells you may encounter (or choose to use), each of which are slightly different from each other, but `bash` is a very common one.

Note that `bash`, the shell, is itself a program!

We can run `bash` itself by typing its name at the prompt, just as we have so far: 

```sh
bash
```

Nothing appears to have changed -- but that's because the nested `bash` we have just ran has the same *interface* (appearance and behavior) as the outer shell we started with.
In an informal sense which we'll make more precise later, the "inner" bash we've just run now is the program which is receiving what we type on the keyboard, and which will show us output when we hit enter within it.
Try running one of the commands we've run previously, which now runs within the inner bash.

We can see that we're inside a second instance of the shell by using the `exit` command, which exits a shell:

```sh
exit
```

If you run it once, you'll exit the nested `bash` we ran, and be back at a similar looking prompt which now is our original "outer" shell.
If you run it a second time, you'll exit the outer shell Google Cloud Shell opened for you, and thereby close the tutorial.
