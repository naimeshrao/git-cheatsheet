# 📌 Git Commands Cheat Sheet for Developers

## 👉 Git Setup & Information Commands
```bash
    git --version
    git clean -fd # Clean Working Tree (Remove untracked files)
    git clone https://username:token@github.com/username/repo.git # Clone using Token
    git remote -v # Shows remote repository URLs is connected
```

## 👉 Git Configuration Commands
```bash
    git config --global user.name "Naimesh Barot"
    git config --global user.email "naimesh.b@email.com"

    git config user.name
    git config user.email

    git config --global --unset credential.helper # Removes saved Git cred helper
    git config --global credential.helper wincred # Enables cred saving on Windows (--system)
    git credential reject # Manually tells Git to FORGET stored creds
```

## 👉 Most Used Daily Git Commands
```bash
    git clone <repository-url>

    git status
    git add .
    git commit -m "Commit message"

    git reset
```

## 👉 Git Branch Management Commands
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
    git push --set-upstream origin feature  # or -u Push to GitHub and set as default upstream. 

    # Fix last commit message/code
    git commit --amend 
    git commit --amend -m "New correct message"
```

## 👉 Git Stash – Save Work Temporarily
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

## 👉 Git Cherry-Pick Commands
```bash
    git cherry-pick <commit-hash>   # Single commit
    git cherry-pick <hash1> <hash2> # Cherry-pick multiple commits
    git cherry-pick feature         # Applies latest commit from feature branch
    
    git cherry-pick -n <commit>     # Cherry-pick without committing (Modify code before commit)

    git cherry-pick --abort
    git cherry-pick --skip
```

## 👉 Git Debugging & History Commands
```bash
    git log
    git log --oneline
    git log -5          # Limit number of commits

    git show <hash>     # See what & why
    git reflog          # History of all Git actions

    git blame file.js   # Know who changed a line.
```

## 👉 Git Reset, Revert & Recovery
```bash
    # 🔴 Hard Reset (destructive, deletes changes)
    git reset --hard HEAD~1     # Previous commit in history
    git reset --hard HEAD@{1}   # Recovery command

    # Soft Reset (safe, keeps changes staged)
    git reset —soft HEAD~1
    git reset —soft HEAD@{1}

    # 🟢 Revert (Create a new commit that undoes changes)
    git revert D    # A → ... → D → D' (D' is a new commit that cancels D)

    # 🟢 Mixed (Commit is undone, All changes remain, Files become unstaged)
    git reset --mixed HEAD~1    # Commits Removed / Staging Cleared / Kept files 

    # Senario: Message is wrong, Maybe you added extra files
```

## 👉 Git Commit Message Standards
```bash
    # Commit Message
    feat: add login API integration 

    # Branch Name Standards
    feature/user-auth 
    fix/cart-total-calculation
    release/v1.2.0
```

## 👉 Most Useful Development Commands
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
    ls -la      # Shows detailed list of all files
    ls -l       # Simple List
```

## 📝 Commit Message Standards

- **feat:**     New feature
- **fix:**      Bug fix
- **docs:**     Documentation changes / Storybook
- **style:**    Formatting (no logic change)
- **refactor:** Code improvement without feature change


## 🎲 Scenario 1 – Working on a Feature Branch
```bash
    git checkout feature-login
    git pull origin feature-login

    git pull

    git pull origin main    # You are on feature-login but want latest from main
```

## 🎲 Scenario 2 – Multiple Commits & PR Workflow
```bash
    git checkout main
    git pull origin main
    git checkout -b feature/profile

    git commit -m "feat: create profile UI"
    git commit -m "feat: integrate profile API"
    git commit -m "fix: validation issue"

    # Keep Branch Updated With Main
    git checkout main
    git pull origin main
    git checkout feature/profile
    git merge main

    # Resolve conflicts if any
    git commit -m "fix: resolve merge conflicts"

    # Push Feature Branch
    git push origin feature/profile

    # Create PR -> Code Review -> Final Merge to Main
```

## 🎲 Scenario 3 – Busy Project Merge Flow
```bash
    git checkout main
    git pull
    git checkout -b feature/login

    # DURING DAY (REPEAT):
    git commit ...
    git checkout main
    git pull
    git checkout feature/login
    git merge main
    git push

    # END OF DAY:
    git checkout main
    git pull
    git checkout feature
    git merge main
    git push

    # Create PR -> Code Review -> Final Merge to Main
```

## 🎲 Scenario 4 – Rebase Workflow (Professional Teams)
```bash
    git checkout main
    git pull origin main
    git checkout -b feature/your-task

    # DURING DAY:
    git add .
    git commit -m "..."
    git checkout main
    git pull origin main
    git checkout feature/your-task
    git rebase main
    git push origin feature/your-task --force-with-lease

    # END OF DAY:
    git checkout main
    git pull origin main
    git checkout feature/your-task
    git rebase main
    git push origin feature/your-task --force-with-lease

    ## Create PR -> Code Review -> Final Merge to Main

    # If conflicts occur → fix them →
    git add .
    git rebase --continue
    git push origin feature/your-task --force-with-lease

    git rebase --abort # If something goes wrong →
```