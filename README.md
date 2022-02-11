# CICD 
- Step 1 - create ssh connection from localhost to github
- 1.1 generate ssh key on localhost
- 1.2 put the lock on githuv - copy the public ssh key to github
- create a new repo for CICD on our github



In order to use any of the CICD technology we need to have an authenticated connection to github.In order to have an authenticated connection to github with a key we need to enter a command into a bash terminal:
- Make sure you are in the ssh directory
- input the command ` ssh-keygen -t rsa -b 4096 -C "fredericoco5@gmail.com"`, the email is the one registered to your github. It will prompt you to give it a name and password. give it a name like `103a` and no password
- This should create a key, you can `cat` the file to make sure it's correct
- Got to github setting and click on SSH keys, click on new key
- give it a name `eng103a` and copy the content of `103a.pub` into the key box
- To create the key you will have to be logged in recently
- create a new repo on github called `CICD etc` (don't add anything like a read me yet)
- select the SSH and copy the key
- create a new directory on your computer called something related to CICD (I called it CICD) use `mkdir`
- input these commands into the new directory
```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin SSH key
git push -u origin main
```
- If there are any issues, delete the 103a and 103a.pem and start again. From making the key on github. when you get back to the step input the command `ssh-add ~/.ssh/103a`
- This will make sure that it idenitifies you and your email
- now the `git push` should work

What is Jenkins:
- Jenkins is an automation server built by Java
- The username is devopslondon and the password is DevOpsAdmin

In order to create a new job:
- click or `create new job` in the middle of the screen or `new item` on the side
- name it and choose freestyle project for now
- give it a description
- discard old builds with a max build number of 3
- go to build and add build steps(execute shell)
- In the shell put in the commands you want to run (uname --a and date for testing)
- apply and save for initial test
- This job should run when you click on build now 
- if it's working the ball on the left will be blue and now you can check the command output
- Create another test, but this time go to build and add `ps aux`
- Go back to the first job and configure, click on post build actions and build other projects, choose the second job and trigger after first is successful.