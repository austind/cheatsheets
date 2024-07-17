# Git Cheat Sheet

[GitHub Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

### Sync remote branch to local branch (destructive)

```sh
git fetch origin
git reset --hard origin/{branch}
```

### Delete branch

```sh
# Local
git branch --delete {local-branch}
# Remote
git push origin --delete {remote-branch}
```