# Git
## 1. Setting Up
```shell
mkdir project
cd project

git init # this initiate .git folder
git config user.name "asa"
git config user.email "devaksa001@gmail.com"

git status # this will show unstaged, staged, and modified file
git add . # this will add all files to staging
git commit -m "start tech rebuild log" 
```
## 2. Connect local to github
**Sources**: [Github Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
### With gh
```shell
gh auth login
```
### Without gh
```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

```powershell
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
ssh-add c:/Users/YOU/.ssh/id_ed25519
```

Then:
1. Create repo first in GitHub
2. In your project local dir:
```shell
   git remote add origin <your repo .git url>
   git branch -M main
```
3. then just add, commit, and push (a)
4. to push:
```shell
   git push -u origin main
```

## 3. Basic git commands
1. git push -u origin main: send local commit to origin (remote).
2. git branch: list branch, use -d to delete branch
3. git switch: switch branch, use -c to create new branch
4. git merge: merge two branch, but first switch to the main branch

# HOW TOs:
## 1. Check current branch
`git branch`
## 2. Create & Switch branch
to create:
`git switch -c \<branch\>`
to only switch:
`git switch \<branch\>`
## 3. To develop in other new branch then merge
```shell
git pull #check latest commits
git switch -c new_branch
git branch --show-current
# Modify files from here, then:
git add .
git commit -m "feature: new features"
git switch main
# STOP here if you dont wanna merge, otherwise:
git merge new_branch
git push
```

## 4. Restoring / fallback
### a. Specific file from last commit
`git restore something.smth`
### b. Discard all uncommited changes (back to last commit)
`git restore .`
### c. Discard all including untracked files (back to last commit)
`git clean -fdn`
### d. Go back to last commit immediately
`git reset --hard HEAD`
### e. Delete last commit but keep changes
`git reset --soft HEAD~1`
### f. Delete last commit WITH the changes
`git reset --hard HEAD~1`
### g. Amend last commit message
`git commit --amend -m "new message"`
### h. Delete first and only commit without reverting changes
`git update-ref -d HEAD`

## COMMIT MESSAGES:

| Type       | Meaning                                          |
| ---------- | ------------------------------------------------ |
| `feat`     | New feature                                      |
| `fix`      | Bug fix                                          |
| `docs`     | Documentation only                               |
| `style`    | Formatting, whitespace, linting; no logic change |
| `refactor` | Code restructuring without changing behavior     |
| `test`     | Add or update tests                              |
| `chore`    | Maintenance/config/tooling                       |
| `perf`     | Performance improvement                          |
| `build`    | Build system/dependency changes                  |
| `ci`       | CI/CD config changes                             |
| `revert`   | Revert previous commit                           |
Use present tense / imperative mood, be direct, and commit every meaningful step.

## TROUBLESHOOT:
#### 1. Fix CRLF warning in win11
```shell
git config --global core.autocrlf input
echo * text=auto eol=lf > .gitattributes
git add --renormalize .
git commit -m "normalize line endings"
git push
```

# NOTES:
**Origin**: is a convention usually used to name remote address
so:
```shell
# instead of
git push -u https://github.com/devaksa01/aksyarat.git main

# U can just use:
# this will make origin=<url> 
git remote add origin https://github.com/devaksa01/aksyarat.git
# then do the same thing but using origin
git push -u origin main 
```
**Stages** in git: Working dir -> Staging -> Commit -> GitHub
