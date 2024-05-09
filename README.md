# Git/Github Cheat Sheet for For Slow Learners

I selfishly created this cheat sheet for myself after trying to learn git for the _third_ time. You would think that I would have learned my lesson after the first time, however, I prefer to learn lessons the hard and expensive way. I figure that in the future, if I need help remembering what I spent several painstaking hours to learn it would be in my best interest to document my findings. Hopefully, someone else out there finds this useful as well. :metal:

For a more extensive tutorial, a buddy of mine recommended [this one](https://gitimmersion.com/index.html). Let's just say I trust this man with my life so you can at least trust his judgement.

## Setup
First off, make sure that you download git. You can either use git as a standalone package or you may use it in tandem with Bitbucket or Github. Choose your flavor. I favor the Git/Github variety. I am not here to recreate the wheel. A simple search on the web will return hundreds of resources that will walk you through git installation. I use __brew__ to download packages to my machine. Again, the way you do it will be up to you! 

Second, you need to configure your git credentials so you can begin to track changes, . That way, when changes are committed, you can refer to the git log to see the who, when, and what regarding each of the changes.
```
git config --global user.name "full name"
git config --global user.email "email"
git config --global core.excludesfile [file]
```
Make it look pretty :sparkles: The following command will enable the syntax coloring for git
```
git config --global color.ui true
```
If you're using zsh you would like to turn off the default branch listing used by git, enter the following command.
NOTE: If you choose to keep the default branch listing, then you can exit by typing in __-F__ then __return__
```
git config --global pager.branch false
```

## Basics
### git status
Display all modified files in the working directory that are staged for the next commit
```
git status
```
### git log 
This command and all of its variations are useful commands that lets you display information about your branches

Show all commits in the active branch
```
git log
```
Display the commit logs, including any paths that may have been removed
```
git log --stat -M
```

## Get Started
Start using git to start tracking a local repository
```
git init --- start watching a new repo in an already existing directory
git init <directory> --- create git repo in current directory
git clone <GitHub-url> --- clone a repo to your local machine
```
Start working on a copy of your code so you can merge the changes later
```
git branch --- list all branches (* appears next to the current)
git branch -a --- List both remote-tracking branches and local branches. Combine with --list to
           match optional pattern(s)
git branch -r --- List or delete (if used with -d) the remote-tracking branches. Combine with
           --list to match the optional pattern(s)
git branch <branch-name> --- create new branch at the current commit
git checkout <branch-name> --- switch to and create a new branch out of the working directory
git push --set-upstream <alias> <branch-name> --- add that branch to repository
```
### git add 
Allows you to stage the changes that you just made so you update the repo

Add a file to the repo
```
git add <file-name>
```
Add all new files in the current directory to repo
```
git add .
```
Let's commit those changes baby!
```
git commit -m "message goes here" --- commit changes to the branch
```
### git remote
Let's bridge the gap between the local repos and the ones that you have on Github

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
Gives you the power to make the changes that you have made locally available elsewhere

Transmit local branch commits to the remote repository branch
```
git push <alias> <branch>
```
Transmit commits to the current branch
```
git push -u <GitHub-url>
```
### git pull
Keep yourself (and your branch) up to speed and copy the changes

Fetch the specified remote’s copy of current branch and immediately copy it into the local repository
```
git pull <remote>
```
### git fetch
Allows you to check to see if you're up-to-date

Retrieve changes from upstream from the Git remote, without the copying
```
git fetch <alias> --- 
```
Fetches a specific <branch>, from the repo. Leave off <branch>
```
git fetch <remote> <branch>
to fetch all remote refs
```
git merge allows you to combine branches that you were working on

Merge the current branch with the one indicated in the call
```
git merge <branch-name>
```
Merge a remote branch into the active branch to bring it up to date
```
git merge <alias>/<branch-name>
```
### git diff
Compare differences in code that you've made changes to and what has been committed

Display what has been updated but not added
```
git diff
```
Display what is updated but not staged
```
git diff --stages
```
Show difference between working directory and last commit
```
git diff HEAD
```
Show difference between staged changes and last commit
```
git diff --cached
```
Made a mistake? Have no fear, not all hope is lost (yet)
```
git reset <file-name> --- un-stage a file but retain the current changes in the working directory before a commit
git reset --hard [commit]
git revert <commit> --- Create new commit that undoes all of the changes made in <commit>, then apply it to the current branch
git reset <file> --- Remove <file> from the staging area, but leave the working directory unchanged. This unstages a file without overwriting any changes
git clean -n --- Shows which files would be removed from working directory. Use the -f flag in place of the -n flag to execute the clean
```
Do some spring cleaning
```
git rm <file-name> --- delete a file from the project and stage the removal for a commit
git mv <exisitng-path> <new-path> --- change an existing file path and stage the move for a commit
```

## Walkthroughs
So now you know the basics, what the heck can you actually do with all you've just learned? Let me walk you through some common workflows.
### Add a remote
1. create a branch
2. check the current remotes --- git remote -v
3. add a remote --- git remote add <alias> <GitHub-url>
4. get the new remote branches --- git fetch <alias>
5. finalize the remote by pushing the changes --- git push <alias> <url>
  
### Delete remotes
git remote rm <alias>

### Push changes to GH
1. git add [file/s] OR git add . --- add specific files to the repo OR add all of the changes to the repo
2. git commit -m "talk about some shit" --- commit and add a short descriptive message
3. git push <alias> <branch-name>
4. git push -u <alias>
 
## Up Next...
- [ ] add a repository
- [x] add a branch
- [x] merge branches
- [ ] quick tips
- [ ] beginner's checklist
- [ ] helpful videos
- [ ] vocabulary (alias, branch, commit)
- [ ] useful tags

## Questions or Comments?
This is a resource not only for me, but for you! If there is anything else that you think should be in here let me know.

## Level Up :video_game::sparkles:
Once you've mastered the basics of git yourself, you can learn how to transfer the knowledge into your workflow. I highly recommend this [team toolkit](github-teamwork-toolkit) that was created by my friend [@emiton](https://github.com/Emiton).
