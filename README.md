## 📌 Git Notes

---

## ⚙️ Setup & Info Commands (Rarely Used)
```bash
    git --version

    git config --global user.name "Your Name"
    git config --global user.email "you@email.com"
```

## Basic Daily Commands (Most Used)
```bash
    git clone <repository-url>

    git status
    git add .
    git commit -m "Commit message"

    git reset
```

## Branch Management
```bash
    git branch feature # Existing Branch
    git checkout -b feature # Create new and switch
    git branch # List of branchs
    
    git switch feature
    git switch -c feature

    git push origin branch-name

    git fetch # Downloads latest commits from remote & branches
    git pull # fetch + merge or rebase into your current branch

    git branch -d feature # Delete Branch
    git push origin --delete feature # Delete Remote Branch
```

## Stash (Temporary Save)
```bash
    git stash
    git stash push -m "Stash Message"
    git stash list
    git stash apply
    git stash apply stash@{1}
    git stash pop # Apply & Delete stash

    git stash drop stash@{0} # Delete stash
    git stash clear # Clear ALL stashes
    git stash show # Show stash content in terminal
```

## Debugging & History
```bash
    git log
    git log --oneline
    git log -5 # Limit number of commits

    git show <hash> # See what & why
```
