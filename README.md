# git_commands

partly inspired from https://github.com/yaseenhasan786/gitCommands
In this doc, we assume there are to repos, one is 'local' which means the device where you treat as 'orgin', the other is 'remote' which means the device where you might use the docs same as 'local' and could do some changes. Our aims are:
(1) When 'local' changed, push it to the 'remote'.
(2) When 'remote' is changed, make 'local' be same as 'remote'.
### Creating a repository in local repository
``` sh
# 
# navigated into your folder you want to put on Github
$ touch README.md								# create a file called README.md where you can put instructions/info about your folder like what you are reading right now!
$ git init 										# initialize your git repository locally
$ git add .										# adds everything changed from local to staging
$ git commit -m "first commit"					# commits everything in staging to be ready to be pushed to Github. "-m": message
$ ?git remote add origin https://github.com/quinnliu/GitCommands.git
$ ?git push -u origin master						# the "-u" is so that the next time your push you don't need to type "origin master"
# put in a username & password
```
### Manipulating remote repository
``` sh
$ rm -rf .git # remove git tracking
```
### Manipulating local repository
``` sh
$ cd path/to/working/repository(directory)
$ git status # check current status
$ git add filename
$ git add . # add all files
$ git commit -m "message to describe current commit"
$ git commit -am "message" # PERFECT short-cut to execute the two commands with one command. "-a": all.
$ git commit -a -m "message" # short-cut to execute the two commands with one command.
$ git add . && git commit -m "message" # short-cut to combine the two commands in one command
$ git add-commit -m 'message' # same as above
$ git push origin master # update everything from local to online. use "git push -u origin master" at first time as stated above. 
$ git log # check all commits history.
$ git diff @^ # @ is alias for HEAD, so this is compare last one to current status
$ git diff HEAD^ # compare last one to  current status
$ git diff commit_id # compare commit_id to current status
$ git diff commit_id1 commit_id2 # compare commit_id1 to commit_id2
$ git diff commit_id1 -- the/file/path commit_id2 -- the/file/path # compare file changes between commit_id1 and commit_id2

first "git commit -m ..." on remote
$ git fetch –all 
$ git reset --hard origin/master

```
$ git wdiff # check difference btw word docs. need to [set up](https://github.com/vigente/gerardus) at first time.


### When adding on to your repository online with changes
``` sh
$ git add .										# adds everything changed from local to staging
$ git add file-name-1.php file-name-2.js file-name-3.html …		# add multiple files	
$ git add -u									# when you have deleted a local file you want to remove from your repository
$ git commit -m 'what has changed'				# -m, add message.
$ git push 
# put in username & password
```

### No more username & password input for every push
``` sh   
# Note that you must first generate a SSH key on your local computer and add it to your 
# Github account before using the following command. Follow the directions here:
# https://help.github.com/articles/generating-ssh-keys
$ git remote set-url origin git@github.com:yourUsername/yourReponame.git
```

### Working together from perspective of person that doesn't have the main repo
``` sh
# fork repo you want to work on
$ git clone https://github.com/yourUsername/yourReponame.git
$ git clone git@github.com:yourUsername/yourReponame.git		# same as above
# add changes to your forked repo 
# make a pull request!
$ git pull 										# use this after someone else has made a change to the online repo you r working on and you want to make your local repo up to date
```

### Want to remove a file from online github repo but keep it locally
``` sh
$ git rm --cached localFileName
# add localFileName to .gitignore file 
# then commit these changes
# push these changes to your repo!
```

### Commands for fixing problems
``` sh
# undo multiple commits  
$ git reset --hard commitSHA###... 				# changes staging index and 
                                   				# local folder to match online 
                                   				# repository commit

# removing 3 commits from online github repo
$ git push -f origin HEAD^^^:branchNameToUndoLast3Pushs
```

### Branch Commands 
``` sh
# creating a new branch
$ git branch -a 								# list all branches in working folder  
$ git branch newBranchName  
$ git checkout newBranchName 					# switch to branch newBranchName
$ git push -u origin newBranchName				# adds new branch to github repo and "-u" lets you know when your local branch is different than the remote branch

# merging new branch to old branch
$ git checkout oldBranchName
$ git merge --no-ff newBranchName 				#"--no-ff" creates a commit that there was a branch merge so in the future when you are looking at your commit log you know when exactly when you merged one branch into another
$ git push origin oldBranchName 
$ git branch -D newBranchName 					# deletes local branch newBranchName
$ git push origin --delete newBranchName 		# deletes remote branch newBranchName
```
