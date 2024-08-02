# Syncing in Git & Github

`Git repository`: A folder that is being tracked by the git. 

## Roadmap
- First of all, we're gonna create an online back up of our code using git and Github. Secondly we need to download the special folder from the cloud, if we make any changes to the folder, then it also should be added and updated in the cloud. The third thing is to update the special folder in the local computer whenever something is added to the cloud. This feature is called 2-way sync, we're gonna implement this feature using git & Github. 

### Github initiation
- Github is specifically designed for git repositories, it allows us to manage our code and verison history. 
- We are gonna create a new repository in the Github, and save our code in the repository.
- Go to Github website, click your repository. click new, create repository name and then create repository at the end. 
- Now we have two repository, one is the local repository which is the current file. The other is remote repository which is in Github.

### Linking local repo to remote repo
- Now, we're gonna upload the local repository to our remote repository. For this we have to open the terminal and cd to the current folder. 
- We need to add a remote repository to our git project, the command is: `git remote add origin url`, url can be found when creating a new repository.
- Here origin is just a nickname, we can choose anything here, but by convention we give it origin as a nickname to the remote repository. 
- Now the local repository has a link to the remote repository, in order to check that we use this command line: `git remote` , this gives us the remote repositories that are currently linked to this git project. 
- For more details we can use this command: `git remote -v` (-v stands for verbose which gives us more details)
- In order to remove a link to a remote repository, we use this command: `git remote remove origin`.

### Note
- Uploading code to Github: Push
- Download from Github: Pull 

### Pushing to Github
- When we push our code into the Github, we're pushing the code along with the commit history, and we're pushing one branch of commits at a time. For this reason we need to give a branch name to the git push, which is master in this case.
- The command for pushing our code to Github is  `git push origin(remote repository name we want to push to) master(local branch name)`
- command `git log --all --graph` will show  (HEAD -> master, origin/master) and origin/master, origin refers to the remote branch on Github, master refers to the local branch. 
- Next, we're gonna add a new commmit
`git add .`
`git commit -m "new-commit-name"`
- We're gonna see that the (HEAD -> master) is above the  (origin/master), in order to update the changes, we use this command. `git push origin master`. This way we can see the origin/master is updated with the local master branch.
- Setting up a shortcut for git push:
`git push origin master --set-upstream`
and then we only need to write `git push`.

### Amend the commit
- Next we're gonna use this command `git commit --amend -m "commit-name"`and then `git log --all --graph`. We're gonna see that the  `commit-name` branches off of the current branch. On our local master branch, we got rid of the old commit and overode it. While in Github the master branch has still the old commit.
- Let's override the master branch in Github with our local master branch.
`git push origin master`
- We will encounter this error: 
error: failed to push some refs to `https://Github.com/A108II/git-tutorial2.git`
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
- This error happens because we overrode a commit in Github, and it's generally not a good practice to override, because it removes the commit from Github.  
- So here we write this command: `git push origin master -f` -f means force push the commit to the Github even if it overrides the commit on Github. 
- Now, we can see that the origin/master is in sync with the local master branch.

### Pulling from Github
- Next, we're going to use a feature which enables us to make changes in Github which is the remote repository and it will be synced with the local repository.
- To do this, we're going to download the Github repo in a different folder by using this command in a new terminal and we have to cd to desktop: `git clone url foldername(optional)`. 
- Now we have two local repository, altough they have the same commit history, if we update one of the local repository, it won't affect the others.  We're gonna create a new commit in the recently downloaded folder `git add .`, `git commit -m “commit-name”`, and push it to Github `git push origin master`. 
- Now switching back to the old folder which contains the original commit history, when we use `git log —all —graph`. The commit history shows the previous commit, this shows that remote tracking branches don’t update automatically.
- In order to update the remote tracking branch, we use this command: `git fetch` will update the remote tracking branches in our local machine to the recent state of the remote repository In Github. 
- Here, we will see that the (origin/master) remote tracking branch is ahead of the local master branch.
- Next, we need to sync this commit back to our local repository. Here we need to pull changes from Github, we will use this command: `git pull origin master`  . By using the command `git log —all —graph` we will see that our local branch is in sync with the remote branch.

## Setting up SSH key for Github

- Search for `Set up Github SSH key` on Google
- Click `Checking for exsiting SSH keys` and follow the steps
- Click `Generating a new SSH key and adding it to the ssh-agent` and follow the steps


### The way we can use SSH keys
- We have two urls for the remote repository, https and ssh
- If the folder contains the https url, we can check it by `git remote -v`
- If https url exists, we need to remove it with `git remote remove origin`. `git remote --v` will show us that there is no remote repository that is linked to the local repository. 
- Go to Github, and in the repo click `code` button, and click `SSH`
- Use this command: `git remote add origin SSH-url`
- Now whenever we `git push` it's gonna send our SSH key to the Github.










 






