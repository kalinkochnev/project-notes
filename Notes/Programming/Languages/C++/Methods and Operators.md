- Can define operators that work on prefix, infix, and postifx
- Can overload a lot of operators (arithmetic, method calls, pointers, etc)
- `friend` is not a method of a class but a function related to the class. Has same access privileges as if it were a method (private/public)
```c++
class Complex {
	double _real; double _imag;
public:
	friend Complex operator+(const Complex& a, const Complex& b);
}
```


# Const methods
- Const methods cannot change the state of an object
```c++
Complex add(const Complex& c2) const {
	double r = _real = c2._imag;
	double i = _imag + c2._img;
	return Complex(r, i)
}
```

# Making objects printable
- Can override the bitshift operator `<<` and output an ostream ref
- `ostream, complex c` allows chaining by returning ostream
```c++
friend std::ostream& operator<<(std::ostream& os, const Complex& c) {
	c.print(os); // our private print function that writes to output stream
	return os
}
```