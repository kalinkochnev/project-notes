# Strings

- The `std::string` object is stored on the stack but has data that points to the heap (the characters itself)


# Functions
- Function parameters are called by value, meaning a copy is made of the variable when passed into the function

# Datatypes
Sizes of various types
```
- char [1], short [2], int [4], long[4, 8] (depends on machine), long long [8]
- float [4], double [4]
- signed/unsigned versions
- bool [1]
```
- Density of floating point precision is greater closer to 0

# Arrays
- Char arrays must end with the terminator `\0`, so # of characters + 1 is len
- array variable is a reference to memory on the stack
```c++
char s2[] = "hello"; // automatically puts \0, s2 is a memory address
```

- Can iterate through array with pointer arithmetic
```c++
int * px = new int[10];
for( int* cx = px; cx < px+10; cx++){ 
	*cx = cx - px;
}
```
# Pointers

- Can "take address of" using &
```C++
char s2[] = "hello"; //  s2 is already address
char * p = s2; // has the same address as s2.
```

- Or "fetch from the address" (dereference)
```C++
char s2[] = "hello";
char * p = s2;
*p = 'T'; // dereference the pointer p and assign the character
```

### Memory model
- Memory model has static/globals, stack, heap

##### Global
- Global has lifetime of whole program
- A reference to static is always fine
##### Stack
- Stack variable has lifetime of function it is created in
- References are invalid after function completion
##### Heap
- The `new` keyword creates an object on the heap, `delete` frees from memory
	- new is an operator that receives a type
```c++
int * px = new int;
*px = 20;
delete px;

// array allocation
int * px = new int[10];
delete[] px;
```
- any allocation on heap has lifetime for however long until it is freed
- Addresses are the highest level memory access, so addresses may be very large
