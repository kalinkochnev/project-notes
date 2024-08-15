## Including spaces in a file path
```bash
cd "/path/path/path/A Folder/file"
cd '/path/path/path/A Folder/file'
cd /path/path/path/A\ Folder/file
```

# Linux Access Control List (ACL)
https://www.redhat.com/sysadmin/linux-access-control-lists

### List permissions  in tree format
Install `tree` on apt and run `tree -p`
```
[drwxrwxr-x]  .
├── [drwxrwxr-x]  archetypes
│   ├── [-rw-rw-r--]  blog.md
│   ├── [-rw-rw-r--]  default.md
│   ├── [-rw-rw-r--]  journeylog.md
│   └── [-rw-rw-r--]  journey.md
├── [drwxrwxr-x]  assets
│   └── [drwxrwxr-x]  scss
│       ├── [-rw-rw-r--]  blog.scss
│       ├── [-rw-rw-r--]  _common.scss
│       ├── [-rw-rw-r--]  content.scss
```

### List permissions of file
`ls -l <file>`


## Interpreting file permissions
```
-rw-r--r-- 12 linuxize users 12.0K Apr  8 20:51 filename.txt
|[-][-][-]-   [------] [---]
user             |       |
    owner        |       +-----------> Group
       other     +-------------------> Owner
```
- First character (-) in this case indicates a file. Otherwise it is an `l` if a folder
- r=read, w=write, x=execute
- 666 represents binary strings for which permission are enabled for user, owner, other
	- Ex: $6_{2}=110=\text{read,  write, no exec}$ for user

## Default permissions
- Default for newly created folders is `775` and for files `664`

## Applying default permissions
https://unix.stackexchange.com/a/1315/549867
1. Set gid bit so any files created under folder will be a part of same group
````bash
chmod g+s <directory>
````
2. Set default ACLs (-d default switch) and -m only changes the default permissions (doesn't affect files that already exist in dir)
```bash
setfacl -d -m g::rwx /<directory>
setfacl -d -m o::rx /<directory>
```
3. If want to apply permissions to files if they already exist too use -R to make it recursive
````bash
setfacl -R -m g::rwx /<directory>
````

## Revoking privileges
`sudo setfacl -d -m g::--- /path`

## Change owner of file
`chown USER FILE`


# Create a symlink
https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/
```shell
ln -s <path to the file/folder to be linked> <the path of the link to be created>
```

# Program executable from anywhere
https://unix.stackexchange.com/questions/3809/how-can-i-make-a-program-executable-from-everywhere
1. Store the program in /usr/local/bin

- Add to path in ~/.bashrc
`export PATH=$PATH:</path/to/file>`

# Change default terminal
https://askubuntu.com/questions/1157503/deepin-terminal-not-showing-up-in-x-terminal-emulator-list

# XARGS
`xargs <cmd>` command run a specified command by passing in arguments to `<cmd>` from stdin input

# UI is wrong resolution?
Install the pop-os nvidia drivers
```
sudo apt install system76-driver-nvidia
```
https://support.system76.com/articles/install-pop/

# App Image Installation
https://askubuntu.com/a/1428457
1. Create a .desktop file with the following contents
```
[Desktop Entry]
Name=Fancy App
Comment=Does this and that
Exec=/home/username/path/to/the/fancy_app.appimage
Icon=/home/username/path/to/the/app-logo.png
Terminal=false
Type=Application
Categories=Something;
Keywords=something;more;
```
2. Store the .desktop file under `/home/username/.local/share/applications/`
3. Create a new folder under the home directory called `Applications/` and move the `.AppImage` file there
4. The Icon can be stored under `/home/username/.local/share/icons/hicolor/` and find the appropriate directory based on image size (svgs are supported)

# See what ports are in use
```
sudo netstat -tunlp
```
- `-t` show tcp
- `-u` show udp
- `-n` show numerical addresses instead of resolving hosts
- `-l` show only listening prots
- `-p` show the PID/name of the process