# Function pointers and templates
```c++
// Run time substitution
bool cmp(const double &a, const double &b);
template<class T>
bool find(vector<T> &x, int (*cmp)(const T&, const T&))

// Compile time substitution
bool cmp(double a, double b)

template<class T, int (*cmp)(T, T)> // function is passed by value in template
bool find(std::vector<T> x, const T &v);
```


- Templates can take in types as well as values
	- Templates make the substitution at compile time instead of run time
- Lambdas are closures. Must specify what variables to capture from environment and whether to capture by copy or by reference
- Function pointers are closures with no state (except global variables)

# Lambda structure

```c++
//closure format
[<what to go in and how>](parameters) -> return type {body};

// we use auto because the type is difficult to write out
auto cmp = [](int a, int b) -> int {};
```
- Capture list parameters are 
```
[] - capture nothing
[=] capture everything by value
[&] capture everything by reference
[captureList] - capture named entities comma separated
```

# Specifying function type
- C++ has a standard type to notate lambdas as a parameter (used with templates often)
```c++
// format
std::function< return_type(parameter type list,)> function_name
// ex
bool find(vector<T> &x, const T& v, std::function<int(double, double)> cmp)
```

## Passing in a lambda (runtime)
- This is only necessary when using a lambda at runtime
```c++
// notice we instantiate a function object with std::function()
bool foundIt = find(x, 2.0, std::function<int(double, double)>([] (double a, double b) -> bool{
	// do stuff
}))
```

# Bind
- You can "fix" a parameter for a function. 
- Ex: if `f(a, b, c)`, we can write `g(a, b) = f(a, 4, b)` by doing
```c++
auto g = bind(f, _1, 4, _2);
```

## bind by value
- occurs by default
- it is essentially doing this
```c++
auto mybind(const std::function<int(double, double> &f, double b) {
	// captures and fices f and b, from mybind
	// returned function only takes one param
	return [f, b](double a) {
		return f(a, b);
	};
}
```

## bind by reference
- Must specify explicitly
```
std::ref - ask for capture by reference of type T
std::cref - ask for capture by reference of type const T
```

ex:
```c++
int n1 = 1, n2 = 2, n3 = 3;
std::function<void()> bound_f = std::bind(f, n1, ref(n2), cref(n3))
```
