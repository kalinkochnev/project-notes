```c++
#include <iostream> // standard headers
#include "myheader.h" // user headers
```
- `#include` is a macro. Must protect against multiple inclusions of headers
	- Can have indirect includes through headers or direct inclusion through source file
	- Protect against with 
```c++
#ifndef __<name>_H     
#define __<name>_H <-- arbitrary variable name
#include "<name>.h"
#endif
```
- `-I<pathname>` includes path to search for headers

# Namespace
- Namespace a group of named entities (constants, classes, variables, etc)
- `using namespace std`  gives access to specified namespace in scope
- Custom namespace
```c++
namespace CSE3150 {
	int foo(int n) { // src here }
}
```

# Linking
- `gcc -c` means only compile (spit out object file)
- `gcc -g` add debug information (both for compilation and linking)
![[Pasted image 20230829211112.png]]