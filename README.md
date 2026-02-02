## 📌 Git Notes

---

## Setup & Info Commands (Rarely Used)
```bash
    git --version
    git clean -fd # Clean Working Tree (Remove untracked files)
    git clone https://username:token@github.com/username/repo.git # Clone using Token
    git remote -v # Shows remote repository URLs is connected
```

## Git Config
```bash
    git config --global user.name "Naimesh Barot"
    git config --global user.email "naimesh.b@email.com"

    git config user.name
    git config user.email

    git config --global --unset credential.helper # REMOVES (deletes) the credential helper setting from Git
    git config --global credential.helper wincred # or --system to ENABLES credential saving on Windows
    git credential reject # Manually tells Git to FORGET stored credentials
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
    git branch feature          # Existing Branch
    git checkout -b feature     # Create new and switch
    git branch                  # List of branchs
    
    git switch feature
    git switch -c feature

    git push origin <branch-name>

    git fetch               # Downloads latest commits from remote & branches
    git pull                # Fetch + Merge or rebase into your current branch
    git pull origin main    # Explicitly pull from remote into current branch

    git branch -d feature                   # Delete Branch
    git push origin --delete feature        # Delete Remote Branch
    git push --set-upstream origin feature  # or -u Push the branch to GitHub & set the default for future pulls and pushes. 

    # Fix last commit message/code
    git commit --amend 
    git commit --amend -m "New correct message"
```

## Stash (Temporary Save)
```bash
    git stash
    git stash push -m "Stash Message"
    git stash list
    git stash apply
    git stash apply stash@{1}
    git stash pop               # Apply & Delete stash

    git stash drop stash@{0}    # Delete stash
    git stash clear             # Clear ALL stashes
    git stash show              # Show stash content in terminal
```

## Cherry-Pick
```bash
    git cherry-pick <commit-hash>   # Single commit
    git cherry-pick <hash1> <hash2> # Cherry-pick multiple commits
    git cherry-pick feature         # Applies latest commit from feature branch
    
    git cherry-pick -n <commit>     # Cherry-pick without committing (Modify code before commit)

    git cherry-pick --abort
    git cherry-pick --skip
```

## Debugging & History
```bash
    git log
    git log --oneline
    git log -5          # Limit number of commits

    git show <hash>     # See what & why
    git reflog          # History of all Git actions

    git blame file.js   # Know who changed a line.
```

## Rarely Used
```bash
    # 🔴 Hard Reset (destructive, deletes changes)
    git reset --hard HEAD~1     # Previous commit in history
    git reset --hard HEAD@{1}   # Recovery command

    # Soft Reset (safe, keeps changes staged)
    git reset —soft HEAD~1
    git reset —soft HEAD@{1}

    # 🟢 Revert (Create a new commit that undoes changes)
    git revert D    # A → B → C → D → D' (D' is a new commit that cancels D)

    # 🟢 Mixed (Commit is undone, All changes remain, Files become unstaged)
    git reset --mixed HEAD~1    # Commits Removed / Staging area Cleared / Working files kept

    # Senario: Message is wrong, Maybe you added extra files
```

## Real Senarios 1
```bash
    git checkout feature-login
    git pull origin feature-login

    git pull

    git pull origin main    # You are on feature-login but want latest from main
```

## Standard for Commit Messages / Naming Standards
```bash
    # Commit Message
    feat: add login API integration 

    # Branch Name Standards
    feature/user-auth 
    fix/cart-total-calculation
    release/v1.2.0
```

## Common Commit Types

**feat:** New feature
**fix:** Bug fix
**docs:** Documentation changes / Storybook
**style:** Formatting (no logic change)
**refactor:** Code improvement without feature change

## Most-useful Commands
```bash
    node -v # Node.js version
    npm -v  # Check npm version

    nvm ls                  # Lists all Node versions installed via NVM
    nvm install 6.9.2       # Installs a specific version using NVM
    nvm use 6.9.1           # Switch active Node version
    nvm alias default 18    # Set version as the default for system

    npm install
    npm update      # Update packages
    npm run dev     # Run script
    npm run build   # Build project

    yarn install
    yarn add axios  # Install package
    yarn dev        # Run dev script
    yarn build      # Build project

    # Cleaning & Fixing (Standard “Reset Project” flow)
    rm -rf node_modules     # Deletes the node_modules folder completely
    rm package-lock.json
    npm cache clean --force

    # Terminal Navigation
    clear       # Clear Terminal
    ls          # List Files
    mkdir test  # Create folder
    rm file.txt # Delete file
    rm -rf dir  # Delete folder forcefully
    cd folder   # Go into folder
    cd ..       # Go back
    cd ~        # Home directory
    cd d:       # Change Drive
    cd u        # Tab to select drive
    pwd         # Show Current Directory
    env         # Show environment variables
    :q          # Quit (only if no changes)
    :wq         # or :x Save the file and exit Vim
    Esc         # Exit insert mode

    # React / Frontend
    npm start
    npm run dev
    npm run build
    
    npx create-react-app myapp
    npm create vite@latest

    # Storybook
    npm run storybook
    npm run build-storybook
    npx storybook upgrade   # Upgrade Storybook
    npx storybook info      # Check Storybook Info
    npm run test-storybook  # Run tests for stories

    # Other Useful Commands
    npm run pretty      # Format code automatically (Prettier)
    npm run format 
    npm run lint        # Run linter (eslint) to check code quality
    npm run clean       # Remove build artifacts (dist, node_modules, etc.)
    npm run typecheck   # Run TypeScript type checking
    npm run deploy      # Deploy project to hosting (Netlify/Vercel etc.)
    npm run test        # Run tests (Jest, RTL, Cypress)
```