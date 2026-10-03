# Storage Classes: 
1. Automatic variables, local, variables, stack variables
2. static variables
	1. global static
	2. file static
	3. block static

```C
int y = 0; // glocal vars with global scope, 
// global vars not initalized will init to 0. 
void f(int p // type 1) { 
	printf("%d", p);
	int x; // type 1
	x = 0;
	{ // you can dclare a block to limit scope this block defines the scop 
		int x; // type 1
		x = 1;
		printf("%d", x); 
	}
}
```

## Static Variables

![[Screenshot 2026-10-03 at 3.21.01 PM.png]]


# Process Address Space:
- two types of computer memory
1. volatile memory --> RAM
2. storage memeory --> ssd/ HD
we will focus on 1. (RAM)

- when you run a file the code gets run in the bottom portion of ram, below that a small portion of ram is reserved and not used
- when a program gets loaded multiple times, these are called processs (browsers e.g)
- computers work in vritual memory, they map virtual memory to real RAM
- each process in virtual memory thinks it is the ony process on the computer running on the entire RAM using 512 GB of RAM
- CPU & operating system handl mapping process to physical RAM
- Static variables get allocated before the rest of the process. 
- the heap is something you can call and control with malloc() allowing you to manually control this portion of memory
- stack grows and shrinks as vars are declared, used,  and returned.

### virtual memory layout
┌──────────────┐  512 GB
│    Stack                                            │  ← local variables, grows down ↓
├──────────────┤
│                                                          │
│ (really big                                        │
│    space)                                          │
│                                                          │
├──────────────┤
│     Heap                                            │  ← malloc(), grows up ↑
├──────────────┤
│ Static Vars                                      │  ┐
├──────────────┤ ├ minimum size of program
│     Code                                           │  ┘
└──────────────┘  0 (unused)

# Stack Variable Allocations

- stack grows down
- Stack Pointer
	- points to the bottom of the stack 
	- handled by the CPU 
	- each byte has an address
	- after variables are used and go out of scope, the stack pointer rolls back up to where it was initally. 
	- compiler knows how big the stack needs to be implicitly 
	- base pointer points back to the start of the program


![[Lecture 6.pdf]]![[Lecture 7.pdf]]