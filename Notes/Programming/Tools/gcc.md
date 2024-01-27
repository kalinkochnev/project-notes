## What do the args of g++ mean?

For the `make debug` command in our makefile, which looks like this

```makefile
**motif_x_debug:
	mkdir -p ./bin
	g++ -pg -DDEBUG -g -std=c++0x -I./header -I/usr/include/biolib -o ./bin/motifx ./src/motifx_step_output.cxx ./src/motif_representation.cxx ./src/motifxinput.cxx ./src/motifx.cxx ./src/motifxstep.cxx ./src/motifxcommandlinewrapper.cxx -lbiolib -lgsl -lgslcblas -lboost_program_options -lmysqlcppconn -lboost_thread -lboost_system**
```

`-g` allows the debugger to collect debugging information (basically turn it on)

`-I` provides directories for header files

`-o` specifies the name of the output file

`-l` links with library `lib<library>.a`

```makefile
shared_prod:
	g++ -O3 -Wall -std=c++11 -fPIC -I./header -c ./src/*.cxx -lboost_thread -lgsl -lgslcblas -lboost_system
```

`-fPIC` allows for usage as a library b/c the memory addresses aren't fixed ([https://stackoverflow.com/questions/5311515/gcc-fpic-option](https://stackoverflow.com/questions/5311515/gcc-fpic-option))

`-Wall` displays all warnings

`-O3` no idea

Note to self. If working on biolib, make sure you run `install.sh` whenever you make a change or else when you compile motifx-cpp it won't have the updated source/header files

Defining multi-line variable in make:

```makefile
define blah
	yo \\
	yo \\
endef
```

**How to create a static library**

preprocessing:

This is where your .cxx files are linked together with your header files (.h). The `#include` macro tells the preprocessor to include the definitions of the classes from the header files into the .cxx file.

The `-I` flag tells the preprocessor where to locate the include files

The result is an object file (.o)

`g++ -I ./headers/ -c main.cxx`

`g++ -I ./headers/ -c SomeHelper.cxx`

linking (this is when compiling the entire program, not for libraries):

There may be functions that main.o references from SomeHelper.o

Linking allows File1.o to access the declarations and definitions from File2

`g++ main.o SomeHelper.o -o executable`

grouping .o files:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d54f4e9a-f806-46ce-b0b9-1102be0f4260/Untitled.png)

This is where the cpp files are converted into .o files. Afterwards there is the linking stage which puts together object files to create an executable

# Types of assignment
https://stackoverflow.com/questions/4879592/whats-the-difference-between-and-in-makefile
