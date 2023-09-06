# Clangd
- Is a language server for C++
- Uses `.clangd` files [for configuration](https://clangd.llvm.org/config#compileflags)
- Uses yaml syntax

## Arguments
```yaml
CompileFlags:
  Add: [-I/usr/share/arduino/hardware/arduino/avr/cores/arduino, -I/usr/share/arduino/libraries] // compilation flags (good for includes)
  CompilationDatabase: . // location of compile_commands.json
```

### Issue: Compilation database not found
- This means that clangd does not how your build output is structured
- [Bear](https://github.com/rizsotto/Bear/tree/master) Is a tool that exports a `compile_commands.json` file so clangd can get additional information about your code:w
- Need to specify location of compile_commands.json
- Bear works amazing with nvim and clangd. It now gives me arduino autocompletion!!

### bear usage:
```bash
bear -- <make command>
```