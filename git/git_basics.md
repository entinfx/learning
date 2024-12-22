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

## Initial setup
* `$ git init`- Initialize empty git repository
* `$ git status`- Check status of your git repository
* `$ git add <filename1.ext filename2.ext or .>` - Add file(s) for staging
* `$ git commit -m "Commit message."` - Create a commit with staged files

## Navigate commits and branches
* `$ git checkout <commit_hash or branch_name>` - Checkout a specific commit or
  existing branch
* `$ git checkout -b <branch_name>` - Create a new branch and checkout
* `$ git branch` - List all branches
* `$ git branch -d <branch_name>` - Delete local branch

## HEAD pointer
* HEAD is a pointer to the currently checked out branch that in itself points to
  a specific [usually latest] commit
* There is only 1 HEAD pointer at any given time
* Detached HEAD - Checking out a commit from history puts HEAD in a detached
  state, where it no longer points to the latest commit of the branch, but
  rather to a currently checked out [non-latest] commit
* HEAD\~n is a pointer to the n'th commit from the latest, e.g. HEAD\~1 would
  point to one commit back from latest, HEAD~2 - 2 back and so on

## Logs
* `git diff` - Show changes against last commit
* `git log --oneline` - Show a log of commits (in one line)

## Setting up config info
* `$ git config --global user.name "username"` - Set git username (shows up as
  commit author name)
* `$ git config --global user.email "email"` - Set git email
* `$ git config --list` - List git config information

## Reverting changes
* `$ git reset --HARD~1` - Go back one commit
* `$ git revert` - Create a new commit undoing changes done by in commit
* `$ git restore --staged <filename1.ext filename2.ext or .>` - Unstage file(s)
* `$ git reset <filename1.ext filename2.ext or .>` - Unstage file(s)

## Merging branches
* `$ git merge <branch_to_merge>` - Default merge
  * `$ git merge -ff <branch_to_merge>` - "Fast-forward" merge. Default behavior
  (can omit -ff) if the main branch hasn't been modified. Commits from the
  feature branch are appended to the main branch)
  * `$ git merge --no-ff <branch_to_merge>` - "Non-fast-forward merge". Default
  behavior (can omit --no-ff) if the main branch has been modified. Usually
  requires resolving a merge conflict (see below). After resolving the merge
  conflict:
    1. Commits from the feature branch are inserted into the main branch (after
       the feature branch has been created and before the new changes in the main
       branch)
    2. New commit with merge conflict changes is appended in the end of the main
       branch indicating successful merge
* `$ git merge --squash <branch_to_merge>` - Squash merge. Squash all commits of
  a merging branch into one, and append it to the end of the main branch. May
  require resolving a merge conflict, if so, edit and stage conflicting files.
  Then create a manual merge commit:
  `$ git commit -m "Merge <branch_to_merge> into main"`
* Rebase. If the target branch (e.g. main) is ahead of the merging branch (e.g.
  feature), rebase moves the feature branch forward so that the base of the
  feature branch becomes main branch's latest commit. Flow:
  1. In the feature branch: `$ git rebase main` - Change the base of the feature
     branch to the latest commit of main. May require resolving a conflict.
  2. Edit conflicting files (if any)
  3. `$ git add <conflict_file.ext or .>` - Stage files after fixing
     merge/rebase conflict
  4. `$ git rebase --continue` - Finish rebasing the feature branch
  5. `$ git checkout main` - Navigate back to the main branch
  5. `$ git rebase feature` - Insert feature branch commits after the
     latest common commit of the two branches.

### Resolving merge conflict
1. `$ git merge <branch_to_merge>` - Assume this results in a merge conflict
2. `$ vim <conflict_file.ext>` - Open the conflicting files and choose the
   change that needs to stay
3. `$ git add <conflict_file.ext or .>` - Stage conflicting files for
   merging/committing
4. `$ git merge --continue` - Create a merge commit and add a merge commit
   message

## Working with a remote branch
* `$ git push -u <remote_name> <branch_name>` - Push changes to a remote branch
  (-u sets up current remote branch as upstream branch for argument-less
  'git pull')
* `$ git pull <remote_name> <branch_name>` - Pull changes from a remote branch
* `$ git push -d <remote_name> <branch_name>` - Delete remote branch

## Forks and pull requests
Pull request is a request to have your changes accepted to a public repository.
1. Fork a repository you want to contribute to on GitHub
2. Setup a local repository, and pull down the project from the GitHub fork
3. Create a new branch to work on your feature you want to add
4. Create changes and push them to your GitHub fork
5. Head over to your GitHub fork and press the "Pull request" button
