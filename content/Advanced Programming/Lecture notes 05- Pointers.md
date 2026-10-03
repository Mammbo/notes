# Pointers & Addresses
- pointers are the size of 8 bytes / 64 bits.
- * : dereferencing operator
	- follows the pointer and grabs what it is referencing

```C
int  *p; // type is int *
// it is a pointer to an int
// it can hold the address of another int variable
// it is written like this standardly because when you dereference it it will become an int.
```

# Pointer Types
- for every type there is a corresponding pointer type

```C
{
	int i = 1234; 
	double d = 3.14;
	int *pi  = &i;
	double *pd = &d;
	
	pi = pd; // two distinct types the compiler will not let this compile
	pi = (int *) pd; // by using type casting operator. this allows it to compile
}

// casting can be necessary and it can also be unpredictable, learn when to use it

// in this instance by type casting a size 4 byte int to a size 8 byte to store it in int it will only grab the first 4 bytes in memory, this cause it to interpret whatever as double is as half of it once it is stored in the int pointer.

```

### Void pointer
- special pointe that can take any type
- you can not dereference a void * so you must type cast the voide pointer to get the right type. 
# Null Pointers:

pointers just like integers can be used in boolean expression
pointers when they equal 0 are NULL
- this is because it is not a valid address and is never used
- when you try dereference this it will cause a null pointer exception and crash.![[Lecture 7.pdf]]