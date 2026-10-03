# CLI Review [[Lecture notes 01 - CLI Basics]]
- basic stuff that is in the previous one 


## Vim
 
**Setup:** follow the config steps from the setup email the professor sent out.
 
### Navigation
| Command | Action |
|---|---|
| `gg` | Jump to the top of the file |
| `G` | Jump to the bottom of the file |
| `zz` | Center the current line on screen |
| `z` then `Enter` | Redraw with the current line near the top of the screen |
| `Ctrl-f` | Scroll one screen **f**orward |
| `Ctrl-b` | Scroll one screen **b**ackward |
 
### Editing
| Command | Action |
|---|---|
| `o` | Open a new line **below** and enter insert mode |
| `O` | Open a new line **above** and enter insert mode |
| `u` | Undo |
| `Ctrl-r` | Redo |
 
### Visual mode (highlighting)
| Command | Action |
|---|---|
| `v` | Highlight character-by-character |
| `V` (`Shift-v`) | Highlight by **line** |
| `Ctrl-v` | Highlight by **column** (block select) |
| `=` (while highlighted) | Auto-indent the selection |
 
> **Tip:** highlight the whole file (`ggVG`) and press `=` to auto-indent everything.
 
### Command mode
Press `:` to run more complex commands.
 
| Command | Action |
|---|---|
| `:set number` | Show line numbers |
 
---
 
## Compiling C code
 
Invoke the `gcc` compiler:
 
```bash
gcc hello.c -o hello    # compile hello.c into an executable named `hello`
./hello                 # run it
```
 
---
 
## Separate compilation
 
The idea: compile each `.c` file **into an object file** (`.o`), then **link** the object files into one executable.
 
```
.c files  ──(compile)──▶  .o object files  ──(link)──▶  executable
```
 
Key flags:
 
- `gcc -c` → **compilation only** (produces a `.o`, no linking)
- `gcc *.o -o program` → **link** object files into the final executable
### Worked example
 
```bash
gcc -c -Wall -g myadd.c          # → myadd.o
gcc -c -Wall -g myprogram.c      # → myprogram.o
gcc myadd.o myprogram.o -o myprogram   # link both → executable
./myprogram                      # run it
```
 
---
 
## Function declarations, prototypes & headers
 
When compiling `myprogram.c` on its own, you get a **warning** (not an error) because
`myadd` was never declared in that file — the compiler doesn't yet know its signature.
 
**Fix it** by adding the function's prototype (declaration) to the file that calls it:
 
```c
int myadd(int x, int y);
```
 
- You can **declare** (prototype) a function in as many files as you need.
- You must **not define** it more than once — there can be only **one definition** of a
  function across the whole project.
### Using a header instead
 
Rather than writing the prototype by hand, include the header:
 
```c
#include "myadd.h"
```
 
At compile time the **preprocessor replaces the `#include` line with the entire contents
of `myadd.h`**, then continues from there.
 
> `#include <stdio.h>` does **not** contain the code for `printf` (or any other function) —
> it only provides the **prototypes**. The actual implementations get linked in later.
 
**Best practice:** `#include` your own `.h` file *inside its own `.c` implementation* too.
That way the compiler can warn you about parameter mismatches between your declaration and
your definition.
 
---
 
## GCC flags reference
 
Example:
 
```bash
gcc -g -Wall -c -o hello.o hello.c
```
 
| Flag | What it does |
|---|---|
| `-g` | Include debugging info (used later in the course) |
| `-Wall` | Enable **all** warnings (great for catching bugs) |
| `-c` | Compilation only (no linking) |
| `-o <name>` | Set the output filename (e.g. `-o hello.o`) |


# Makefile 
- Make is a program that allows you to compile and link everything faster.
- We use a makefile, which is the spec for making things
- Start by writing the target file, then colon, then the list of ingredients

Ingredients -> dependecies / prereqs
`myadd.o: myadd.c myadd.h`

Make knows when to check the timestamps of the last modifications of the file to check when to recompile a program or not. (saves time)

you then need to tell make what to do: the command
`gcc -c -Wall -g myadd.c`
Make file is old and annoying and needs to only use tabs and spaces:

ex make file:
`myAdd.o: myAdd.c myAdd.h
	gcc -c -Wall -g myAdd.c`

Cat command to debug make: 
-t shows tab character
-e shows leading spaces etc
-n shows line numbers
cat -ten Makefile

make Commands: 
make filename: makes that sepcific fil

# Makefile Dependency Ordering

## The rule shape

```make
target: prerequisites
	recipe
```

- **target** — the thing being built (a file, or a phony name like `clean`)
- **prerequisites** (a.k.a. dependencies) — what the target is built _from_
- **recipe** — the shell command(s) that build the target (must be TAB-indented)

## How Make decides what to do

When you ask Make to build a target, it works **bottom-up (dependencies first)**:

1. **Read the target's first line** to find its prerequisites.
    
2. **Recurse into each prerequisite first** — before touching the target, Make makes sure every dependency is itself up to date. If a dependency is also a target with its own dependencies, Make repeats this whole process on it.
    
3. **Compare timestamps** once the dependencies are settled:
    
    - If the target **doesn't exist**, or
    - If **any prerequisite is newer** than the target (i.e. changed since the target was last built),
    
    then the target is **out of date** and its **recipe runs**.
    
4. If the target is newer than all its prerequisites, it's already up to date and Make **skips the recipe**.
    

## Key ideas

- **Ordering comes from the dependency graph, not the order lines appear in the file.** Make figures out the build order by walking prerequisites recursively.
- **Timestamps drive rebuilds.** Make uses file modification times to decide "did this change?" — only changed pieces (and whatever depends on them) get rebuilt.
- **This is what makes Make incremental** — it avoids recompiling things whose inputs haven't changed.

## Tiny example

```make
program: main.o utils.o
	gcc main.o utils.o -o program

main.o: main.c
	gcc -c main.c

utils.o: utils.c
	gcc -c utils.c
```

Asking for `program`:

- Make sees it depends on `main.o` and `utils.o` → resolves those **first**.
- `main.o` depends on `main.c`; if `main.c` is newer, recompile `main.o`.
- Same check for `utils.o`.
- Finally, if either `.o` is newer than `program` (or `program` is missing), relink `program`.

Edit only `utils.c` → Make rebuilds `utils.o` and relinks `program`, but **leaves `main.o` alone**.

# Declaring variables:
```make
CC = gcc
CFLAGS = -g -Wall
program: main.o utils.o
	$(CC) main.o utils.o -o program

main.o: main.c
	$(CC) -c  $(CFLAGS) main.c

utils.o: utils.c
	$(CC) -c $(CFLAGS) utils.c
```
 since we declared the variables at the top of the file we can just omit the lines and it will just know what we want to run because of the declared variables, they are default ones make knows about. This is called Make Implicit Rules.

# defining a command to clean

```make
CC = gcc
CFLAGS = -g -Wall
program: main.o utils.o
	$(CC) main.o utils.o -o program

main.o: main.c
	$(CC) -c  $(CFLAGS) main.c

utils.o: utils.c
	$(CC) -c $(CFLAGS) utils.c
	
.PHONY: clean --> this makes it so make doenst check for a file named clean, if it did exist this would break
clean: 
	rm -f *.o myprogram
	
.PHONY: all 
all: clean myprogram --> does all of this.
```
curl -O https://cs3157.github.io/www/2026-9/code/02/Makefile.  --> donwloads the makefile.
# Git basics
git init --> initalizes git repository
git status --> checks commits and files you are (un)tracking
- untracked files git does not know about
- tracked, modified, and staged --> ready to commit
- tracked, unmodified --> files tracks and nothing has changed
- tracked, modified, but unstaged --> modified the file but did not add it to staging so its not ready to commit
git diff --> shows you changes of tjhe file
git diff --cached --> shows the difference between staging and what was committed before.
git add file --> tracks files

git log --> tells us what we have done
git log -u --> same thing but with all the diffs
git rm --> removes a file from staging

git mv old_file new_filw --> renames a file

# Homework Submission Process w/ Git

1. git config --global user.name "Your Full Name"
2. git config --global user.email your_uni@columbia.edu
3. create cs3157 directiory set permissions to 700
	1. cd 
	2. mkdir cs1357
	3. chmod 700 cs3157
4. setup command line email configs
	1. cd
	2. cp /home/jae/cs3157-pub/conf/.muttrc ./
5. cd cs3157
	1. git clone /home/jae/cs3157-pub/labN labN

MW 11:30 am – 12:30 pm, 621 Mathematics Building.
1. Submit the lab:
	1. only include
		1. header files,
		2. c files
		3. make files
		4. readme
	2. make clean
	3. git status
		1. make sure there is nothing missing / committed that shouldnt be to submission
	4. run /home/w3157/submit/submit-lab lab1
2. verify submission
	1. .mbox --> is the submission 
	2. clone lab1 again as a test repo 
	3. git am ../labN/.mbox file
	4. apply the patch  
	5. go into the lab1 timestamp submission and test every code but making sure everything compiles and works, make and test everythign

# Lab Submission Checklist

- **Test in the submission dir** — after submitting, a timestamped submission dir appears; build & test *there*, not just your working dir. If it fails there, no points (even if it works in yours).
- **README** — include name, lab #, UNI, and a description of each part. Every lab.
- **No generated files** — submit `.c`, `.h`, `Makefile`, `README` only. No `.o` files or executables (we build from your Makefile). Extras may cost points.
- **Commit ≥ 5 times** per lab.
- **Makefile** — use `gcc` (not `cc`) with `-g` and `-Wall`.
- **Verify Makefile** — run `cat -ten Makefile`: commands must start with a single TAB (`^I`), and blank lines must have no stray TAB/space (`$` marks line ends).