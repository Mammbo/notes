# Arrays: 
- work basically the same as in  other langugaes 
- array DO NOT throw an exception when you go out of bounds in C. 
- array take up a contigous space in memroy

## Sizeof()
- size of operator output the size of in byte of what you give it, 
- you can also evaluate type to get their size.
- when getting the size of pointer / memory address no matter the type it is of size 8 bytes.

## Pointer Arithmetic
 
```c
foo() {
    int a[4] = {100, 101, 102, 103};
    int *p = &a[0];   // taking the address of a single element
 
    for (int i = 0; i < 4; i++) {
        printf("%d", a[i]);       // ┐
        printf("%d", *(p + i));   // ├ equivalent, does not change p
        printf("%d", p[i]);       // ┘
    }
 
    p++;                  // changes p
    printf("%d", *p++);
}
```
 
```
       2000  2004  2008  2012
a:   [ 100 | 101 | 102 | 103 ]
p:   [ 2000 ]
```
 
- In general, all **postfix operators have higher precedence than prefix** operators.
- You can add a number to a pointer.
- **`p + 1` means:** find the underlying data type, get the size of that type, and add it to the pointer (the next byte).
- C allows pointing **1 past the last element**, but you can't read it.

## Grand Unified Theory (GUT) of Pointers & Arrays
 
```c
int a[4] = {100, ...};
int *p = &a[0];   // or: int *p = a;
```
 
**I)** `a[i] ⟺ *(p + i)`
 
**II)** `a ⟹ &a[0]` (in most cases)
Exceptions:
```c
sizeof(a);       // 16
sizeof(&a[0]);   // 8
```
 
**III)**
- `a[i] ⟺ *(p + i) ⟺ *(a + i)`
- `a[i] ⟺ *(a + i)`
- `p[i] ⟺ (&a[0])[i] = a[i]`
- `p[i] ⟺ *(p + i)`
**III Final:**
```
u[i] ⟺ *(u + i)     // u = array or pointer
```
 
```c
a[2];
2[a];   // compiles by GUT III, but it is dumb
        // ⟺ *(2 + a) ⟺ *(a + 2) ⟺ a[2]
```

## Pointer vs. Array
 
1. `sizeof(a)` vs `sizeof(p)` → 16 vs 8
2. `p++` ✓ / `a++` ✗
3. Array size in a parameter is ignored. C doesn't let you pass an array:
```c
   int f(int a[10]) { ... }   // the 10 will be ignored
   int f(int *a)  { ... }     // what it really is
```
 ![[Lecture 8.pdf]]