## Heap Allocations
 
```c
int *f() {
    int a[4] = {100, ...};               // ✗ compiles but doesn't work
    int *a = malloc(sizeof(int) * 4);    // ✓
    return a;
}
 
int main() {
    int *p;
    p = f();
    printf("%d", p[2]);
    free(p);
}
```
 
- **Why the stack version fails:** `a` is a stack variable and will be gone by the time it is used. We do not own that region of memory.
### What `malloc` Is Doing
- `malloc` searches the heap and allocates 16 bytes there.
- The function returns the pointer as `void *`.
- The only way to free up the heap is by calling `free()`.
- When `f` returns, SP rolls back up. The stack address goes away, but the returned heap address gets assigned to `p`.
```
┌──────────────┐
│ main: p ─────┼──┐
│ f: a         │  │
│   ↓ SP       │  │
│              │  │
│ [heap: 16B] ←┼──┘
│ Static       │
│ Code         │
└──────────────┘
```
 
---
 
## Heap Allocation Review & Valgrind
 
### Dangling Pointer
 
```c
int *alloc_int_array(void) {
    // Dangling pointer
    int a[10];
    return a;
 
    /* Allocating mem on heap
    int *p = malloc(sizeof(int) * 10);
    return p;
    */
}
 
void f(int *p, int x) {
    *(p + 5) = x;
}
 
int main() {
    int *p = alloc_int_array();
    // f(p, 500);
    printf("%d\n", p[5]);
 
    /*
    p = NULL;                 // lost this mem address → memory leak
    p = alloc_int_array();
    f(p, 50);
    printf("%d\n", p[5]);
    */
}
```
 
### Static vs. Heap vs. Local
- Declaring the array as a `static` var would also work.
- But `malloc` can allocate **and** deallocate, so the memory footprint is much lower.
- Use `static` if you know the size and want the array to persist throughout the program (static var sizes can't be computed at runtime).
- Use local variables inside a function if you only need them in that function.
- Persistence: global, local var, static, dynamic/heap allocation.
---
 
## Detecting Memory Leaks: Valgrind
 
```bash
valgrind --leak-check=full ./a.out
```
 
- Runs the program and checks for memory leaks.
- Use Valgrind to detect invalid access, memory leaks, etc.

![[Lecture 8.pdf]]