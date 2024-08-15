Rsync with ssh
```bash
Local to Remote: rsync [OPTION]... -e ssh [SRC]... [USER@]HOST:DEST
Remote to Local: rsync [OPTION]... -e ssh [USER@]HOST:SRC... [DEST]
```

## options
https://linuxize.com/post/how-to-transfer-files-with-rsync-over-ssh/
`-a`  "archive mode" - sync dirs recursively, also transfers permissions, symbolic links, etc
`-v` verbose
`-z` compress
`-exclude-from` path of file that contains directories to exclude
# Sync files/folder from local to host
```
rsync -avz -e ssh /src/ user@remote:/path/to/dst
```
