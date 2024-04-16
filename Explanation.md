## 2-way Sync in Git & Github

- We're gonna create a online back of up our code using git and github.

- Much like Google drive, we want to upload our code in the cloud and download it from cloud when it's needed. 

- Secondly it should let us download the special folder from the cloud, if we make any changes to the folder, then it also should be added and updated in the cloud. 

- The third thing that the cloud service should do is to update the special folder in the local computer whenever something is added to the cloud. 

- This feature is called 2-way sync, we're gonna implement this feature using git & github. 

Note: Git repository is a folder that is being tracked by the git. 

- Github is specifically designed for git repositories, it allows us to manage our code and verison history. 

- We are gonna create a new repository in the github, and save our code in the repository.

- Go to github website, click on the icon, then click your repository. click new, create repository name and then create repository at the end. 

- Now we have two repository, one is the local repository which is the current file. The other is remote repository which is in github.

- Now, we're gonna upload the local repository to our remote repository. For this we have to open the terminal and cd to the current folder. 

- We need to add a link to our remote repository in github, the command is: `git remote add origin url`, url in github
Here origin is just a nickname, we can choose anything here, but by convention we give it origin as a nickname to the remote repository. 

- Now the local repository has a link to the remote repository, in order to check that we use this command line: `git remote` , this gives us the remote repositories that are currently linked. 

- For more details we can use this command: `git remote -v` (-v stands for verbose = gives us more details)

- In order to remove a link to a remote repository, we use this command: git remote remove origin

- Uploading code to github => Pushing code to github => Push
- Download from github => Pulling from github => Pull 

- We need to push the code to the remote repo, but
first we need to configure git and github with our usrername
git config --global credential.username A108II

- When we push our code into the github, we're pushing the code along with the commit history, and we're pushing one branch of commits at a time. For this reason we need to give a branch name to the git push. 

- The command for pushing our code to github is  `git push origin(remote repository name we want to push to) master(branch name)`

- Next we're gonna create a 2 way sync feature 

- command `git log --all --graph` will show  (HEAD -> master, origin/master), origin/master means a remote tracking branch. origin refers to the remote repository on github. master refers to the local repository. 

- Next, we're gonna, add a new commmit
`git add .`
`git commit -m "Version 4"`
 
- We're gonna see that the (HEAD -> master) is above the  (origin/master), in order to update the changes, we use this command. `git push origin master`. This way we can see the origin/master is updated with the local master branch.

- if we write the command again: 
git push origin master
We will see Everything up-to-date

- Setting up a shortcut for git push:
`git push origin master --set-upstream`
and then we only need to write `git push` 


- Next we're gonna use this command `git commit --amend -m "Version 4 new"`and then `git log --all --graph`. we're gonna see that the  `Version 4` branches off of the current branch. On our local master branch, we got rid of the old commit and overode it. While in github the master branch has still the old commit.

- Let's override the master branch in github with our local master branch.
`git push origin master`
- We will encounter this error: 
error: failed to push some refs to `https://github.com/A108II/git-tutorial2.git`
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

- This error happens because we overrode a commit in github, and it's generally not a good practice to override, because it removes the commit from github.  

- So here we write this command: `git push origin master -f` -f means force push the commit to the github even if it overrides the commit on github. 

- Now, we can see that the origin/master is in sync with the local master branch. Now we only see the "Version 4 new" and not "Version 4". Because we replaced the old commit with "Version 4 new". 

- Next, we're going to use a feature which enables us to make changes in github which is the remote repository and it will be synced with the local repository, this way local repository will also be affected. 

- To do this, we need to pretend that we're on a different machine, and we're going to download the github repo by using this command in a new terminal and we have to cd to desktop: `git clone url foldername(optional)`. 

- Now we have two local repository, altough they have the same commit history, if we update one of the local repository, it won't affect the others. We're gonna create a new commit in the recently downloaded folder, and push it to github and then sync those changes back to our local repository (The old one). 

- Now switching back to the old folder which contains the original commit history, when we use `git log —all —graph`. The commit history shows that the last commit is Version 4 new. But it should be Version 5. This shows that remote tracking branches don’t update automatically. 

- In order to update the remote tracking branches, we use this command: `git fetch` will update the remote tracking branches to the current state In GitHub. 

- Here, we will see that the (origin/master) branch is ahead of the local master branch. Next, we need to sync this commit back to our local repository. Here we need to pull changes from GitHub, we will use this command: `git pull origin master`  . By using the command `git log —all —graph` we will see that our local  master branch is in sync with the remote branch. By using `git pull origin master —set-upstream` command git will memorize the origin and master. So if we type `git pull` it will do the same job. If we run this command once, it will work for `git pull` and `git push`. 

## Setting up SSH key for Github

- Search for `Set up Github SSH key` on Google: `https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account`
- Click `Checking for exsiting SSH keys` and follow the steps
- Click `Generating a new SSH key and adding it to the ssh-agent` and follow the steps


### The way we can use SSH keys
- We have to urls for the remote repository, https and ssh
- If the folder contains the https url, we can check it by `git remote -v`
- If https url exists, we need to remove it with `git remote remove origin`. `git remote --v` will show us that there is no remote repository that is linked to the local repository. 
- Go to Github, and in the repo click `code` button, and click `SSH`
- Use this command: `git remote add origin SSH url`
- Now whenever we `git push` it's gonna send our SSH key to the github, instead of us entering the password. 










 






