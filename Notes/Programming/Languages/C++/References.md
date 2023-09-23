- Same purpose as pointers. Has cleaner syntax but more strict rules (can't do arithmetic with references)
- Can think of it as an alias to the original data
- References must be initialized as soon as they are defined
- Allows you to write directly to the variable you are referencing without using the star syntax to de-reference

*example*
```c++
const int &y = x;
// y is a reference to an integer that is constant 
```

# In arguments
- When passing objects around, it makes sense to use a reference since you don't want to pass them around by value
- If you add const, you can prevent overwriting a reference
```c++
int sumOf(const string& a);
```
