# Basic Git workflow

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

## Common commands
*