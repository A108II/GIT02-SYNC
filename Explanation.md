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

- We need to add a link to our remote repository in github, the command is: git remote add origin url, url ==> HTTPS in github
Here origin is just a nickname, we can choose anything here, but by convention we give it origin as a nickname to the remote repository. 

- Now the local repository has a link to the remote repository, in order to check that we use this command line: git remote , this gives us the remote repositories that are currently linked. 

- For more details we can use this command: git remote -v (-v stands for verbose = gives us more details)

- In order to remove a link to a remote repository, we use this command 
git remote remove origin

- Uploading code to github => Pushing code to github => Push
- Download from github => Pulling from github => Pull 

- First we push the code the repository,
for this first we need to configure git and github with our usrername
git config --global credential.username A108II
- Pushing the code to github repository: 
git push origin(remote repository) master(branch name)

- When we push our code into the github, we're pushing the code along with the commit history, and we're pushing one branch of commits at a time. For this reason we need to give a branch name to the git push. 

- The command for pushing our code to github is  `git push origin(remote repository we want to push to) master(branch name) 

- Next we're gonna create a 2 way sync feature 

- command `git log --all --graph` will show  (HEAD -> master, origin/master), origin/master means a remote tracking branch. origin refers to the remote repository on github. master refers to the local repository. 

- Next, we're gonna, add a new commmit







 






