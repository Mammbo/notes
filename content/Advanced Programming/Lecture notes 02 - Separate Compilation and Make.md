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

