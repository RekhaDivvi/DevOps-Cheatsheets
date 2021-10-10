# Git

<hr>

### 1. What is version control system?
Version control, also known as source control, is a system that records changes to a file or set of files over time so that you can recall specific versions later. Version control systems are software tools that help software teams manage changes to source code over time.

**Ex:** Git, Subversion

A version control system serves the following purposes,

- Version control enables multiple people to simultaneously work on a single project. Each person edits his or her own copy of the files and chooses when to share those changes with the rest of the team.
- Version control integrates work done simultaneously by different team members. In rare cases, when two people make conflicting edits to the same line of a file, then the version control system requests human assistance in deciding what to do.
- For any part of a file, you can determine when, why, and by whom it was ever edited.
- Version control gives access to historical versions of your project. This is insurance against computer crashes or data lossage. If you make a mistake, you can roll back to a previous version. You can reproduce and understand a bug report on a past version of your software.

### 2. What is Git and why it is used?
Git is the most commonly used version control system. Git is software for tracking changes in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development.

Advantages:
- Create proper work flows. Git also makes collaboration easier, allowing changes by multiple people
- Git tracks the changes you make to files (Keep the history of changes - who, why, and when changes were done), so you have a record of what has been done, and you can revert to specific versions should you ever need to.
- Each version has a description of what the changes in this version are done. These descriptions help in tracking the changes in the code by version.
- Synchronizes the versions and ensures that your changes don’t conflict with others using the same repository.
- In any case if your central server crashes, a backup is always available in your local systems.

### 3. What are different types of version control system?
There are two types of version control: centralized and distributed.

**`Centralized version control system (CVCS):`** In centralized version control, each user gets his or her own working copy, but there is just one central repository. This central server enables team collaboration. It just contains a single repository, and each user gets their working copy. We need to commit, so the changes get reflected in the repository. Others can check our changes by updating their local copy. 

**Ex:** Subversion (SVN)

Benefits of CVCS:

- Easy to learn and manage 
- Works well with binary files 
- More control over users and their access. 

Drawbacks of CVCS:

- It is not locally available, which means we must connect to the network to perform operations. 
- During the operations, if the central server gets crashed, there is a high chance of losing the data. 
- For every command, CVCS connects the central server which impacts speed of operation 

**`Distributed version control system (DVCS):`** In distributed version control, each user gets his or her own repository and working copy. So the complete code base (including its full history) is mirrored on every developers computer. The User needs to update for the changes to be reflected in the local repository. Then the user can push the changes to the central repository. If other users want to check the changes, they will pull the updated central repository to their local repository, and then they update in their local copy. 

**Ex:** Git, Mercurial 

Benefits of DVCS

- Except for pushing and pulling the code, the user can work offline in DVCS 
- DVCS is fast compared to CVCS because you don't have to contact the central server for every command 
- Merging and branching the changes in DVCS is very easy 
- Performance of DVCS is better 
- Even if the main server crashes at any point of time, the lost data can be easily recovered from any one of the developer’s local repositories.

![image](https://user-images.githubusercontent.com/43535914/129599133-211e5789-652c-4869-88bd-ab5de3f606b9.png)

### 4. Explain the following:
**1) Git &emsp;&emsp; 2) GitHub &emsp;&emsp; 3) Git Bash &emsp;&emsp; 4) Source tree** 

**`1) Git:`** Git is a software and a version control system that lets you manage and keep track of your source code history.

**`2) GitHub:`** GitHub is a cloud-based hosting service that lets you host and manage Git repositories so that you don't have to set up your own server. Alternatives of GitHub are GitLab, BitBucket, etc.

**`3) Git Bash:`** Git Bash is a command line tool installed locally on system. Git Bash is an application for Microsoft Windows environments which provides an emulation layer for a Git command line experience. Gitbash is a very handy tool that helps you use git and linux commands in windows to connect and use git. (As the name says, Git Bash (Bourne Again Shell) is a terminal application used to interface with an operating system through written commands)

**`4) Source tree:`** SourceTree is a GUI application that you can use to work with git if you don't like the command line tools. Another alternative of sourcetree could be GitHub Desktop.

### 5. What is .git folder for and what does it contain?
.git (hidden by default) will be created inside the repository when you initialize new repository using git init command. In .git folder contains all the information that is necessary for your project/repository. The .git folder will contain details of every single change made to the code base. Without .git folder, your project is a local project and not a git project which means you cannot perform any git operations.

.git folder contains:
-  Remote information (to which remote server your project is connected)
-  History of all local commits
-  Branch information (on which branch is your current project state (HEAD) pointing to)
-  Contains a log that stores your commit history so that you can roll back to history.

### 6. What is bare and non-bare repository?
A bare repository is one that contains nothing but the .git folder; in other words, it has the index but lacks the actual working files. No commits can be made in a bare repository and the changes made in projects cannot be tracked by a bare repository as it doesn't have a working tree. These repositories are only for storing & sharing code. 

A non-bare repository is what you're used to working with, which includes both the git index and the checked out copy of working files.

### 7. What is a git snapshot?
A snapshot is a copy of your project at some point of time. A snapshot is generated whenever changes are committed. Every time you commit to a git repository, you are saving a snapshot of all the files in your repository. Instead, each commit, git saves the changes from the previous commit.

### 8. Explain the core areas of Git: Working directory, staging area, local repository, remote repository
Files in a repository go through following stages before being under version control with git:

- Untracked/modified: Untracked means that the file is new to your Git project. The file exists, but is not part of git's version control (which basically means that Git sees a file you didn’t have in the previous snapshot or commit). Modified means that the file has been seen before, but has been changed. Modification of a file occurs in your working directory.
- Staged: The file has been added to git's version control but changes have not been committed. Stage the files and add snapshots of them to your staging area. 
- Unstaged: It means that some changes in tracked file that are not yet in staging area.
- Committed: Commit stores the snapshots permanently to your Git directory. Committed means that Git has officially taken a snapshot of the files in the staging area, and stored a unique index in the Git directory. Commit means that packaging all your files in order to push to your remote repository
<br>
When working in a git repository files and modifications will travel from the Working Tree to the Staging Area and finish at the Local Repository.

**`1) Working directory:`**	(Files are modified but untracked).
It is basically where you are currently working. This is the directory where all your project files and folders reside (along with the .git folder). If you make changes to files in your working tree, git will recognize that they are modified, but until you tell git, it won’t save anything that goes on in them. This area is also known as the “untracked” area of git.
How can you see what is in your Working Tree? Run the command "git status".

**`2) Staging area/index:`** (adding snapshots to staging area)
The Staging Area is when git starts tracking and saving changes that occur in files. These saved changes reflect in the .git directory. You tell git that I want to track these specific files (by issuing git add command), then git says okay and moves them from you Working Tree to the Staging Area. However, if you make any more additional changes after adding a file to the Staging Area, git will not know about those specific changes until you tell it to see them. 
Staging area can be considered as a preview of your next commit. Before committing a file, it can be reviewed in this intermediate area.

**Ex:** Let's say you have 10 modified files and when you think about pushing it to server, you realised you don't want to push 5 files out of them then you would only stage 5 files which you want to push to server. So it is basically a marker which files you want to push and which are yet to worked upon.

**`3) Local repository:`**	(stores that snapshot permanently to .git directory)
The Local Repository is everything in your .git directory. Mainly what you will see in your Local Repository are all of your checkpoints or commits. It is the area that saves everything. We move from the Staging Area -> Local Repository when we issue a git commit command.

**`4) Remote repository:`** The remote repository refers to the server repository that may be present anywhere. This repository is used by all the team members to exchange the changes made.

Run the command "git status" after each stage (ie., after modifying files in working directory, after adding changes to staging area and after commiting), to get to know what is happening while transition of file changes across different stages.

![image](https://user-images.githubusercontent.com/43535914/129604799-227ad7cd-410c-43d4-853e-793c2d21794c.png)


### 9. How does Git store information/data?

Git uses a three-level structure for this:
- A commit contains metadata such as the author, the commit message, and the time the commit happened. In the diagram below, the most recent commit is at the bottom (feed0098), underneath its parent commits.
- Each commit also has a tree, which tracks the names and locations in the repository when that commit happened.
- For each of the files listed in the tree, there is a blob. This contains a compressed snapshot of the contents of the file when the commit happened (blob is short for binary large object, which is a SQL database term for "may contain data of any kind"). In the middle commit, report.md and draft.md were changed, so the blobs are shown next to that commit. data/northern.csv didn't change in that commit, so the tree links to the blob from the previous commit. Reusing blobs between commits help make common operations fast and minimizes storage space.

Note:
Git stores each commit by a unique identifier called as commit hash (SHA)

![image](https://user-images.githubusercontent.com/43535914/129769817-16cc240a-359c-4592-9813-8c6ea45329a7.png)

### 10. Where does git store files?
Git stores snapshot of your files (that have changes). Git stores the complete history of your files for a project in a special directory (a.k.a. a folder) called a repository, or repo. This repo is usually in a hidden folder called .git sitting next to your files.  Git is smart and does not replicate all your files, and instead keeps only changes to your files.

### 11. How do you ignore certain types of file in your repository?
.gitignore is a specific file used to list what (type of) files you do not want git to track. This file need to be placed at the top level of the directory. It's Good to create a gitignore at the start of project because files already been tracked by Git are not affected.

Ex:

You can ignore certain type of files, such as all files in logs directory (excluding the .gitkeep file), whole tmp directory and all files *.swp, *.exe, etc. File ignoring will work for the
directory (and children directories) where .gitignore file is placed

    /logs/*
    !logs/.gitkeep
    /tmp
    *.swp
    *.exe
    *.gz
    *.sql

### 12. What is a git branch and why do we use them?
A git branch is essentially an independent line of development that isolates your work from that of other team members. We will use branch when working on new features, releases or bug fixes etc.
##### Branch Types: 
Below mentioned are some of the branch types.

Branch name | Description
----------- | -----------
master | Usually the integration branch and is often the default branch
feature | Used for specific feature work or improvement.
release | Used for release tasks and long-term maintenance versions.
bugfix | Typically used to fix Release branch issues
hotfix | Used to quickly fix a Production branch issue

![image](https://user-images.githubusercontent.com/43535914/129941330-f4c1e7a0-c814-402a-8133-53626b95db8a.png)

### 13. What is pull request?
A pull request is a practice of having code changes reviewed by someone and getting feedback to "merge" or "do not merge" the code.

### 14. Explain basic Git workflow?
##### Local workflow:
- Either create a new repository in the local system (git init) or clone existing repository (git clone) or pull latest changes if repository exists in local (git pull).
- Create/modify/delete files in your working directory and save them as usual
- Add snapshots of your changes files to your staging area
- Do a commit, which takes the files as they are in the staging area and permanently stores them as snapshots to your Git directory.
- Connect the local repository to your remote repository and push the latest changes

![image](https://user-images.githubusercontent.com/43535914/129610463-da6488c4-c078-4a09-8f86-47c53bb91273.png)

##### Working with remote repository:
- Code in master is deployable at all times.
- When you want to start working on a new task, create a new branch off of master and give it a descriptive name.
- Commit to that branch locally and regularly send your work to the same-named branch on the server.
- Open a pull request when you feel your changes are ready to be merged (or even if you aren’t so sure, but would like some feedback).
- After the new feature is revised and approved, you can merge it into master/equivalent branch.
- Once your changes are merged and pushed to relevant branch, you can deploy immediately.

### 15. Git commands
<details>
<summary>Setting up your identity (Configure user information)</summary><br> 
You need to do this step the first time you use git on a computer.
    
```sh    
# Set username and email
$ git config --global user.name "yourName"
$ git config --global user.email "yourEmail"
    
# View configuration settings and check that everything is correct
$ git config --list	 

# Modify everything at the same time.
$ git config --global --edit   
    
# Set your text editor:
$ git config --system core.editor vim    
```    
</details>    


<details>
<summary>Getting & creating projects/repositories</summary><br>

Init:
```sh 
# Initialize an existing folder on your system as a new Git repository. This creates a .git directory that contains all the Git-related information for your project.    
$ git init
```    

Clone:    
```sh 
# Copying an existing repository to your system (This will copy all branches). The cloning process will automatically create a directory on your machine named like the online repository.     
$ git clone <Git_Repo_URL>  
    
# To clone one specific branch
$ git clone <Git_Repo_URL> --branch <branch_name> --single-branch
```    
</details>       


<details>
<summary>Basic snapshotting - File modification related commands</summary><br>

Stage:
```sh     
# Stage file for commit. Snapshots the file in preparation for versioning
$ git add <file1> <file2>
    
# Stage all files for commit
$ git add .  
```
    
Unstage: 
    
```sh    
# Used to unstage a file which is been added to staging area    
$ git rm --cached <filename>   (or)   git reset HEAD <filename>
```
    
Commit: Records file snapshots permanently in version history

```sh      
$ git commit -m “commit message”
```
    
Remove a file or folder
    
```sh      
$ git rm -r <filename> 
```
    
</details> 
    
<details>
<summary>History and log related commands</summary><br>    
status: 
    
```sh  
# Displays the status of the current repository. It displays whether everything is up to date or untracked files, changes not staged, changes to be committed etc.    
$ git status
```
    
show:

```sh
# Shows meta data and content changes of a commit    
$ git show <commit-id>
```
    
diff: Display the differences between 2 versions, or  working directory and an index, or index and most recent commit.

```sh    
# Compares working directory with index, i.e. shows the changes that are not staged
$ git diff
    
# Compares index with local repository. Track changes that have staged but not committed
$ git diff --staged (or) git diff --cached
  
# Track the changes after committing a file
$ git diff HEAD
    
# Track changes between two commits
$ git diff <commit-id1> <commit-id2>
    
# Shows content differences between two branches
$ git diff <branch-1> <branch-2>
```
    
Log:

```sh    
# Display the entire commit history for the current branch using the default format
$ git log
  
# View changes (detailed)
$ git log --summary
   
# View changes (briefly). Displays short log, One commit per line. An overview with reference labels and history graph
$ git log --oneline  (or)  git log --pretty=oneline
    
# List commit history of current branch. -n count limits list to last n commits. Ex: git log -3
$ git log -n  
```   
   
</details>  
   
   
<details>
<summary>Rewriting Git history</summary><br>    
   
Modify commit message:
    
```sh 
# Used to modify the most recent commit. If you wrote something wrong in a commit message, then use "amend" to edit your very last and unpushed commit    
$ git commit --amend -m "new commit message"
```
    
Rebase: Rebasing is changing the base of your branch from one commit to another making it appear as if you'd created your branch from a different commit. Internally, Git accomplishes this by creating new commits and applying them to the specified base. 

```sh    
# Here <base> can be a commit ID, branch name, a tag, or a relative reference to HEAD
$ git rebase <base>  
```    
     
</details>
   
   
<details>
<summary>Temporary commits</summary><br>    
Temporary commits are used when we do not want to commit our code but also don’t want to lose the unfinished code. Then we can use git stash command to record the current state of the working directory and index. 
    
**Ex:**
    
![image](https://user-images.githubusercontent.com/43535914/129778194-619137ab-f71f-4579-8fc9-2e7d88b4f50c.png)

To stash local changes:
    
```sh     
# The git stash command takes your modified tracked files and saves it on a pile of incomplete changes that you can reapply at any time    
$ git stash
    
# Stash local changes with a custom message    
$ git stash save "message"    
```
       
Re-apply the changes you saved in your stash

```sh    
# To bring back the saved changes onto your current working directory and continue working where you had left your work. Pop will apply the stash and then immediately drop it from your stack
$ git stash pop
    
# Re-apply the changes you saved in your latest stash. Same as pop but leaves stashed changes in the stash list for reuse. You can later use git stash drop to delete it
$ git stash apply
    
# Re-apply the changes you saved in a given stash number
$ git stash apply stash@{stash_number}    
```
  
List:
    
```sh   
# List all stashes.
$ git stash list   
    
# Show the latest stash changes
$ git stash show    
```
    
Discard saved stash 
  
```sh    
# Discards the most recently stashed change set
$ git stash drop
    
# Discard stash particular stash by its number
$ git stash drop stash@{stash_number}
   
# Remove all stashed entries
$ git stash clear
```
    
</details>    
    
<details>
<summary>Tags</summary><br>    
A tag is a user-friendly label attached to a particular commit and thereafter does not change, even if the branch moves on. In other words, tags are immutable references. 
A "tag" object allows to mark certain important revision or releases. Tags can help the users of the repo to easily navigate to the important parts of the code history like release points. 
    
Ex:     
git tag v1.2.1
    
Types of tags in Git:
- Lightweight tags: Creates without a message, so the only hint as to what the tag is about is how you name it.

- Annotated tags: These are stored as full objects in git database. Contain tagger name, email and date: have a tagging message.   
    
To Create a tag
    
```sh    
$ git tag <tag_name> -m "any message"
```
    
Tagging existing commits
    
```sh    
# Tagging old commits (You can specify whole commit id or first few digits of commit id) Ex: git tag -a v1.2 15027
$ git tag -a <tag-name> <commit-id>
    
# ReTagging /Replacing Old Tags. If you try to tag an older commit with an existing tag identifier Git will throw some error then -f FORCE option must be used
$ git tag -a -f <tag-name> <commit-id> 
```
    
To view all information about tag (who, when committed etc)
    
```sh    
$ git show <tagname>
```    
    
To List all tags
    
```sh
$ git tag (OR)  git tag -l
```
    
Push tags:
    
```sh    
# To push Tags to Remote. By default, git push will not push tags. Tags have to be explicitly passed to git push
$ git push origin <tagname>
    
# To push all tags at once
$ git push origin --tags
```
    
Delete tags:
 
```sh    
# Delete all local tags at once. If you want tags again locally. Then use git fetch to get remote tags locally. Check using git tag command. Now you will have tags in local
$ git tag -d $(git tag -l)
    
# Delete a remote tag
$ git push origin --delete <tagname>  (OR)  git push origin :refs/tags/<tagname>
    
# Delete all remote tags at once
$ git push origin --delete $(git tag -l)
```
    
</details>    
   
   
<details>
<summary>Undo Changes</summary><br> 
 
```sh    
# Discard changes to a file in working directory. Suppose we have modified 3 files in working directory, but we don’t want modification for 3rd file then we can discard those changes using this command.
$ git checkout -- <filename>
   
# Undo local commit changes (In the below command, HEAD~1 represents latest commit)
$ git reset <commit>  (OR)  git reset HEAD~1
   
# Undo remote commit changes
$ git revert <commit>
```
    
</details>    
   

<details>
<summary>Branching and Merging</summary><br>    

Create and switching among branches
 
```sh    
# Create a new branch
$ git branch <branch-name>
    
# Switch to the specific branch
$ git checkout <branch-name>
    
# Create a new branch and switch to it. (git checkout -b [branch-name] = git branch [branch-name] + git checkout [branch-name])
$ git checkout -b <branch-name>
    
# Switch to the branch last checked out
$ git checkout -
```
    
Rename branch (local branch)
   
```sh    
# Renames the current branch to new branch name
$ git branch -m <new_branch>
    
# Rename a specific branch with new name
$ git branch -m <old-branchname> <new-branchname>
```
    
Merge
   
```sh    
# Merge specified branch history into the active branch ie.,current branch. Ex: Lets say, you want to merge feature branch into master branch. First check if you are in master branch or not. If not do git checkout master. Then do "git merge <feature-branchname>"   
$ git merge <branch-name>
    
# Merge a branch into a target branch
$ git merge <source branch> <target branch>
    
# Prints the branches merged into master. Used to know whether a branch is already merged or not.
$ git branch --merged master
    
# Viewing all branches that have been merged into your current branch, including local and remote
$ git branch -a --merged
    
# Viewing all branches that haven't been merged into your current branch, including local and remote
$ git branch -a --no-merged
```        
   
List
   
```sh    
# Lists all local branches 
$ git branch
    
# Lists all local and remote branches
$ git branch -a
    
# Viewing remote branches
$ git branch -r    
```    
    
Delete
    
```sh   
# Deletes the specified local branch. Prevents you from deleting the branch if it has unmerged changes
$ git branch -d <branch-name>
    
# Force delete a local branch without checking its merge status, even if it has unmerged changes
$ git branch -D <branch-name>
    
# To delete a remote branch through command line
$ git push origin --delete <branch-name>
    
# Remove any remote refs you have locally that have been removed from your remote (you can substitute <origin> to any remote branch)
$ git remote prune origin    
```    
      
</details>    

<details>
<summary>Synchronizing repositories</summary><br>    
   
Remote

```sh    
# Add a remote remote repository. Used to connect your local repository to the remote server
$ git remote add origin <Repo-URL>
   
# To check whether your origin is set or not
$ git remote -v
   
# Deletes the origin
# git remote remove origin  
```
    
Push
  
```sh    
# Sends the branch commits to your remote repository
$ git push origin <branch-name> 
    
# Pushes all branches to your remote repository
$ git push --all origin
    
# Pushing local branch to remote
$ git push -u origin branchname    
```
    
Pull:
   
```sh
# Updating a local repository with changes from a Github repository. It will fetch and merge the changes on the remote server to your working directory    
$ git pull <Repo_URL>
(OR)
$ git remote set-url “https://github.com/RekhaDivvi/test.git” and then git pull origin master	
```
    
Fetch:

```sh       
# Fetch changes from the remote, but not update tracking branches
$ git fetch [remote]
    
# This will fetch all the remote branches for you.
$ git fetch origin    
```    
      
</details>    


### 16. What is Git Reset?
Git reset is used to undo local changes to the state of a Git repo. Reset command tells Git to reset HEAD to another commit. In general, git reset's function is to take the current branch and reset it to point somewhere else, and possibly bring the index and work tree along.

Ex:
If your master branch (currently checked out) is like this:

    - A - B - C (HEAD, master)
    
and you realize you want master to point to B, not C, you will use git reset B to move it there:

    - A - B (HEAD, master)      # - C is still here, but there's no branch pointing to it anymore

Digression: This is different from a checkout. If you'd run git checkout B, you'd get this:

    - A - B (HEAD) - C (master)    
    
You've ended up in a detached HEAD state. HEAD, work tree, index all match B, but the master branch was left behind at C. If you make a new commit D at this point, you'll get this, which is probably not what you want:

    - A - B - C (master)
           \
            D (HEAD)
    
Remember, reset doesn't make commits, it just updates a branch (which is a pointer to a commit) to point to a different commit.
    
##### Types of git reset:
Git reset operates on "The Three Trees of Git". These trees are the Commit History ( HEAD ), the Staging Index, and the Working Directory.   
   
- Soft	=>  Uncommit changes, changes are left in staging and working tree
- Mixed	=>  Uncommit + Unstage changes, changes are left in working tree (default)
- Hard	=>  Uncommit + Unstage + delete changes, nothing left

Example of soft reset:    
    
![image](https://user-images.githubusercontent.com/43535914/129939714-4a725f1d-e693-4380-8fcc-0d43e2610f0a.png)

    
### 17. Are git fetch and git pull the same?
git fetch is the command that tells your local git to retrieve the latest meta-data info from the original (yet doesn't do any file transferring. It's more like just checking to see if there are any changes available). If you want to reflect these changes in target branch, git fetch must be followed with a git merge. git pull on the other hand download latest changes from the remote repository and automatically merge those changes in current working/target branch of local repo and other branches stay unaffected. It does not give you a chance to review the changes and as a result conflicts might occur.
    
In Short, **git pull = git fetch + git merge**
    
### 18. What is merge conflict?
A merge conflict is an event that occurs when Git is unable to automatically resolve differences in code between two commits. Sometimes the commit to be merged and current commit have changes in same location. In this scenario, GIT is not able to decide which change is more important and due to this GIT reports a merge conflict.  

Ex:
Let’s assume there are two developers: Developer A and Developer B. Both of them pull the same code file from the remote repository and try to make various amendments in that file. After making the changes, Developer A pushes the file back to the remote repository. But these changes are not known to Developer B. Now, when Developer B tries to push that file after making the changes from his end, he is unable to do so, as the file has already been changed in the remote repository and Developer B has modified the old version of file.

### 19. How to handle the merge conflicts in Git?    
When merge conflict occurs, Git will mark the file as being conflicted and halt the merging process. The conflicted file looks as shown below
    
    <<<<<<< HEAD
    This is an edit on the master branch
    =======
    This is an edit on the branch
    >>>>>>> branch_to_create_merge_conflict    

As you can see, Git added some syntax including seven "less than" characters, <<<<<<< and seven "greater than" characters, >>>>>>>, separated by seven equal signs, =======. The easiest way to resolve a conflicted file is to open it, delete those extra lines added by git, make any necessary changes to the file. After editing the file, we can use the git add command to stage the new merged content and commit those changes.
    
### 20. What is the difference between git rebase and git merge?
Git rebase and merge both integrate changes from one branch into another. Where they differ is how it's done. 

##### Git rebase:    
When we perform rebase of a feature branch onto the master branch, we move the base of the feature branch to the master branch ending point. It re-writes the changes of one branch onto another without creating a new commit. In Rebasing, we move a branch from one commit to another. By this we can maintain linear project history.

##### Git merge:    
Merge is pretty much like taking two threads and tying them up in a knot. By performing merge, we take the contents of the feature branch and integrate them with the master branch. As a result, only the master branch is changed, but the feature branch history remains the same. In the below example, the commit ‘b’ has the information regarding all the commits in feature1 and feature2. So, Git merge adds a new commit, preserving the history.
    
Ex:
Let’s say we have two branches feature1 and feature2 that have diverged from a common commit “a”. Now we want to combine both the features into a single branch
    
![image](https://user-images.githubusercontent.com/43535914/129946843-db9ebee7-1a6c-4527-81aa-60b6ab9e5c9e.png)
    
### 21. Difference between git reset and revert?
Reset moves the pointer back to the commit you specify, while revert creates another commit at the end of the chain to cancel the change. Reverting undoes a commit by creating a new commit. It is similar to the reset command, but the only difference here is that you perform a new commit to go back to a particular commit.   
    
### 22. What is git cherry pick?
Cherry picking is the act of picking a commit from a branch and applying it to another. It does not alter current history, instead it adds commits to it.
    
Ex:  
    
Lets say a commit is accidentally made to the wrong branch but do not want to merge the whole branch. You can switch to the correct branch and cherry-pick the commit to where it should belong. Cherry picking is commonly discouraged in the developer community. The main reason is that it creates duplicate commits and you lose the ability to track the commit history.
    
### 23. Can we skip staging area and directly commit changes to local repository?
Partially true.
- New files cannot be added directly into commit area without staging because those are untracked files. 
- Modified file can directly be added to commit area. When I modify existing file and do git status, it shows file is modified rather than showing untracked file. Already this file references are there in the meta data of local repository so it can be skipped from staging area.
    
Git commit -a -m “directly adding into commit area”    
    
    
    
