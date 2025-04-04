# dont-forget
Reminders for common operations

## CLI

### Oh my ZSH

```
# Is commit in branch history?
function branchContains() {
    if git merge-base --is-ancestor "$1" HEAD; then
        echo "Yes"
    else
        echo "No"
    fi
}

# list files in git by size
function gitlarge() {
  git rev-list --objects --all --missing=print |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort --numeric-sort --key=2 |
  cut -c 1-12,41- |
  $(command -v gnumfmt || echo numfmt) --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
}

# what is listening on my port?
function listening() {
 lsof -i :$1
}

# show directory
function tree(){
  lsd --tree --depth $1
}
```

### Ripgrep

```
# search 'raw', i.e. no escapes or special character effect s
rg -F 'xxxxxxxxxxxx' .
```

### Other tools

- Glow for documentation






