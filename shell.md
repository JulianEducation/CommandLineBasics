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
You can think of it almost like interactively executing a programming language you're familiar with -- like Python -- but where instead of calling functions or objects from the programming language, the "units of code" that you use are going to be entire programs, each with a job.

We can run any program -- including any you already use -- via a shell, but we will primarily be learning to run a suite of *new* programs you likely have not interacted with before.
The reason they are likely to be new is that they themselves are *textual* programs -- they, unlike graphical programs, do not draw nice menus or expect you to heavily use the mouse.
Their interface is instead more primitive -- it's simple text -- but also powerful and flexible, and specifically meant to be used here in this kind of environment.

## Running a program

You should by now be looking at this tutorial alongside a shell -- one running on a Linux computer which we've connected through via your browser.
If you don't see one, follow the link in the README of [this repository](https://github.com/JulianEducation/CommandLineBasics).

Think about what's happening here -- you have your local computer (a laptop, tablet or similar) which is showing you an interface being exposed by a second computer far away from yours.

You should see a *prompt* -- by default this will be a line ending in the `$` sign, and followed by a cursor shaped like a blinking square box (or sometimes a vertical line) where you're able to type.

At its most basic level, the prompt is similar to a text box you've encountered on a web page.
With the cursor blinking, if you type the letters `hello` (and nothing else), you should see each one appear.
If you hit backspace a few times, they disappear, and we've done nothing at all by typing them as long as we delete the letters.

The shell is waiting for you to give it a command to run, and will show you output that any program you run emits.
Let's run our first program.
A simple one to start with is:

```sh
date
```

Try running it now by typing it into the shell *without* the `$` and then hitting enter to execute it.
Within Google Cloud Shell you can also use the "Copy to Cloud Shell" button.

As a program runs it may show you output by *printing* it to the interface you see.
When a program exits, you'll see an identical prompt again, as the shell waits for you to tell it yet another thing to run.

The `date` program should have exited quickly, and shown you the current date and time.

We've just run our first program via a shell!

In the rest of the tutorial (and for the rest of this lecture) we'll learn about additional programs, and build up the library of functionality we can use at a shell.

A quick word of caution -- never run a command that you don't understand!
You should be running this tutorial from Cloud Shell, meaning regardless of what you do, your local machine is "safe".
Even if you remove important operating system files (accidentally or intentionally), as long as you are within Cloud Shell, you are not affecting your local machine.
Nevertheless, make it a habit not to run a command or program unless you understand what it will do first.

## Is This Linux?

We've just run a program -- and one claimed above to be running on a Linux computer.
How can we tell this is a Linux computer?
Many different operating systems can give us shells.
Is this one really running Linux?

The answer can be found using another program, one called `uname`:

```sh
uname
```

The `u` in `uname` is a "historical artifact".
It stands for `Unix` -- yet another family of operating systems which have influenced many more modern operating systems, to the point where we refer *collectively* to operating systems like Linux and macOS as "Unix-like operating systems" (for reasons we won't elaborate on much in this tutorial).
But the `uname` here is short for `unix name`, and is sort of asking the computer to tell you "what kind of Unix-like operating system are you?".
Ours sure enough says Linux.

### Command Line Options

Every program (including the 2 we've just learned) may take zero or more extra *arguments*.
Think of these again like passing arguments to functions or methods in programming languages you've seen, though the syntax is slightly different.
We'll dive deeper into passing arguments in just a moment, but let's learn about the first *kind* of argument, what are known as "options".
The `uname` command above told us we were on Linux, but it has more to say about what *version* of Linux we're using, for example.

Run:

```sh
uname -r
```

and you should see `uname` tell you what *version* of Linux this computer runs on top of.

Here, I see:

```text
5.10.133+
```

telling me this computer is running that specific version of Linux.
If you head to [the Linux development repository's list of releases](https://github.com/torvalds/linux/tags) you should be able to find that version somewhere in it.
You may need to scroll back in time, as Linux is released somewhat often.

What we added was three characters, a space character, followed by the two characters `-r`.
`-r` is an *option* that `uname` takes, one which tells it we are interested in seeing the "release version", not just that we're running on Linux.
Options are passed by simply adding some space and then typing the option on the command line.
Passing the `-r` option changed what `uname` showed us.
Options in general do this -- they tell the program we want it to behave differently from its default behavior.
Which options exist and how they affect a program *differ* from each program to the next.

If you run:

```sh
uname --kernel-release
```

you should see... exactly the same output as `-r`.
`--kernel-release` is just another longer (but easier to read) name for the same `-r` option.

## OK It's Linux... But What Distribution?

Linux comes in many *distributions* -- combinations of Linux itself along with additional programs, sometimes including a desktop environment (a graphical UI).
Anyone can create a distribution, so there are many of them, each suiting particular groups of peoples' needs.
For instance, some people really like always having the newest versions of all of the programs they want to use, so that they can immediately use new functionality that is added to them.
Others think constantly updating to new versions is painful because programs can change how they work in newer versions, which can disrupt getting work done by constantly having to learn about what's changed and why it's broken something you were used to doing previously.
There are distributions that cater more or less to each of these styles -- some which update the programs they distribute very rapidly, and some which do so more slowly but are extremely *stable*.
There are other distributions which cater to people who do creative work, like audio editing.
They come pre-installed with many programs useful for the particular use case they're designed for.

Which distribution are we using here in Cloud Shell?
We can answer that with yet another program:

```sh
lsb_release --all
```

which should tell you we're running a version of [Debian](https://www.debian.org/), an extremely popular and reliable Linux distribution.

The `lsb_release` program is one whose job it is to tell you information about the specific distribution of Linux being run.
`--all` is a command line option that it takes, which you can imagine simply shows *all* the information it knows.

## Navigating History

Before we go further, it's useful to point out a few more keyboard shortcuts which can come in handy.

When you're at the shell prompt, using the up arrow (or down arrow) moves backwards (or forwards) through your shell *history*.
Your history is the set of commands you've executed, often across sessions (meaning not just from your current use of the shell, also previous ones).

Try hitting up arrow now to bring the `date` command back, and execute it a second time, which now should produce a different output.

You can use left and right arrow to navigate within a command you're writing -- so if you make a mistake early in a command, you can fix it without backspacing, and then move back to the end of the line.

All of the *output* of commands you've executed will remain above your prompt, so if you execute a number of commands, you can use your mouse to copy output from any previous command.
If there's been enough output from previous commands, you'll see the screen begin to *scroll*, so that you still see a prompt at the bottom, but commands and output from earlier are no longer visible.
In Google Cloud Shell, you can scroll up and down the previous *output* with your mouse's scroll wheel (or with 2 fingers on your trackpad) if you want to see or copy something you know was printed out earlier that isn't visible on the screen where your current prompt is.

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

With no arguments, it opens a Python interpreter:

```sh
python3
```

At the interpreter you can interactively write any Python code you know.

You can exit the interpreter by typing `exit()` or hitting `^d` (remember that
`^` is shorthand for the Control key).
If you do so you should be back at a shell prompt.

### Positional arguments

The first kind of argument is one which we've used above with `echo` and `man` -- namely, a positional argument.
These can be either required (as is the case with `man`) or optional.

There is a Python file in this directory.
You can run it via:

```sh
python3 hello.py
```

where the argument to Python is the name of a file containing Python code to run.

When Python is given this one argument, instead of opening a REPL, it executes the file, quitting when it is done.

### Short options

If we look at `man python3`, we'll see one of the arguments it takes is one that looks like:

```terminal
  -c command
        Specify the command to execute (see next section).  This terminates the option list (following options are passed as arguments to the command).
```

What this is telling us is that we can write:

```sh
python3 -c 'print("Hello from Python")'
```

where we've given `python3` 2 additional arguments -- one, `-c`, and then an additional argument (which `-c` "consumes") containing a piece of Python code to run *instead* of opening the REPL.

You'll notice that we've placed the last command line output inside single quotes -- the reason we do so is because we wish to pass the entire contents of the quotes as one single argument to `python3`.
Remember -- shells split a command line each time they see a space.
If we had not quoted the final argument, the shell would interpret what we were passing itself, and pass a different argument to Python than what we intended.

Arguments that consist of a single hyphen followed by a single letter, such as `-c` in this case are common to many programs.

In general these arguments are often optional, and can typically be provided in any order on the command line -- for `echo`, running:

```sh
echo -n -e hello
```

is equivalent to running:

```sh
echo -e -n hello
```

### Long options

A second kind of argument are longer options, which often start with two hyphens, and which generally are named with full words rather than single letters.
Again from `man python3` we see `--version` is an argument which shows information about the Python version:

```sh
python3 --version
```

These long options are also generally optional and can be passed in any order in the command line.
Often, as is the case with `python3 --version`, there is a single-character shorter version of the argument which is functionally equivalent and shorter to type but harder to remember.

Options like `--version` and `--help` are common across many programs, so you often can try running `someprogram --help` when trying to learn how to use a new program.

Have a further look at

```sh
man python3
```

for more information on what the `python3` program can do.
Don't be overwhelmed if a lot of what you see is incomprehensible.
Try to understand the parts which use concepts we've covered in class.

## Files & Directories

You likely have had some previous exposure to interacting with directories or files on your computer from a programming language like Python (if you haven't don't worry, keep reading).

There are a number of programs available to us within the shell for interacting with directories and files on our machine (or here, our remote machine).

We first should note that whenever running programs from a shell, we do so with a *working directory*.
This working directory represents a directory within which we are running each program.
It might be a "project directory" if it contains files related to a single project or piece of work.
Some shell prompts will indicate this directory to us each time they wait for our input, so you've already seen the working directory we've been inside to the left of the `$` character in our prompt.
A program may sometimes change its behavior depending on the working directory we run it from.

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

We can *change* which directory we are in using `cd` (for "change directory"):

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

## `grep` and Regular Expressions

The `grep` program is extremely versatile as a way of *finding* things in files.

Alongside *regular expressions*, which are a generic tool we'll use from Python as well, we can easily write concise expressions that allow us to find substrings of interest from files and directories.

The basic usage of `grep` involves passing it a *pattern* and a file or directory to look through.
The pattern is written in a small language known as *regular expressions*.

The goal of this small language is to give us terse but powerful ways to represent a pattern of characters we want to find.

`grep` will use this pattern to *filter* which lines of a file match the pattern.

Here's our first example, which you should run from within the `alice` subdirectory:

```sh
grep Alice alice.txt
```

This, even though it may not look like it, is our first regular expression.

The string `"Alice"` will match any line which contains that sequence of characters.

So what you should see is all of the lines of the book which contain "Alice" on them.
All of the other lines of the book have been filtered out and not printed.

If all we could do was match literal text, regular expressions would not be very useful.
Much of their power comes from using some special syntax which allows us to find more general patterns in text.

### Anchors

The `^` character in a regular expression is an *anchor* -- it matches at the *beginning* of a line.

So the regular expression `^Alice` means "match the word Alice, but only at the beginning of a line".
Pass this regular expression to grep, and notice that now we get lines that contain "Alice", but only when it is the first word on the line.

The `$` character similarly is an anchor, and matches the *end* of a line -- so `Alice$` will match lines where "Alice" is the *last* word on the line.

### Character Classes

Regular expressions support *character classes* -- groups of characters.

As an example, we may wish to match *any* number within a body of text.
The general syntax for a character class is similar to that of an escape sequence in Python -- you use the `\` character followed generally by a single letter.
For example, `\w` is a character class which matches a "word character", i.e. any letter or number.

For example:

```sh
grep '\w\w\w\w\w\w\w\w\w\w' alice.txt
```

will print you all the lines of the file containing a word with at least 10 letters in it.

You can combine this with the above anchors to see if there are lines containing such a word at the beginning or end of them.

Other useful character classes are `\s` which matches any space character (space, tab, and a few others), as well as `\W` and `\S` which match the *inverse* of `\w` and `\s`, i.e. any *non*-letter-or-number and *non*-space character.

The `.` character within a regular expression matches *any* character at all.

So `grep . alice.txt` will find all lines that have 1 or more character on them no matter what it is.

If you ever want to match a period itself, use `\.` to escape it.

### Repetition

We can indicate we want to match *repeated* characters using a few different pieces of additional syntax.

Above we searched for words with 10 characters in them, but did so tediously with repeatedly using the `\w` class.
We can instead use:

```sh
grep '\w\{10,\}' alice.txt
```

where within the brackets we've said we want at least 10, and at most an infinite number of word characters.

The above syntax will apply to anything you tack it onto.
For instance, `o\{2,\}` as a pattern will match 2-or-more repeated o's in a word.
`man grep` has further details on repetition.

There are common shorter ways to write 0 or more or 1 or more.

If we want 1 or more of a character, `\+` is equivalent to `\{1,\}` -- so:

```sh
grep 'Alice \w\+$' alice.txt
```

will match the word "Alice" followed by a word with at least 1 letter, and then end of line.

Replacing the `\+` with a `*` will match 0 or more instances of the character.

### Exercise

As a quick exercise, see if you can use repetition to match lines containing the word `Alice` *twice* on the same line.

### Explicit Lists of Characters

We can give an explicit list of characters to match using square brackets (`[]`).

As an example:

```sh
grep '[abcde]\{5,\}' alice.txt
```

will match 5 or more repeated uses of any of the characters "a" through "e".

If you run this and find it hard to tell where in the line was matched, you may find it helpful to note the `--color` option to `grep`, which will tell it to highlight where in the line was matched:

```sh
grep --color=yes '[abcde]\{5,\}' alice.txt
```

### Case Insensitivity

Another useful option to be aware of is the `-i` argument to `grep`, which makes it case-insensitive.

Compare:

```sh
grep chapter alice.txt
```

to

```sh
grep -i chapter alice.txt
```

### There's more

We have only scratched the surface on regular expressions.

They can be used to perform lots of menial text matching that would otherwise be tedious to do "manually".
We'll see how they can be used from Python as well, where the syntax is very similar to what we've used with `grep`.

Regular expressions have a reputation for being easily overcomplicated -- meaning it's easy to write an incomprehensible long regular expression which you will have a hard time diagnosing when it doesn't behave as you expect.

If you use them for what they're meant for however -- short, simple but powerful parsing of substrings, especially interactively -- you have an important tool under your belt.

## Some Interactive / Long-Running Programs

Though some of the programs we've seen so far "stay open" when we run them, such as `python3` with no argument, for the most part programs we've run do a job and then exit.

Here are a few programs which you can try which have a more interactive feel:

### `top`

Your computer (or the Linux one we're using) has many programs running on it at once.

```sh
top
```

will show us information about many of these programs, most of which we have not covered.

### `less`

The `cat` program can be used as previously mentioned to spit the contents of a file out.

But what if you want to browse around the file?

That's what `less` is for.

Try running:

```sh
less alice/alice.txt
```

and note you can now use keys like the arrow keys to move around the file and read it at your leisure.
Hit `q` to exit `less`.

### `nano` and `vim`

If you don't want to just read a file but also *edit* it, now you want a command line text *editor*.

`nano` and `vim` are two very widely used and installed text editors.

Try running `nano alice/alice.txt` -- you should see you're able to insert or delete text at will.
Follow the instructions at the bottom of nano to exit, remembering that `^` means the `Ctrl` key.

`vim` is a text editor that is hugely powerful, and likely different from any other program you've used previously.
It would take a whole lecture or more to talk about `vim` itself, but for now you can notice that similar to `nano`, if you open our text file with it you can browse around with the arrow keys.
If however you try to insert some text by typing some letters, `vim` likely won't do what you're expecting.
Hit `Esc` a few times, then `:q` -- that's the colon key followed by the letter `q`, and then hit enter to quit `vim`.

## `curl` and `cheat.sh`

The `curl` program is a command line way to retrieve websites!

Whilst it's not a full-blown *browser* (though command line browsers indeed exist!), it can be used for retrieving a page or file from a website.

Let's see what it does for an extremely useful website you may not have heard before -- <https://cheat.sh/>.

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
  * `lsb_release`
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
  * `uname`
  * `vim`
  * `wc`

## Additional Resources

There's a nice "course" that was offered by MIT called ["The Missing Semester of Your CS Education"](https://missing.csail.mit.edu/).
Even if you aren't a Computer Science student you may find its page on [the shell](https://missing.csail.mit.edu/2020/course-shell/) to be helpful for a second perspective, and may find other lectures from it interesting to expand your knowledge on computing in general.
It also has a video which treats some of the material we've covered today.

You may also wish to go back through some of the programs we've covered and skim through their `man` pages.

If you've gotten this far, you may also now be comfortable enough to try out a shell on your own machine.

On macOS, you can find `Terminal.app` already installed, which gives you a shell on your computer.
Programs on macOS are similar but unfortunately not identical to those on Linux (due to macOS actually being a descendant of an operating system called BSD).
Luckily, macOS also gives you access to `man` pages, so you can refer to those whenever you encounter a difference.
The general concepts we've discussed should apply essentially unchanged.
You might immediately consider checking what `uname` tells you on `macOS`.
(Recall that it gives information about the operating system you're using.)

On Windows, you can have a look at [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) which you can install to give you access to Linux from your machine.
