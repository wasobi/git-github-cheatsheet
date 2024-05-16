# Git/Github Cheat Sheet for For Slow Learners

I selfishly created this cheat sheet for myself after trying to learn git for the _third_ time. You would think that I would have learned my lesson after the first time, however, I prefer to learn lessons the hard and expensive way. I figure that in the future, if I need help remembering what I spent several painstaking hours to learn it would be in my best interest to document my findings. Hopefully, someone else out there finds this useful as well. :metal:

For a more extensive tutorial, a buddy of mine recommended [this one](https://gitimmersion.com/index.html). Let's just say I trust this man with my life so you can at least trust his judgement.

## Setup
__1. Download git and choose your version control software.__
First off, make sure that you download Git. You can either use git as a standalone package or you may use it in tandem with Bitbucket or Github. Choose your flavor. I favor the Git/Github variety. I am not here to recreate the wheel. A simple search on the web will return hundreds of resources that will walk you through git installation. I use __brew__ to download packages to my machine. Again, the way you do it will be up to you! 

__2. Configure Git to Track Your Changes.__
Second, you need to configure your git credentials so you can begin to track changes, . That way, when changes are committed, you can refer to the git log to see the who, when, and what regarding each of the changes.

```
git config --global user.name "full name"
git config --global user.email "email"
git config --global core.excludesfile [file]
```
__3. Add some pizzaz (optional but worth it).__
Make it look pretty :sparkles: The following command will enable the syntax coloring for git
```
git config --global color.ui true
```
If you're using zsh you would like to turn off the default branch listing used by git, enter the following command.
NOTE: If you choose to keep the default branch listing, then you can exit by typing in `-F` then `return`
```
git config --global pager.branch false
```
## Get Started
### git init
_Start using git to start tracking a local repository and connect it to a remote repository in the future._

Start watching a new repo in an already existing directory
NOTE: Execute this command once you have used `cd` to navigate into the directory.
```
git init
```
Create git repo in current directory
```
git init <directory>
```
### git clone
_Clone a repo to your local machine._
```
git clone <GitHub-url> --- clone a repo to your local machine
```
### git status
_Display all modified files in the working directory that are staged for the next commit._
```
git status
```
### git branch
_Start working on a copy of your code so you can merge the changes later._

List all branches (__*__ appears next to the current)
```
git branch
```
List both remote-tracking branches and local branches
NOTE: You can combine with `--list` to match optional pattern(s)
```
git branch -a
```
List or delete (if used with `-d`) the remote-tracking branches. Combine with the flag `--list` to match the optional pattern(s)
```
git branch -r
```
Create a new branch at the current commit
```
git branch <branch-name>
```
### git checkout
_Switch to and create a new branch out of the working directory._
```
git checkout <branch-name> 
```
### git add 
_Allows you to stage the changes that you just made so you update the repo._

Add a file to the repo
```
git add <file-name>
```
Add all new files in the current directory to repo
```
git add .
```
### git commit
_Let's save those changes baby!_

Commit changes to the branch
```
git commit -m "message goes here" 
```
### git remote
_Let's bridge the gap between the local repos and the ones that you have on Github._

Display all of the git remotes for the repo
```
git remote
```
Display the status of all remotes for the repo
```
git remote -v
```
Add an alias to a remote repository
```
git remote add <alias> <GitHub-url>
```
A list of branches associated with the remote and also the endpoints attached for fetching and pushing
```
git remote show <alias>
```
Remove the connection to the remote repository called
```
git remote rename <old-name> <new-name>
```
Changes the list of branches tracked by the named remote
```
git remote set-branches --add <name> <branch>
```
### git push
_Gives you the power to make the changes that you have made locally available elsewhere._
Transmit commits to the current branch
```
git push -u <GitHub-url>
```
Add a new branch created locally to the remote repository
```
git push --set-upstream <alias> <branch-name> 
```
Now, you can use `git push` to send those changes to the remote
```
git push <alias> <branch>
```
### git pull
_Keep yourself (and your branch) up to speed and copy the changes._

Fetch the specified remote’s copy of the current branch and immediately copy it into the local repository
```
git pull <remote>
```
### git fetch
_Allows you to check to see if you're up-to-date._

Retrieve changes from upstream from the Git remote, without the copying
```
git fetch <alias> --- 
```
Fetches a specific `<branch>`, from the repo. Leave off <branch>
```
git fetch <remote> <branch>
```
### git merge
_Allows you to combine branches that you were working on._

Merge the current branch with the one indicated in the call
```
git merge <branch-name>
```
Merge a remote branch into the active branch to bring it up to date
```
git merge <alias>/<branch-name>
```
### git diff
_Compare differences in code that you've made changes to and what has been committed._

Display what has been updated but not added
```
git diff
```
Display what is updated but not staged
```
git diff --stages
```
Show the difference between the working directory and the last commit
```
git diff HEAD
```
Show the difference between staged changes and the last commit
```
git diff --cached
```
## Fixing Mistakes
Made a mistake? Have no fear; not all hope is lost (yet). The beauty of version control is that you can track all of your past versions and retrieve lines of code or entire files. This can get really advanced, really fast. I suggest fixing your mistakes under the guidance and supervision of someone else who knows their way around git. I'm speaking from experience and guaranteeing it will save you 50 hours of headaches.
### git rm and git mv
_Do some spring cleaning and get rid of some files or move them around then commit them. Using this method, you can change the file structure or delete things from your project with the safety net of being able to roll back your changes with git._

Delete a file from the project
```
git rm <file-name> ---  and stage the removal for a commit
```
Change an existing file path
```
git mv <exisitng-path> <new-path> ---  and stage the move for a commit
```
### git log 
_This command and all of its variations are useful commands that let you display information about your branches._

Show all commits in the active branch
```
git log
```
Display the commit logs, including any paths that may have been removed
```
git log --stat -M
```
### git reset
_Rollback your changes to a previous version of your work._
Un-stage a file but retain the current changes in the working directory before a commit
```
git reset <file-name>
```
Reset a branch using a previous commit ID (find this using `git reflog`)
```
git reset --hard [commit]
```
Create a new commit that undoes all of the changes made in <commit>, then apply it to the current branch
```
git revert <commit>
```
Remove <file> from the staging area, but leave the working directory unchanged
NOTE: This unstages a file without overwriting any changes
```
git reset <file>
```
### git clean
_Shows which files would be removed from the working directory._
NOTE: Use the `-f` flag in place of the `-n` flag to execute the clean
```
# Run a test run
git clean -n

# Run the clean
git clean -f
```
## Common Workflows
So now you know the basics, what the heck can you actually do with all you've just learned? Let me walk you through some common workflows.
### Add a remote
1. create a branch --- `git branch <new-branch-name>`
2. check the current remotes --- `git remote -v`
3. add a remote --- `git remote add <alias> <GitHub-url>`
4. get the new remote branches --- `git fetch <alias>`
5. finalize the remote by pushing the changes --- `git push <alias> <Github-url>`
  
### Delete remotes
`git remote rm <alias>` 

### Push changes to GH
1. add specific files to the repo OR add all of the changes to the repo --- `git add [file/s]` OR `git add .`
2. commit and add a short descriptive message --- `git commit -m "talk about some ~~shit~~"`
3. send the changes from your local repo to the remote --- `git push <alias> <branch-name>` or `git push -u <alias>`
 
## Up Next...
- [ ] Workflow: add a repository
- [x] add a branch
- [x] merge branches
- [x] quick tips
- [ ] helpful videos
- [ ] vocabulary (alias, branch, commit, remote, local, repo)
- [ ] useful tags

## Questions or Comments?
This is a resource not only for me, but for you! If there is anything else that you think should be in here let me know. Feel free to raise an issue.

## Level Up :video_game::sparkles:
Once you've mastered the basics of git yourself, you can learn how to transfer the knowledge into your workflow. I highly recommend this [team toolkit](github-teamwork-toolkit) that was created by my friend [@emiton](https://github.com/Emiton).
