# Basic Git workflow and commands

## Setting up a new repository and local project with GitHub and SSH
1. Generate SSH keypair on your local machine
2. Add your public SSH key to GitHub in settings
3. Create a new repository on GitHub
4. Set up a repository on your local machine:
   `$ git init`
5. Add a remote (tracking) branch to your local branch:
   `$ git remote add origin git@github.com:entinfx/learning.git`
6. Stage files and create a new commit on your local branch:
   `& git add .`
   `$ git commit -m "Initial commit."`

   or if you need to pull your remote branch in instead:
   `$ git pull origin main`
7. Sync up your remote branch with the local branch:
   `$ git push -u origin main`

## Upstream/downstream terminology
    *---*---*---*---*---*---*---*---*---*---*> - upstream branch 'origin/main'
    |   |   |   |   |   |   |   |   |   |   |
    |   |   |   |   |   |   |   |   |   |   |
    |   |   |   |   |   |   |   |   |   |   |
    |   |   |   |   |   |   |   |   |   |   |
    *---*---*---*---*---*---*---*---*---*---*> - downstream branch 'origin/main'

* Downstream - data being pulled from a remote branch to a local one
* Upstream - data being pushed from a local branch to a remote one

## HEAD pointer
A HEAD pointer i

## Common commands
### Initial setup
* `$ git init`- Initialize empty git repository
* `$ git status`- Check status of your git repository
* `$ git add <filename1.ext filename2.ext or .>` - Add file(s) for staging
* `$ git commit -m "Commit message."` - Create a commit with staged files

### Navigate commits and branches
* `$ git checkout <commit_hash or branch_name>` - Checkout a specific commit or
  existing branch
* `$ git checkout -b <branch_name>` - Create a new branch and checkout
* `$ git branch` - List all branches
* `$ git branch -d <branch_name>` - Delete local branch

### Logs
* `git diff` - Show changes against last commit
* `git log --oneline` - Show a log of commits (in one line)

### Working with a remote branch
* `$ git push -u <remote_name> <branch_name>` - Push changes to a remote branch
  (-u sets up current remote branch as upstream branch for argument-less
  'git pull')
* `$ git pull <remote_name> <branch_name>` - Pull changes from a remote branch
* `$ git push -d <remote_name> <branch_name>` - Delete remote branch

### Setting up config info
* `$ git config --global user.name "username"` - Set git username (shows up as
  commit author name)
* `$ git config --global user.email "email"` - Set git email
* `$ git config --list` - List git config information

### Reverting changes
* `$ git reset --HARD~1` - Go back one commit
* `$ git revert` - Create a new commit undoing changes done by in commit
* `$ git restore --staged <filename1.ext filename2.ext or .>` - Unstage file(s)
* `$ git reset <filename1.ext filename2.ext or .>` - Unstage file(s)

### Merging branches
* `$ git merge -ff <branch_to_merge>` - "Fast-forward" merge. Default behavior
  (can omit -ff) if the main branch hasn't been modified. Commits from the
  feature branch are appended to the main branch)
* `$ git merge --no-ff <branch_to_merge>` - "Non-fast-forward merge". Default
  behavior (can omit --no-ff) if the main branch has been modified. Usually
  requires solving a merge conflict. Commits from the feature branch are
  appended to the main branch) and a new commit with merge conflict changes is
  created on the main branch indicating successful merge
