https://github.com/iggredible/Learn-Vim/tree/master
cheatsheet: https://docs.google.com/spreadsheets/d/19l4rQdYZfqpMtdTjvCrYLF2z9OsAqahhPunnw7I831s/edit#gid=1082709605

# Navigation

| Keybind                    | Mode     | Action                                                     |
| -------------------------- | -------- | ---------------------------------------------------------- |
| `<h>`, `<j>`, `<k>`, `<l>` | normal   | left, down, up, right                                      |
| `<w>`, `<b>`               | normal   | Start of next word, start of previous word                 |
| `<}>`                      | normal   | Next paragraph                                             |
| `$`                        | normal   | Move to end of line                                        |
| `^`                        | normal   | Move to start of line                                      |
| `+`                        | normal   | Next line                                                  |
| `:Ex`                      | normal   | Open Netrw file explorer                                   |
| `%`                        | Netrw    | New file                                                   |
| `d`                        | Netrw    | New directory                                              |
| `Ctrl+\,Ctrl+n`            | terminal | exit terminal                                              |
| `G`                        | normal   | go to last line                                            |
| `gg`                       | normal   | go to first line                                           |
| `nG`                       | normal   | go to line **n**                                           |
| `Ctrl-W` + (h,j,k,l)       | normal   | navigate between windows                                   |
| `Ctrl-F/Ctrl-B`            | normal   | scroll down/up a whole screen                              |
| `Ctrl-D/Ctrl-U`            | normal   | scroll down/up half a screen                               |
| `Ctrl-E/Ctrl-Y`            | normal   | scroll down/up a line                                      |
| `n`/`N`                    | normal   | After completing a search, go to next/previous occurrences |
| `<n>gt/<n>gT`              | normal   | go to tab n                                                |
|                            |          |                                                            |
## Grammar
- Noun (motion like `h`, `w`, etc) + verb (`y`, `d`, `c`)
- accepts arguments
- linewise operators are done with repeated verb (yy, dd, cc)
### examples:
`y$` - yank from here to EOL
`dw` - delete up to next word
`y2h` - yank two characters to the left
`c2j` - change next two lines
``


## Netrw
`%` new file
`d` new directory

| Keybind | Mode  | Action   |
| ------- | ----- | -------- |

## Comment block
https://stackoverflow.com/a/1676690/10521417

 1. First, go to the first line you want to comment, press <kbd>Ctrl</kbd><kbd>V</kbd>. This will put the editor in the `VISUAL BLOCK` mode.
 2. Then using the arrow key and select until the last line
 3. Now press <kbd>Shift</kbd><kbd>I</kbd>, which will put the editor in `INSERT` mode and then press <kbd>#</kbd>. This will add a hash to the first line. 
 4. Then press <kbd>Esc</kbd> (give it a second), and it will insert a `#` character on all other selected lines. 

For the stripped-down version of vim shipped with debian/ubuntu by default, type `: s/^/#` in the third step instead (any remaining highlighting of the first character of each line can be removed with `:nohl`).

## Uncomment
1. `Ctrl-V`
2. Select
3. press `x` to delete a single character



# Buffers

| Keybind                | Mode   | Action                                                                                                 |     |
| ---------------------- | ------ | ------------------------------------------------------------------------------------------------------ | --- |
| `:tabclose` or `:bd`   | normal | close the current buffer                                                                               |     |
| `:%bd|e#`              | normal | close all buffers                                                                                      |     |
| `:terminal`            | normal | opens new terminal                                                                                     |     |
| `y`                    | visual | yank/copy                                                                                              |     |
| `d`                    | visual | delete text, save to register                                                                          |     |
| `c`                    | visual | delete text, save to register, start insert mode                                                       |     |
| `u`                    | normal | undo                                                                                                   |     |
| `<C-r>`                | normal | redo                                                                                                   |     |
| `:za`                  | normal | toggles fold at cursor ([more here](https://stackoverflow.com/questions/2362914/fold-function-in-vim)) |     |
| Selection + `=`        | visual | Autoformat                                                                                             |     |
| `ni`                   | normal | Enter insert mode (or any alternative insert cmd) and repeat input **n** times                         |     |
| `o`                    | normal | Insert a line below and insert text                                                                    |     |
| `O`                    | normal | Insert a line above and insert text                                                                    |     |
| a                      | normal | append text after the cursor                                                                           |     |
| A                      | normal | append text at the end of the line                                                                     |     |
| `:split` / `Ctrl-W S`  | normal | Splits the window into a top and a bottom buffer                                                       |     |
| `:vsplit` / `Ctrl-W V` | normal | Splits window into left and right buffer                                                               |     |
| `Ctrl-W C`             | normal | close a window                                                                                         |     |
| `Ctrl-W O`             | normal | close all other windows except the one on screen                                                                                                       |     |
# Configuration
## Saving nvim session
`:mksession <path>/mysession.vim`
Open session `nvim -S <path>/mysession.vim`

## Nvim config location
~/.config/nvim/init.vim

## Runtime path variables
`:h rtp`

## Source a file
`:so`

# Files

| Keybind | Mode | Action     |
| ------- | ---- | ---------- |
| `:q`    | cmd  | quit       |
| `:q!`   | cmd  | force quit |
| `:w`    | cmd  | save file  |
| `:e`    | cmd  | edit file  |
| `:v`    | cmd  | view only           |

# Bindings
## Remapping
`vim.keymap.set("n", "<leader>pv", vim.cmd.Ex)` 
While in normal mode "n", set "< leaderpv>" to the command ":Ex"

| Keybind       | Action                                     |
| ------------- | ------------------------------------------ |
| `< leader>`   | space                                      |
| `< leader>pv` | netrw                                      |
| `< leader>pf` | fuzzy search project files                 |
| `< leader>ps` | find in file                               |
| `<C-p>`       | find in git repo                           |
| `< leader>u`  | View undo tree for file                    |
| `<` leader>a  | Harpoon add file                           |
| `dd`          | While in harpoon menu, delete from harpoon |
| `<C-e>`       | Toggle harpoon menu                        |
| `<C-h>`       | harpoon file 1                             |
| `<C-t>`       | harpoon file 2                             |
| `<C-n>`       | harpoon file 3                             |
| `<C-s>`       | harpoon file 4                             |
| `< leader>gs` | Open git menu                              |
| J/K           | slide selection up/down                                      |


# Packages
Using **Packer.nvim** package manager
`:PackerSync` checks for package updates

## Process
1. Add a new plugin to `nvim/lua/kalinkochnev/packer.lua`
2. Configure the plugin by creating a new file `nvim/plugin/after/<plugin nickname>.lua` and specifying settings there

## Translate from Plug to Packer.nvim
Example:
`Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}` 
to
`use({'nvim-treesitter/nvim-treesitter', { run = ':TSUpdate '})`

# Macros
Start recording macro in register a `qa`
End macro recording `q`
Execute macro in register a `@a`
Repeat last macro `@@`
Repeat macro in register a, n times `n@a`

# Miscellaneous
## Language server list
https://microsoft.github.io/language-server-protocol/implementors/servers/

# LSP

| Keybind        | Mode   | Action                                 |
| -------------- | ------ | -------------------------------------- |
| `<C-p>`        | insert | Next item in autocomplete              |
| `<C-n>`        | insert | Previous item in autocomplete          |
| `<C-y>`        | insert | Confirm autocomplete                   |
| `<C-Space>`    | insert | Invoke completion menu                 |
| `< leader>vrn` | normal | rename                                 |
| `< leader>vrr` | normal | references                             |
| `<C-h>`        | insert | signature help                         |
| `< leader>vca` | normal | code action                            |
| `[d`/`]d`      | normal | go to next/prev in diagnostic/warnings |
| `K`            | normal | Hover/show docs                        |
| `gd`           | normal | show definition                                       |

# Git

| Keybind     | Mode   | Actjion                              |
| ----------- | ------ | ------------------------------------ |
| `=`         | menu   | See the diff of the file             |
| `a`         | menu   | stage file                           |
| `cc`        | menu   | create a new commit                  |
| `r`         | menu   | refresh                              |
| `:Git push` | normal | push the commits                     |
| `X`         | normal | discards the change/file             |
| `gI`        | normal | adds file under cursor to git ignore |
| :            |        |                                      |

# Search and replace

| Keybind                                     | Mode   | Action     |
| ------------------------------------------- | ------ | ---------- |
| `:s/<regex>/<replace with>/<flags> [count]` | normal | Substitute |
| `:g/<regex>/`                               | normal | Search     |
|                                             |        |            |

`%` - look for all occurences in the file
`\v` - very magic mode (basically regular regex). Otherwise any regex characters must be escaped with `\` which is annoying
`\0` - first capture group (or entire line if a selection)
`\1 \2 \3 ...` - other capture groups
`&` when replacing represents the selection found so you can append/prepend
`\r` is a carriage return

## Replace markdown images with
Regex to find `![[ link.png ]]` is `!\[\[([^\]]*)\]\]`
`:%s/\v!\[\[([^\]]*)\]\]/{{<figure src="\1" alt="">}}/g`

# Lists of plugins
https://github.com/rockerBOO/awesome-neovim