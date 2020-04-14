# Section I. Introduction

<img src="imgs\img0.png" width="600px" />

## 2. What is DevOps



A software development approach which involves CD, CT, CI, CDepl, CMonitoring... Includes PLAN, CODE, BUILD, TEST and after test: DEPLOY, OPERATE, MONITOR. If in the MONITOR we face a issue, go back to PLAN, CODE...

<img src="imgs\img1.PNG" width="600px" />

### Dark Launching Technique

- Part 1: the new feature is deployed first on a smaller set of user.  
- Part 2: continuous monitoring, continuous development and continuous testing
  - Monitoring the feedback of the feature
  - Developing the bugs
  - Testing and again deploying. This is the cycle
- Part 3: once the feature is stable, it is deployed on other user bases in multiple releases. We release in multiple release for very specific users. We will release the new features in chunks (multiple releases), this is the Dark Launching Technique.

### Diagram

- Introduce a new feature and deploy it in a specific group in yellow and specific data centre
- Get the bugs and rollback the feature. This is a cycle.
- First the feature goes to a specific user and we get the feedback (Continuous Monitoring)
- Then the feature go back to the development team and fix it and test it (Continuous Development and Testing) and then release a new build and test in (Continuous Monitoring)
- Once the feature is **stable** we release the particular feature to other users (Continuous Integration)
- Once we have that particular feature in our application, we open the feature in multiple releases in multiple users (Continuous Deployment). We are deploying our app continuously on different data centers.  



### DevOps Tools

<img src="imgs\img2.PNG" width="600px" />



## 3. Continuous Development - CD

<img src="imgs\img4.PNG" width="600px" />

- Involves planning and coding the new functionality
- Code mantained in a **Version Control System**
- We must plan the **version** of every release we plan to make



### Version Control System

- Hold a single source of Application
- Which version of the build don't have issues to roll back to it
- It is a centralized code repository
- **Rollout** the faulty snipped of code or complete release and go back to the previous version



### Git and GitHub

<img src="imgs\img5.PNG" width="300px" />

- Git is a tool and GitHub is a repository

#### Distributed Version Control System

- On our server we have a single repo where all my code is placed in
- Then we have the second layer of repo: **staging area**
- Then we have a **working copy** on your desktop computer
- You **commit** changes to the **staging area** and then **push** them to the **central repo**



## 4. Continuous Testing

- When de developer has completed the code, they check in their code to the repository or to some branch or to the intregration or master branch. 
- After the succesful build, we will execute some verification test 
- Example: your are in a team of 40 developers. You are building your product and once it is built you are **executing tor the Jenkins server** (or de the continuous integration server) is executing some kind of**verification and validation test** on that particular **build**. 
- Test are fully automated either with the help of **Selenium** for the **UI** or the REST assured for the back-testing. 
- If the **test** fails, it means that the new code is breaking the already existing code. So we can easily find the bugs.



## 5. Continuous Integration

- Process of automated build and automated test
- We have 10 developers are checking in the code in a shared repo. 
- Jenkings or CI is to pull the code from the shared repository and build it with the help of a build tool (whatever is being used in the development) (i.e Maven). After the build is successful, execute the test on that particular build. This is CI. CI is limited to Automated build. Automated test is not a part of the CI, but by extension, is considered as part of CI
- Jenkings is a CI and CD tool written in Java, which builds test and deploy software projects
- After each change, we run some tests and detect failures... 
- Jenkings also automates deployments  and makes it easy to push code to production.
- We require a server to host Jenkins on.
- Jenkings allows to pull the code from the particular repo and build it with the help of a Build tool (i.e Maven). After the successful build, execute test on the particular build. This is CI. CI is up to automated build. Some people include Automated Tests in the CI.
- **CI helps to detect errors quickly and locate them**

<img src="imgs\img6.PNG" width="500px" />

<img src="imgs\img7.PNG" width="500px" />

- The last shcema is how CI works. Developers commit changes to the Source Code Repo , and this is handled by our Jenkings server or the CI Server, where we build, test and deploy that particular build in our test environment or production for further use. We can **triger** the build on every commit or **schedule** a build...   
- Allows more frequent releases
- CI it helps to create the app and with CDeploy we are building the image or the application.

### Continous Deployment

- **Continuous Deployment**:  is related to CI and refers to keep you application deployable at any point.
- CDeploy we are deploying that build on the servers or on our production servers
- **Continuous Delivery**: is the practice of keep your codebase deployabel at any point. If the CI and CDeploy is successful then CDelivery will be succesful. 
- With the help of CI we are building our project more frequently and with the help pf CDeploy we are deploying our fully qualified build on the Test environment or in the production environment. 

### Continuous Delivery

- Is a practice of keeping your **codebase** deployable at any point of time
- Make sure the application passes automated tests and the configuration necessary is OK to push it into the production
- It means that when talking about CD, we have a set of latest builds and we can push any build, at any time in our production line. 



## 6. Continuous Deployment and Monitoring

CDep means to deploy our service across all the servers which are running (either the clound machines or the hosted machines). Then we are releasing the application on server. This is called the **application deployment**.  The servers could the the Queue environment, the performance environment, the production environment or testing environment.

So CDep will be responsible to deploy your fully qualified application on the production or performance or any other environment. 

### Configuration Management

Mantain the configuration of the servers which will be compatible with your application requirement.

- Establish and Maitain Application's functional requiremente and Performance
  - In our servers where my app is being deployed, I will configure them so that they fulfill the functional requirements and performance requirement. IS the minimum config required to setup my app. 
- Relaseing deployments to Servers
  - Relase the **same deployment** across the servers
- Scheduling Updates on all Servers
  - Any upgrade, updates on your OS,  that should be done on ALL the servers
- Maintain Config Consistency on ALL server
  - All servers where my app is going to be deployed  should have the same config, same OS, same RAM, same resources, same version languages, same tools...



### Containerization

Set of tools that will maitain the consistency across the environment. We contain all the dependencies of the project in a single container 

- We will deploy the same container across all the servers on which my app is going to execute
- If one version changes, maintaining the config consistency across all the servers is part of the Containerization tasks.



### Continuous Monitoring

- Monitoring your application from the performance point of view
- Monitor you application as well as your software health-check.
- Memory USAGE, CPU usage, RAM usage...



## Annex I: pipenv (Python)

- Launch an environment: launch a subshell and locate a Pipfile
```bash
pipenv shell
```
- If we want to know from where Python is being executed inside the pipenv environment:
```bash
python # open the python shell
>>> import sys
>>> sys.executable
#'C:\\Users\\David\\.virtualenvs\\pipenv_tests-kta5TH8-\\Scripts\\python.exe'
```

- Or you can know the folder in:
```bash
pipenv --venv
#C:\Users\David\.virtualenvs\pipenv_tests-kta5TH8-
```

- Where the pipenv project is (folder):
```bash
pipenv --where
#D:\Google Drive\25. SaturdaysAI\pipenv_tests
```


### Install package inside the env
```bash
pipenv install camelcase
```

- If we inspect the **Pipfile** (not Pipfile.lock) in that directory we will see:

```sql
/*
[[source]]
name = "pypi"
url = "https://pypi.org/simple"
verify_ssl = true

[dev-packages]

[packages]
camelcase = "*"

[requires]
python_version = "3.7"
*/
```

- The asterisk means it is the latest version. 

- If we look at the **Pipfile.lock** it has all the **dependencies and the dependencies of the dependencies**. This will help us to have a deterministic build so that we will have the same versions when we are ready to deploy. 


### List the packages of the environment

```bash
pipenv lock -r

#-i https://pypi.org/simple
#camelcase==0.2
```

### Uninstall a package
```bash
pipenv uninstall camelcase
```

### Install packages for only developing, NOT in production

```bash
pipenv install nose --dev
```
- In the Pipfile we will see that is added in the dev-packages:

```sql
/*
[dev-packages]
nose = "*"
*/
```

### Install packages from a requirements .txt


```bash
pipenv install -r requirements.txt
pipenv install -r dev-requirements.txt --dev # to install requirements for the dev packages
```

- These packages will be added in the Pipfile and the Pipfile.lock will be also updated. 

- Or from requirements in github account:

```bash
pipenv install -e git+https://github.com/requests/requests.git#egg=requests
```


### Check for security vulnerabilities

```bash
pipenv check
```

- In some cases if a module version has been updated by correcting mistakes for the previous version, if we are using that previous version we will be noticed.

### Change version of package manually

- We can go to the Pipfile and change manually the version of a package. Once we change it we save the file and run:

```bash
pipenv install
# if we add numpy = "==1.18.2" in the packages section and run install we will get this module with that version
```

- This will look at the Pipfile and check if all the versions match the installed versions, and if not, it will update packages. 

### View dependency graph

```bash
pipenv graph
```

### Prepare for production

- Lock the Pipfile.lock:
```bash
pipenv lock
```

- **Once you get in the SERVER were you want to deploy the code, you want the pipenv install to look at the .lock file and ignore the Pipfile**:

```bash
pipenv install --ignore-pipfile
```

- If you want to install the "dev" packages:

```bash
pipenv install --dev
```



### Remove pipenv virutal env

```bash
pipenv --rm
```

### Generate a requirements file from Pipfile

```bash
pipenv lock -r > requirements.txt
```


# Section II. GIT

## 13) Configuration info

```bash
git config--list
```

```bash
git config --global user.name "Amat, David"
git config --global user.email "daolondrizdaolondriz@gmail.com"
```

## 14) First GIT Repository

Initialize git in the directory that you want to initialize reposityory

```bash
git init
```

Status

```bash
git status
```

You get untracked files and changes not staged for commit.

To commit changes you have to add the changes to my git projects:

```bash
# all changes done in the directory (.)
# it stages unstaged files
# you can stage particular files and leave other files in the directory unstaged
git add .
```

Now git status in on gree and changes are to be committed
```bash
git commit -m "Message of the commit"
```

This will tell us the snapshot of our files 

```bash
git status
```
We will see there is nothing to do, everything is up to date locally. 
When we modify a document, when running git status it locates the changes not staged !

## 16) GIT Logs


```bash
git log
```

We can see all the commit logs and **git commit ID**
To see the particulars commits of a particular member

```bash
git log --author="Amat, David"
```

## 21) Verify changes between local repo and working copy
Changes between the Working area and the Local Repo
```bash
git diff
```
Difference of the Stage Area with Local Repo
```bash
git diff --staged
```

## 24) Delete file in git 

Either remove it manually and then do git add to stage it or do:
```bash
git rm <filename>
```

Our deleted file is then in the Staging Area (no need to do git add).
Now we can commit the changes

```bash

```

## 26) Create Cetralized Repository

- Create a repo in GiHubt
- Create a Folder in your local machine

```bash
git init
```

Pass the URL of the Github repo
```bash
git remote add origin "https://github.com/DavidAmat/xxxx.git"
```

- In my Github account I had a file called README.md  but in my local repo I dont' have anything. 

- Right now my Github account and my Loal Repo are not synchronized.
- I have to **pull the changes from the server**. I **need to provide my BRANCH name**:

```bash
git pull origin master
```

If I go to my folder in local repo we see the README.md

## 27) Create Branch

Create a branch named "develop"
```bash
git branch develop
```
**All code in the master branch is being copiend in the develop branch** 

We are not creating copies of the files, we create pointers for the same file, and such pointers are to the Master and to the newly created branch. 

At this point, if I see a (master) in the command line it means that I have not changed to my new branch. 

If I switch to the **develop branch** and **create a file**, this file is only pointing to the develop branch



**Switch to the new branch**
```bash
git checkout develop
```

If I write git branch to **see all branches**:
```bash
git branch
```

Then I create a new folder and a new file. Check that these are unstaged changes in the develop branch:

```bash
git status
```

Add to the staging:

```bash
git add .
```


To **remove the branch**:
```bash
git branch -d develop
```
If the branch is not fully merged... then we have to add "-D" but be sure that no critical code is to be merged on that branch!

```bash
git branch -D develop
```

Once you have **committed changes to the develop branch** you have to push them:


```bash
git push
# BUT SOME ERRORS WILL OCCUR:
##$ git push
##fatal: The current branch develop has no upstream branch.
#To push the current branch and set the remote as upstream, use

#    git push --set-upstream origin develop

```
This is because **we have to specify that pushing changes are being pushed in the develop branch**

```bash
git push origin develop
```

NOW, once we have pushed, in the GITHUB you WILL SEE the new branch (develop)


## 28) Merge Branches Git

First you need to checkout to the particular branch that you want to merge.
If **we want to merge the changes TO master, we switch to master branch**:

```bash
git checkout master 
```

This merging will **occur in the LOCAL repository**. 
```bash
git merge develop
```
So to make such changes available in GitHub, **once we are in master and have merged the develop branch, we do a push specifying master as origin**:

```bash
git push origin master
```

### Pull changes from Master branch
If I keep doing changes on the Master branch and then one day decide to work on the develop branch, **once in the develop branch, I will have to PULL changes from the master branch**. So I do all the changes in master, I do a push, and then change branch and do a pull (and lastly we will push these changes to the origin develop to update the develop branch in GitHub):

```bash
git add .
git commit -m "Commit to master branch"
git push

# Change branch
git checkout develop
git pull origin master 
```

Once we do the pull, we update the files in the **Local Repo** of your develop branch, but in GitHub, they are the older version still... So you have to **push changes to the develop branch**:

```bash
git push origin develop
```

Finally, I switch to the master and do a merge with the develop and the push the changes to have it all synchronized!

```bash
git checkout master
git merge develop
git push origin master
```

## 29) Revert a Commit in GIT

### A add from Working copy to Staging area

If I do a git add on a file and then want to get it back to the working copy state (look at the first image of this markdown), we have to do a reset:

-The sequence is as follows:

	- You do an git add <filename> (now the file is in the Stagin Area)
	- You realize that you want the working copy back
	- You run:

```bash
git reset HEAD <filename>
```

	- Now the file, when you hit "git status" will be marked as red, as in the working copy, as a modified file that needs to be staged with git add

### A commit to my Local Repo (you want your working copy back)

Once you have add and commit to the Local Repo, imagine you want it back (revert that commit).

```bash
git reset HEAD~ 
```

What it does, it recovers the file that was in the working copy and it lets this file as changes pending to be staged with git add (check it with git status). If we look at git log, we will see that the **message of the commit** that we have reverted is **removed**


## Fork GitHub Project

Fork means, create the repository inside my private space, **copy a target repository into my GitHub repository**.

In GitHub we have a Fork button when we visit someone's else repositories. The icon is a fork, not the box of a repo.

When you clone it to your Local Repo in your local computer, when you hit git clone, it will **create a folder inside the folder where you hit the command**.

When we hit status, it says that your branch is up-to-date with "origin/master".

Here **origin** means:
  - When you put git clone https://github.com/gittower/git-crash-course.git basically **origin** will be a shorthand name for the remote repository (it is used instead of the original repo URL) to make referencing much more easier. 

## Remove git
```bash
rm -rf .git
```

## Fetch

Imagine that we are syncrhed with a github repo.
Now someone creates a branch in the GitHub repo...
Locally, I am not able to do a git checkout to that branck, cause locally it does not exist... so, I **need to fetch the branch**:

```bash
git fecth origin
```

This will take the remote repository from which we have cloned and get ALL the branches that are in GitHub but are NOT in your local.
To **fecth one specific branch**:

```bash
git fecth origin <Name_branch_Github>:<Name_branch_Git>
```
(they should coincide)

## Git reset deleted file

Imagine you delete a file with git rm XXXXX.txt.
Now, if you choose to do a "git reset HEAD XXXX.txt", this WILL NOT restore your file.
You need to do:

```bash
git checkout -- XXXXX.txt
```

## Rename the file
From XXX to YY 
```bash
git mv XXXX.txt YYYY.txt
```

Now the git status shows a renamed line in green! Then, this change has been added to the staging area

If you rename it manually, in the git status, the change is not in the staging area, that is why you need to use git mv otherwise you need to git add after renaming the file. 

## Find Commit, File History

- To verify the last commit we use git log.

```bash
git log
```
- We see the commit hash (the code for that commit)

- If we want one line per commit and make a graph:
```bash
git log --oneline --graph --decorate
```
We see the pictorial info of all the **branches** with the graph command...

<img src="imgs\img8.PNG" width="600px" />

- Filter since 2 days ago:

```bash
git log --since="2 days ago"
```

- If we want the particular changes of a file:

```bash
git log -- <Filename.txt>
```

- If I want the details of a commit ID:
```bash
git show <full ID>
# see the ID in the git log 
```

## Git Alias for long commands

- If I have such a long command:

```bash
git log --all --graph --decorate --oneline
```

- If I create an alias of this command:

```bash
git config --global alias.<name_alias> "log --all --graph --decorate --oneline" 
```
- The configuration file can be edited manually:

```bash
subl ~/.gitconfig
```
<img src="imgs\img9.PNG" width="600px" />
- To run the alias command:
```bash
git <name_alias>
```

## Exclude Unwanted Files in GIT

- Open the **.gitignore**:
  - Imagine I want to exclude test.txt and all the files terminated by .log and a folder named FOLDER:

```bash
subl .gitignore

# add these lines to the gitignore file:
# test.txt
# *.log
# FOLDER/
```

- You will see that such files, in a git status command, they appear in red but tagged as gitignore.


## Compare Working Directory & Stage Area

Compare Working Directory with the Last commit:

```bash
git diff HEAD
```
## Compare Work Directory and GIT Repo

```bash
git diff --staged HEAD
```

## Compare Stage Area and GIT Repo

## Compare Commits in GIT (difference between 2 commits)

```bash
git log --oneline 
```
We get all commits line by line

```bash
git diff <commitID1> <commitID2>
```
Difference between the latest commit and the previous last commit (^)
```bash
git diff HEAD HEAD^
```

# Section IX. Merging and Branching

## Basics of Branches

- List git branches
```bash
git branch -a
```
- Create a branch

```bash
git branch <branch_name>
```

- Master: production
- Branches of features:
  - master
  - develop

- Change branch
```bash
git checkout <branch_name>
```

- Rename branch
```bash
git branch -m <branch_original> <branch_new_name>
```

Delete branch, **before delete the branch, I have to switch to another branch**::

```bash
git branch -d <branch_name>
```

## What is HEAD

You can think of the HEAD as the "current branch". When you switch branches with git checkout, the HEAD revision changes to point to the tip of the new branch.
You can see what HEAD points to by doing:

```bash
cat .git/HEAD
```
It is possible for HEAD to refer to a specific revision that is not associated with a branch name. This situation is called a detached HEAD.


## Happy Path Merges 

Move to the develop branch, make a change and commit it to the branch. Change to master branch. And do:
```bash
git merge <branch_to_merge_to_the_master>
```

The merge is **fast-forward**: if when we created the develop branch, before we have stopped to commit in the master branch, and when we merge the develop with the master  there was no extra committed in the master branch so the merge is fast-forward. It does not have to look and the changes, only move the commits from develop to master! 

## Auto-merge 

Imagine I have two files A and B.
I go to develop, and modify file A and commit
I switch branches and modify file B and commit




If I do:
```bash
git log --oneline --graph --decorate --all
```
<img src="imgs\img10.PNG" width="600px" />

We see that we have started all the commits (from bottom to top) in the master branch.
Then we switch a to a branch (develop) and commit the change in Human.txt.
Then we have switched to master branch and done another commit for the change in a different file


Now I switch to the develop branch and do the same command:

<img src="imgs\img11.PNG" width="600px" />

- The HEAD is in the develop cause we are in the develop.

- Now, I modify another file in the develop and make a merge to the master after commiting the change in the develop

<img src="imgs\img12.PNG" width="600px" />

- Now all the changes done in the develop branch, will be in the master branch


## Merging conflicts 

1) Changes on A (develop) and commit
2) Change to master
3) Go to file A (master) and change them (do other changes, you won't see the changes done in step 1) and commit

<img src="imgs\img13.PNG" width="600px" />

<img src="imgs\img14.PNG" width="600px" />

<img src="imgs\img15.PNG" width="600px" />

- Manually, you have to remove the part of code that you don't want


## Rebase

- Used to merge branches together like merge.

- In this scenario:

<img src="imgs\img16.PNG" width="500px" />

- So, if we are on the feature branch, to incorporate changes that have been implemented by someone else in the master, we have to do a merge with the master:

```bash
git checkout <feature_branch>
git merge master
```

- But when I did this merging:

<img src="imgs\img17.PNG" width="500px" />

I didn't commit anything! So why this **commit of merging is being generated?** This commit 833... is being generated by the git itself as a **merge commit**

- This commit is generated by the git itself, so basically it does like this:

<img src="imgs\img18.PNG" width="500px" />

- Every time you want to update your branch with the commits done in the master branch, a commit is being made.

- If a master branch is VERY ACTIVE, this can pollute your feature branch's history with lots of commits, so won't be easy to follow the history of the project. 

- **Git rebase is the solution to that problem** 

```bash
git checkout <feature_branch>
git rebase master
```

- We want to rebase the master to our feature branch. Git will pick up all the changes from your feature branch and **keep it on the top of the master branch**. So it's kind of trying incorporating all the commits in that feature branch, to the master. 

- GIT Rebase the entire feature branch to begin on the **tip of the master branch**. 

- Instead of using a merge, a rebasing operation re-writes the project history by **creating new commits for each commit** in the original branch. 

<img src="imgs\img19.PNG" width="500px" />

## Git Rebase Benefits

- Much cleaner project history
- Perfect linear project history 

## Git Rebase Example

- From a master-only project, I create a branch and checkout to that branch:

```bash
git checkout -b mybranch
```

- I change file A in mybranch and commit changes 

```bash
git commit -am "Modified text in humans"
```

- I check the git log:
```bash
git log --oneline --decorate --graph --all
```

- I return to my master branch and **modify another file B** and commit it:

```bash
git commit -am "Added message in README"
```

- I execute the log:

<img src="imgs\img20.PNG" width="500px" />

- Now I want to **rebase the master branch with my feature branch**.

```bash
git checkout mybranch

git rebase master
# source branch that you want to rebase

# Message: First, rewinding head to replay your work on top of it...
```
- Now if I check the log:

```bash
git log --oneline --decorate --graph --all
```

<img src="imgs\img21.PNG" width="500px" />

- Now, if I go to the master branch and do another change and commit it (modified again commit):

<img src="imgs\img22.PNG" width="500px" />

- Now if I do a merge

```bash
git merge mybranch
```

<img src="imgs\img23.PNG" width="500px" />

- It has created an extra commit (merge commit). 


## Merge Conflicts Rebase

- I am in the master branch and commit as "Added text on master"

<img src="imgs\img24.PNG" width="500px" />

- Switch the branch to mybranch. Here I modify **the same file again** and commit as "Added conflicts in the feature branch". We open the git log:

<img src="imgs\img25.PNG" width="500px" />

- (recall that now the figure on top is for the mybranch point of view)

- I switch to master branch, and **do another change in the file** (so we have done a change in master, a change in feature branch and another change in master) ("Added trouble in file") 

<img src="imgs\img26.PNG" width="500px" />

- Now I need to rebase mybranch with my master branch.

```bash
git checkout mybranch
```

- Check the log:

<img src="imgs\img27.PNG" width="500px" />

```bash
git rebase master
```
<img src="imgs\img28.PNG" width="500px" />

- Rebase has **not happende due to the merging conflicts**. So first i have to abort it:

```bash
git rebase --abort
```

- And then check the logs:

<img src="imgs\img29.PNG" width="500px" />

- If we list the branches, we will be ina conflict with no selected branch:
<img src="imgs\img30.PNG" width="500px" />

- I have to remove manually the changes conflicted:

<img src="imgs\img31.PNG" width="500px" />

- I commit the file once deleted manually. 

<img src="imgs\img32.PNG" width="500px" />

- It says that rebase is in progress... To fix the rebase conflicts click on rebase continue: 

<img src="imgs\img33.PNG" width="500px" />

```bash
git rebase --continue
```

- It says that my changes are not still done, if I check my current branch:

<img src="imgs\img34.PNG" width="500px" />

- I am on between on something... 

- El tiu es fa un liu... 
<img src="imgs\img35.PNG" width="500px" />

## Rebase remote repository (GitHub)

- Go to the master branch

- I will push my changes to my git repo. 

- For good practices, we first pull master origin:

```bash
git pull origin master
```

- Then I push my changes:

```bash
git push origin master
```

- I do changes in my file in sublime and commit as "Change in Local"

<img src="imgs\img36.PNG" width="500px" />

- I change something in the GitHub! And commit changes on remote:

<img src="imgs\img37.PNG" width="500px" />

- If I run git status, the git status is **not aware of the remote**. 

- **Instead of the pull, execute the command fetch**:

```bash
git fecth
```

- This gets all changes present in the remote repository but NOT present in your machine.

<img src="imgs\img38.PNG" width="500px" />

- We can see 3 changes fetches. If we hit status, we see a diverge of the master branch (my remote and my local is not in synchred)

<img src="imgs\img39.PNG" width="500px" />

- First I need to syncrhed... 

- Now I am going to rebase my local repository with my remote repository (to pick all the changes I have on my branch and put them in the head of the changes in the remote).

```bash
git pull --rebase origin master
```
- We have rebased our directory with the remote directory. 

<img src="imgs\img40.PNG" width="500px" />

- We see that my local changes have been put after the changes done in the remote repo. Now I can push changes to the remote repo.

```bash
git push origin master
```

- And now my local will be in synch with the remote:

<img src="imgs\img41.PNG" width="500px" />


## Git Stash

Save uncommited changes so that you can work on something else and revert them from your working directory (always up to date with your remote repository).
SO I have made changes, I don't want still to commit them but want to save them.


- In the master check status, if you are ahead of the origin/master:

```bash
git pull origin master
git push origin master
```

- Once synchred with the remote repo, we check git status to see all is up to date.

- I change file "simple.html" and add a file name access.log

- We will **stash all this changes**:

```bash
git stash
```

<img src="imgs\img42.PNG" width="700px" />

- If we do a git status we will find that we are in the master branch and everything is still up to date... This is surprising cause we made changes, so that's the effect of stash. We can see that the new file is maintained but the changes in the html have not been kept.

- We make another change in the README and commit the changes and push them. **Although I have made some changes in the sample.html file, where are my changes?**. How can I recover my stashed changes?

<img src="imgs\img43.PNG" width="700px" />

- **See if we have changes stashed** (WIP - work in progress):

```bash
git stash list
```

- How to apply the stashed changes to the working directory

```bash
git stash apply
```

- Now I do a git status:

<img src="imgs\img44.PNG" width="500px" />

- Now the sample.html, README.md, ...  appears as changed... So I only need to commit the changes and push them. 

- But now if I do again a list of the stashed changes:

```bash
git stash list
```

- We will see that they are still there... So we need to drop them:

```bash
git stash drop
```

<img src="imgs\img45.PNG" width="500px" />

- How the log looks like this (**there is no trace of the stash in the git log, only the commits we made after we recover (apply) the stashed changes**)

<img src="imgs\img46.PNG" width="500px" />

### Stash untracked files - pop

- By default, git stashes changes that have been added to your index (staged changes) made to files that are currently tracked by Git (unstaged changes)

- This does not apply hence to **new files** added to the working directory and have not yet been staged (newly created file like the access.log from the example before) or files in git ignore. Those are **not going to get STASHED**. 

- List the git tracked files:

```bash
git ls-files
```

- We modify the .gitignore, if I put in the git ignore "testfile.txt", all changes in that file are not going to be stashed. 

- I modify "humans.txt". Now I add a new file "ANewFile.txt". This new file won't be in the tracked file list. Now I do "git stash":

<img src="imgs\img47.PNG" width="500px" />
<img src="imgs\img48.PNG" width="500px" />

- But we see that in the status, that new file was not stashed by git.

- So how can we track unstashed files?

```bash
git stash -u
#-u stands for untracked 
```

- Now if I look at stashed changes in list:

<img src="imgs\img49.PNG" width="500px" />

-  This way we can also stash the untracked files as well! 

- To stash files in the gitignore, we edit access.log (which is present in the gitignore).

```bash
git stash -a
# a stands for all files
```

<img src="imgs\img50.PNG" width="500px" />

- Now there are 3 stashed changes... **how to get all stashes and include them in your working directory** (is like doing an apply with all the stashed changes): **using the POP only takes the LAST stashed**:

```bash
git stash pop
```
<img src="imgs\img51.PNG" width="500px" />

- If I **execute the pop again**:

<img src="imgs\img52.PNG" width="500px" />

- The git pop is doing an apply of the top stashed change (?? I think is the latest??) and then a drop for that stash so that it does not appear in the stash list anymore. 

- If we do the last pop, we will have done 3 pops so we won't have any stash in the stash list. Now I can commit all the changes and push. 

### Manage Multiple Stash - save, show, apply

- Save specific stashes with a specific messages so that later we can recover them.

- I change simple.html and save the stashed changes:

```bash
git stash save "<message1_simple.html>"
```

<img src="imgs\img53.PNG" width="500px" />

- I change some other file: index.html. I want to stash that particular changes to:

```bash
git stash save "<message2_index.html>"
```

- And also modify the 404.html:

```bash
git stash save "<message3_404.html>"
```

- Now I do a stash list:

<img src="imgs\img54.PNG" width="500px" />

- The top is is the latest change I have made (message3). 


- **I want to see the changes in each stash command: SHOW**:

```bash
git stash show stash@{1}
```
<img src="imgs\img55.PNG" width="500px" />

- **Apply an specific stashed change**:

```bash
git stash apply stash@{1}
```

<img src="imgs\img56.PNG" width="500px" />

- But the stash is being present in the stash list already, so we need to drop it:

<img src="imgs\img57.PNG" width="500px" />

```bash
git stash drop stash@{1}
```

<img src="imgs\img58.PNG" width="500px" />

- IMPORTANT!! See that the next index, the one that before was a 2 **now it's been autoshifted to 1** when dropping index 1. 

- To clear all of the stashed changes list:

```bash
git stash clear
```

### Stashing into branch

- Create a new branch with all stashed changes.

- I change 3 files: index, humans and ANewFile. And I add index.html (staged):

<img src="imgs\img59.PNG" width="500px" />

- And create a new file: dummy.txt

- Now we have different scenarios:

<img src="imgs\img60.PNG" width="500px" />

- One file is modified (index) and in the staged area (we have done the add on index only), two files are modified but not in the staged area and one file is untracked.

- Now I am going to execute a git stash all:

<img src="imgs\img61.PNG" width="500px" />

- Now the git status shows that everything is up to date

- They might be a situation when, when you pick the apply to recover the stashed changes, there are **conflicts** with the files. To avoid this, we will add all the stashed changes in a new branc:

```bash
git stash branch newBranch
# a new branch is being created
```

<img src="imgs\img62.PNG" width="500px" />

- See that the stashed index is being dropped! The git stash list is empty. And if we execute git branch to see which branch am I, **I am in the newBranch**:

<img src="imgs\img63.PNG" width="500px" />

- I checkout to master to merge the branch:

```bash
git checkout master
git merge newBranch
```
<img src="imgs\img64.PNG" width="500px" />

- Now all the changes are in the master branch after that merge. Now I can drop the branch:

```bash
git branch -d newBranch
```

## Git Tagging


<img src="imgs\img65.PNG" width="500px" />
<img src="imgs\img66.PNG" width="500px" />
<img src="imgs\img67.PNG" width="500px" />
<img src="imgs\img68.PNG" width="500px" />
<img src="imgs\img69.PNG" width="500px" />


```bash

```


```bash

```


```bash

```

```bash

```


```bash

```


```bash

```


```bash

```

```bash
for ii in range(16,40):
	print(f'<img src="imgs\img{ii}.PNG" width="500px" />')
```
