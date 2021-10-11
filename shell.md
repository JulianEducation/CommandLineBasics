# Command Line Interfaces & the Shell

In this tutorial (and lecture) we'll be learning about running command line programs with a *shell*.

## What is a shell?

We're all familiar with running graphical programs.

Doing so on most operating systems involves locating the program in a menu, in a common shortcut location like a Desktop or Dock, or in another directory.
Clicking on a graphical program launches the program.

Running a browser is an extremely common graphical example – you're likely sitting within one to read this tutorial.

Interacting with a graphical program often means clicking buttons, using the mouse heavily and interacting with menus, graphics or icons.
There are great reasons why this is the primary way most people use a computer -- for the vast majority of "normal use", they are easier to understand and learn.

A shell is another *textual* interface for running programs, often interactively (meaning whilst continuing to give them input and see their output).

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
Even if you remove important operating system files (accidentally or intentionally), as long as you are within Cloud Shell, you are not affecting your local machine.
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

## Passing Command Line Arguments

A program may take one or more *arguments*.

How it handles these arguments (what it does with them and how they change or affect the program's behavior) depends on each program.

When using a shell, the shell take what you type as your command and *splits* or *parses* your command line.
It does so to extract which program you want to run, and what arguments you want to pass it.
Shells split a command line at each block of **space**.

The `echo` program is a simple program which merely echoes back each of its arguments.

Run

```sh
echo first second third fourth
```

and observe you see the 4 words you typed echoed back to you.

We have passed `echo` 4 arguments in this example, because there are 4 words separated by space after the name of the program.
You can pass it more or fewer arguments, its behavior will echo them back to you, however many there are.

This makes `echo` a bit like `print()` from Python.

## `man`

We've just used the `echo` program to echo a line of text.

If we want to learn more about what the `echo` program does, like perhaps whether it takes any additional arguments, we can use... another program!

The `man` program, which stands for *manual* is an interactive help program which can tell us about other programs and their usage notes.

It takes an argument -- the name of a program you wish to learn about.

Run:

```sh
man echo
```

and observe you see a page (or multiple pages) of output telling you how to use `echo`. You can hit `q` to exit what you see in `man`.

## Types of Command Line Arguments

As we've mentioned, each program may take different options or arguments, and handle them as it wishes.

In general there are 3 common styles of argument.
Let's see examples of each by looking at another program, one we're quite familiar with even if we have never used it directly... `python3`!

`python3` is a program which, unsurprisingly, runs Python code.

With no arguments, it opens the REPL:

```sh
python3
```

We can use all of the language features we've learned from the REPL.

### Short options

A program like `echo` or `python3` often takes a number of arguments which begin with a single hyphen (`-`) followed by a single letter, such as `-c`.

In general these arguments are often optional, and can typically be provided in any order on the command line -- so running:

```sh
echo -n -e hello
```

is often equivalent to running

```sh
echo -e -n hello
```

and occasionally to:

```sh
echo hello -e -n
```

`man python3` tells us:

```terminal
  -c command
        Specify the command to execute (see next section).  This terminates the option list (following options are passed as arguments to the command).
```

If we pass the `-c` argument to Python, `man` tells us it takes one *additional* argument after `-c` which represents a piece of Python code to run.

Try it by running:

```sh
python3 -c 'print("Hello from Python")'
```

You'll notice that we've placed the last command line output inside single quotes -- the reason we do so is because we wish to pass the entire contents of the quotes as one single argument to `python3`.
Remember -- shells split a command line each time they see a space.
If we had not quoted the final argument, the shell would interpret what we were passing itself, and pass a different argument to Python than what we intended.

### Long options

A second kind of argument are longer options, which often start with two hyphens, and which generally are named with full words rather than single letters.
Again from `man python3` we see `--version` is an argument which shows information about the Python version:

```sh
python3 --version
```

These long options are also generally optional and can be passed in any order in the command line.
Often, as is the case with `python3 --version`, there is a single-character shorter version of the argument which is functionally equivalent and shorter to type but harder to remember.

Options like `--version` and `--help` are common across many programs, so you often can try running `someprogram --help` when trying to learn how to use a new program.

### Positional arguments

The third kind of argument is one which we've used above with `echo` and `man` -- namely, a positional argument.
These can be either required (as is the case with `man`) or optional.

There is a Python file in this directory.
You can run it via:

```sh
python3 hello.py
```

where the argument to Python is the name of a file containing Python code to run.

When Python is given this one argument, instead of opening a REPL, it executes the file, quitting when it is done.

Have a further look at

```sh
man python3
```

for more information on what the `python3` program can do.
Don't be overwhelmed if a lot of what you see is incomprehensible.
Try to understand the parts which use concepts we've covered in class.

## Files & Directories

We've previously briefly discussed manipulating files and directories with the filesystem or directory hierarchy from Python.

There are a number of programs available to us within the shell for interacting with directories and files on our machine (or here, our remote machine).

We first should note that whenever running programs from a shell, we do so with a *working directory*.
This working directory represents a directory within which we are running each program.
Some shell prompts will indicate this directory to us each time they wait for our input.
A program may somehow change its behavior depending on the working directory we run it within.

As a first example, the `pwd` program is a program whose sole purpose is to *print* the working directory.

Try it:

```sh
pwd
```

A more interesting example of a program which changes behavior depending on the working directory is `ls`.

`ls` is a program which *lists* the contents of a directory.

Try running it:

```sh
ls
```

We can *change* which directory we are in using `cd`:

```sh
cd /tmp
```

See what happens in this new directory if you run `pwd` and `ls`.

Giving `cd` no arguments will default to changing our working directory to what's called the *home directory*.
On Linux here, home directories look like `/home/yourusername`.
(On macOS this would be `/Users/YourUsername/`.)
This directory is the "base" directory for one's own user.
If you were using a machine on a daily basis, you'd put most of your documents, downloads, files and applications within this directory, as it belongs to your user.

We can change back to our previous working directory above by giving `cd` an argument.

Run `cd` with the output you got in your original `pwd` command to put us back in the directory we started in when beginning this tutorial.

Confirm that you get the same results as before when running `ls`.

### Relative and Absolute Paths

We have briefly discussed that a *path* is a string of characters which represents a location on a computer.

`/tmp` is an example of a path we referenced above, where the root directory `/` contains a subdirectory named `tmp`, which we entered via `cd`.

Paths which begin with `/` are known as *absolute paths* -- they represent a fully described path on your computer.

In contrast are what are known as *relative paths*.
A relative path is a path *relative* to a working directory.

As an example, the current directory contains a subdirectory called `alice` (which contains a file called `alice.txt`).
The absolute path to this file will be long and contain many `/`'s.
But a relative path to this file is simply `alice/alice.txt`, where we leave off all of the path segments above our current working directory.

At a shell, it is much more common to refer to paths below your current working directory (i.e. children) via relative paths.

We can again for instance list the contents of the `alice` directory via:

```sh
ls alice
```

where `alice` is again a relative path.

There are three "specially treated" path segments.

`..` within a path refers to the *parent* directory of a path.

`.` refers to the path itself.

Observe for instance that:

```sh
ls ..
```

returns the children of the current working directory's parent -- meaning the current working directory is one of the entries in the output!

```sh
ls .
```

with the `.` argument will show you indistinguishable output as `ls` alone -- because it will list the current directory's contents.

Finally, `~` within a path *given at a shell* will refer to a home directory.

Run

```sh
ls ~
```

and confirm it shows the list of files in your current user's home directory.

You can combine these special path segments with additional path segments.

If you `cd` into the `alice` folder, you'll note you can run

```sh
ls ../README.md
```
to refer to a file in the parent directory we came from.

Use `cd ..` to `cd` back out of it again.

### File Contents & Manipulation

So far we've navigated around the directory tree without directly interacting with what is *inside* of a file or directory.

There are of course a number of programs which allow us to interact with creating, viewing or deleting files and directories.

From the directory we started in as our working directory, simplest of all is the `cat` command:

```sh
cat alice/alice.txt
```

which will simply print the entire contents of the file out to us.
The name `cat` comes from the word con-*cat*-enate -- and truthfully the program is useful for concatenating multiple files together.

Try:

```sh
cat alice/alice.txt README.md
```

and you'll see `cat` has shown both files one after the other.
But it is most often used simply to show a single file.

You'll find programs called `head` and `tail` useful to look at as well -- they'll show you lines from the beginning of a file or end of it respectively.
Try using them to pull off lines from our book.

Sometimes we want to copy, move or delete a file.

The `cp` program will make a full duplicate of a file:

```sh
cp alice/alice.txt 'alice/alice in wonderland.txt'
```

(Remember we need to quote paths which contain spaces in them.)

Use `ls` and `cat` to confirm that we now have two copies of the same file.

Other programs to be aware of (and try out) are `mv`, which moves files to a given second path, and `rm` which *deletes* files.

```sh
mkdir new-directory
```

will *create* a new empty directory with nothing inside of it.
The argument given is a path, perhaps relative -- so here, we have created a new subdirectory of the current working directory.

```sh
rmdir new-directory
```

will *remove* an empty directory, deleting it.

## `curl` and `cheat.sh`

The `curl` program is a command line way to retrieve websites!

Whilst it's not a full-blown *browser* (though command line browsers indeed exist!), it can be used for retrieving a page or file from a website.

Let's see what it does for an extremely useful website you may not have heard before -- https://cheat.sh/.

This site hosts examples and explanations for command line programs.

If you run:

```sh
curl cheat.sh/cp
```

you should see lots of examples about how to use `cp` shown to you.

Try visiting this page in your real browser and comparing.

## Summary

We've covered a number of commands or programs in brief so far.
Here's a unified list you might use to continue investigating them and others:

  * `bash`
  * `cat`
  * `cd`
  * `cp`
  * `curl`
  * `date`
  * `echo`
  * `exit`
  * `grep`
  * `head`
  * `less`
  * `ls`
  * `man`
  * `mkdir`
  * `mv`
  * `nano`
  * `pwd`
  * `python3`
  * `rm`
  * `rmdir`
  * `seq`
  * `sleep`
  * `tail`
  * `top`
  * `vim`
  * `wc`

## Additional Resources

The [extra learning resources document](https://docs.google.com/document/d/1XwMHRRP3Wwy8hLSGRYKVjqpQ20dMVhGLobRIqYG-goo/) which is linked in the syllabus contains a link to [MIT's "The Missing Semester of Your CS Education"](https://missing.csail.mit.edu/).

You may find its page on [the shell](https://missing.csail.mit.edu/2020/course-shell/) to be helpful for a second perspective.
It also has a video which treats some of the material we've covered today.

You may also wish to go back through some of the programs we've covered and skim through their `man` pages.
