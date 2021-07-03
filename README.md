# Git Hooks Examples
This repository will explain what git hooks are and show examples of some common use cases and impelentation of hooks 

----------

## What are Git Hooks? 
Git hooks are scirpts you can write to proform actions on certain triggers
#### Examples Please!
In my team we wanted to make sure people adhrear to our standards of branch naming. so we made a script to run after each commit.
It checked the name of the branch to against a regex to make sure it didn't break our rules, if it did the commit was rejected and a message was displayed to the user.

#### But how does it work??
Hooks reside in the *.git/hooks* directory of every Git repository. In there you can see the default hooks (**notice that they have the .sample sufix, that means they are inactive**)
Each hook fires on a different git action (you can see which by their name).

##### But wait, the .git folder isn't cloned, how can I share my majestic creations with my teams?? 
Great question! what I recommand doing is moving the scripts you want to run to a folder in your repository that will be cloned (let's say */hooks*). Lastly you (and all of your team) will need to reconfigre git to look for hooks to run in your new folder. You do this by running the following command: `git config core.hooksPath hooks`

##### But in what language do we write them?
That's the beauty of it, you can use any scripting language you like as long as it can be run as an executable. The shebang line `(#!/bin/sh)` in each script defines how your file should be interpreted.
So, to use a different language, all you have to do is change it to the path of your interpreter.

#### Great, where do I start?
In the src folder of this repository you will find two hooks ready for use. 
- **pre-commit**: Which checks if your branch name conformes to a given regex.
- **pre-push**: Which Checks if you are trying to push to the test branch, and if so forces you to change the version number. 

Both are hooks used in my team and will not necessarily fit to your needs, but feel free to use them as a base to build your own hooks!

