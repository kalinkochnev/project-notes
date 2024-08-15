- `isatty(int filedes)` - tests whether the open file descriptor is associated with a terminal device
- [`read(int fd, void buf[.count], size_t count)`](https://man7.org/linux/man-pages/man2/read.2.html) - attempt to read up to `count` bytes from the `fd` into `buf` 
- `fstat(int fd)` -  gives information about a file in a `stat` structure

- On program startup, the integer file descriptors associated with the streams _stdin_, _stdout_, and _stderr_ are 0, 1, and 2
- preprocessor symbols **STDIN_FILENO**, **STDOUT_FILENO**, and **STDERR_FILENO** are defined with these values in `<unistd.h>`