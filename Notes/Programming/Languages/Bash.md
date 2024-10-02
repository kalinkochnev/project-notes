# `$` character
- Can expand parameters, substitute commands, or expand arithmetic
- Can be defined as `${something_here}` to be less ambiguous
# Export env variables defined in a `.env` file
```bash
set -a
source .env
set +a
```

# `set` command
- **Using a `+` instead of a `-` for an argument will disable that option**
- `set -a` any variable or function that is modified or created past this point is marked for export
- `set +a` any variable or function modified past this point is not marked for export

# `source` command
- source is a synonym for dot/period '.' in bash, but not in POSIX sh, so for maximum compatibility use the period.
- When a script is run using 'source' it runs within the existing shell, 
- any variables created or modified by the script will remain available after the script completes.
- if you run a script without source, then a subshell with completely different env variables is used to execute
## Syntax
```
. filename [arguments]
source filename [arguments]
```

# `trap`
- Creates a handler to run when a shell receives a signal

Example
```bash
trap "echo The .env file was not defined; exit" SIGINT # defines error trap if .env isn't defined
source .env # executes .env script and variables remain after completion
trap '-' SIGINT # resets error trap
```

# Resources
[[Notes/Resources|Resources]]
Advanced Bash-Scripting Guide
A complete guide to shell scripting, using Bash Mendel Cooper - Brindlesoft

This tutorial assumes no previous knowledge of scripting or programming, but
progresses rapidly toward an intermediate/advanced level of instruction
(...all the while sneaking in little snippets of UNIX wisdom and lore). It
serves as a textbook, a manual for self-study, and a reference and source
of knowledge on shell scripting techniques. The exercises and heavily-
commented examples invite active reader participation, under the premise that
the only way to really learn scripting is to write scripts.

The guide is availabe at http://tldp.org/LDP/abs/html/
