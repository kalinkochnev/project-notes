# Reading pointers
- You can start by trying to read a declaration backwards
```c++
const char* blah; // blah is a pointer to to a char that is constant
char* const blah; // blah is a constant pointer to a char
```

- You can use the [spiral/zig-zag rule](https://stackoverflow.com/a/34560439)
	- Read declaration from inside out, starting at variable name
	- Favor `[]` and `()` over `*`

Example:
```c++
void ( *(*f[]) () ) ();  
```
- f is an array of pointers to a function that returns a pointer to a function returning void
![[spiralrule.gif]]

# Pointer typing
- in C you can coerce pointers to be a different type (ex: can read a char pointer as an int)
- C++ pointers are strongly typed, but can be explicitly cast

## ways of casting
### C
```c
((*T)(a))
```
### C++
#### `static_cast<T>(e)`
- Converts between compatible types (checks at compile time)
```c++
int x = 10
char c = 'a';
int * p = static_cast<int*>(&c); // this does not work
```
- static casts work with classes and subclasses
#### `const_cast<T>(e)`
- allows you to change toggle the constness of expression (compile time)
```c++
const int x = 10;
int * p = const_cast<int *>(&x);
```
#### `reinterpret_cast<T>(e)`
- does basically what c does (bit level copying)
#### `dynamic_cast<T>(e)`
- Allows downcasting of compatible types at run time
- returns null if the cast failed


# Smart Pointers
https://learn.microsoft.com/en-us/cpp/cpp/smart-pointers-modern-cpp?view=msvc-170
- Use when allocating on the heap.
- When a smart pointer is initialized, it is an object created on the stack that points to some value on the heap
- When the object goes out of scope, since on stack, destructor gets automatically called and destroys the SP and frees memory properly
- Methods of smart pointer called using `.()` syntax. Methods of object pointed to are called via `->()` syntax

### Types of smart pointers
`std::unique_ptr<>` - a pointer to an object that is not copied or shared but can be moved. One owner only
`std::shared_ptr<>` - reference counted pointer that can be shared across multiple objects. Memory is valid as long as there is at least one owner.