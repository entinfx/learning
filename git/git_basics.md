# Basic Git workflow and commands

## Setting up a new repository and local project with GitHub and SSH
1. Generate SSH keypair on your local machine
2. Add your public SSH key to GitHub in settings
3. Create a new repository on GitHub
4. Set up a repository on your local machine:
   $ git init
5. Add a remote (tracking) branch to your local branch:
   $ git remote add origin git@github.com:entinfx/learning.git
6. Stage files and create a new commit on your local branch:
   & git add .
   $ git commit -m "Initial commit."

   or if you need to pull your remote branch in instead:
   $ git pull origin main
7. Sync up your remote branch with the local branch:
   $ git push -u origin main

## Upstream/downstream terminology
Upstream branch 'origin/main'   *---*---*---*---*---*---*---*---*---*---*>
                                |   |   |   |   |   |   |   |   |   |   |
                                |   |   |   |   |   |   |   |   |   |   |
                                |   |   |   |   |   |   |   |   |   |   |
                                |   |   |   |   |   |   |   |   |   |   |
Downstream branch 'origin/main' *---*---*---*---*---*---*---*---*---*---*>

* Downstream - data being pulled from a remote branch to a local one
* Upstream - data being pushed from a local branch to a remote one

## HEAD pointer
A HEAD pointer i

## Common commands
* $ git init - Initialize empty git repository
* $ git status - Check status of your git repository
* $ git add <filename1.ext filename2.ext, .> - Add multiple or all files for
  staging
* $ git commit -m "Commit message." - Create a commit with staged files

* $ git checkout <commit_hash, branch_name> - Checkout a specific commit or
  existing branch
* $ git checkout -b <branch_name> - Create a new branch and checkout
* $ git branch - List all branches
* $ git branch -d <branch_name> - Delete local branch

* git diff - Show changes against last commit
* git log --oneline - Show a log of commits (in one line)

* $ git push -u <remote_name> <branch_name> - Push changes to a remote branch
  (-u sets up current remote branch as upstream branch for argument-less
  'git pull')
* $ git pull <remote_name> <branch_name> - Pull changes from a remote branch
* $ git push -d <remote_name> <branch_name> - Delete remote branch

* $ git config --global user.name "username" - Set git username (shows up as
  commit author name)
* $ git config --global user.email "email" - Set git email
* $ git config --list - List git config information

* $ git reset --HARD~1 - Go back one commit
* $ git revert - Create a new commit undoing changes done by in commit
* TODO: Continue with reverting changes.