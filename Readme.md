# Welcome to CPT(Concepts-Practices-Tasks) Repository for Git and GitHub!
---
## 📋 Table of Contents

1. [Installation](#installation)
2. [GitHub Sign-Up](#github-sign-up)
3. [Initial Configuration](#initial-configuration)
4. [Creating and Cloning Repositories](#creating-and-cloning-repositories)
5. [Working with Local and Remote Repositories](#working-with-local-and-remote-repositories)
6. [Git Staging and Committing](#git-staging-and-committing)
7. [Pushing Changes to Remote Repositories](#pushing-changes-to-remote-repositories)
8. [Pulling Changes from Remote Repositories](#pulling-changes-from-remote-repositories)
9. [Handling Merge Conflicts](#handling-merge-conflicts)
10. [Creating Files with PowerShell](#creating-files-with-powershell)
11. [Branching and Merging](#branching-and-merging)
12. [Renaming the Branches](#renaming-the-branches)
13. [Deleting the Branches](#deleting-the-branches)
14. [Viewing Commit History](#viewing-commit-history)
15. [Stashing, Reverting, and Resetting Changes](#stashing-reverting-and-resetting-changes)

## Installation

Install Git, a version control software, from the official website:

[Download Git](https://git-scm.com/downloads)

## GitHub Sign-Up

Sign up for GitHub, a remote (online) software development platform used for storing, tracking, and collaborating on software projects:

[Sign up for GitHub](https://github.com/)

## Initial Configuration

Verify Git installation by opening your terminal and typing:
```bash
git
```
If installed correctly, a list of features will appear. If not, re-download and install Git properly.

Then Configure Git with your GitHub account username and email:
```bash
git config --global user.name 'username'
git config --global user.email 'Email Id'
```

## Creating and Cloning Repositories
Create a `new repository` on GitHub and name it. Copy the repository HTTPS URL or To initialize a new Git repository, use:
```bash
git init
```
It can convert an existing, unversioned project to a Git repository or initialize a new, empty repository
(A Git repository is a virtual storage of your project. It allows you to save versions of your code, which you can access when needed).

Open your terminal (or VSCode editor) and clone the repository:
```bash
git clone repository_Url
```
if done then we will see the `.git` folder in the hidden views option in our local directory
(Do not modify the '.git' folder, it is the link between our local and remote(online) repositories).

## Working with Local and Remote Repositories
Once the repository is cloned, create a project file. To reflect changes from your local repository to the remote GitHub repository, follow these general rules:
(General Rule: if any changes are made in the local repo, we need to do the necessary steps to reflect in the remote repo, and vice versa). <br> 
`From local to remote(online): add (staging) -> commit -> push` <br> 
`From remote(online) to local: pull`

## Git Staging and Committing
Add file changes in the working directory to the staging area:
```bash
git add [file]
```
Or add all file changes:
```bash
git add .
```
(git add does not affect the repository in any significant way—changes are not recorded until you run git commit) <br>
View the state of the working directory and the staging area:
```bash
git status
```
Commit the changes:
```bash
git commit 
```
(command captures a snapshot of the project's currently staged changes) <br>
Or commit with a message for a specific file:
```bash
git commit -m "message/comment" *filename
```
(*filename is optional to include)

## Pushing Changes to Remote Repositories
Push local repository content to a remote(online) repository:
```bash
git push
```
Or push to a specific remote branch repository:
```bash
git push origin [branch]
```

## Pulling Changes from Remote(online) Repositories
Fetch and download content from a remote repository and immediately update the local repository: (git pull=git fetch+git merge)
```bash
git pull
```
Or download content from a specific remote branch and update the local repository:
```bash
git pull origin [branch]
```

## Handling Merge Conflicts
(Version control systems are all about managing contributions between multiple distributed authors (usually developers).
Sometimes multiple developers may try to edit the same content. 
If Developer A tries to edit code that Developer B is editing a conflict may occur.)
(ex: Conflicts generally arise when two people have changed the same lines in a file, or if one developer deleted a file while another developer was modifying it.
In these cases, Git cannot automatically determine what is correct. Conflicts only affect the developer conducting the merge, the rest of the team is unaware of the conflict.
Git will mark the file as being conflicted and halt the merging process. It is then the developer's responsibility to resolve the conflict.
The most direct way to resolve a merge conflict is to manually edit the conflicted file.) <br>

i.e. Conflicts arise when multiple developers edit the same content. Git will mark the file as conflicted and halt the merging process. Manually resolve conflicts in each file marked by Git. 
To find differences between states of a repository/files, Use:
```bash
git diff
```

## Creating Files with PowerShell
Create an empty file using PowerShell:
```powershell
New-Item -ItemType file [file_name.txt]
```
Echos(prints) content into a Out-File [file_name.txt]:
```powershell
echo "Hello, this is the content of the file" | Out-File [file_name.txt]
```
 
## Branching and Merging
Branches allow you to work on different parts of a project without impacting the main branch. When the work is complete, a branch can be merged with the main project.
You can even switch between branches and work on different projects without them interfering with each other. <br>
List all of the branches in your repository(the branch is a new/separate version of the main repository(local branches)):
```bash
git branch
```
Create a new branch:
```bash
git checkout -b [branch_name]
```
Switch between branches:
```bash
git checkout [branch_name]
```
List all branches in a Git repository, including both local branches and remote branches:
```bash
git branch -a
```
(" -a " option stands for "all").
  
## Renaming the Branches
(1) Rename a branch in the local repository: <br>
Before renaming the branch, switch to a branch other than the one you want to rename. You cannot rename the branch you are currently on. Use
```bash
git checkout [other_branch]
```
rename the old_branch_name with new_branch_name
```bash
git branch -m [old_branch_name] [new_branch_name]
```

(2) Rename a branch in the remote repository: <br>
If the branch has been pushed to the remote repository, you may want to update the remote branch name as well. Use the following command to delete the old remote branch and push the new one
```bash
git push origin --delete [old_branch_name]
```
(Renaming a branch in Git does not create a copy of the branch, instead it directly renames the existing branch. 
 However, when it comes to the remote repository, Git maintains separate references for local and remote branches. 
 when you rename a branch locally using `git branch -m`, the remote repository still has a reference to the old branch name. 
 To update the remote reference and reflect the name change, you use `git push origin --delete [old_branch_name]` to delete the old branch on the remote repository, 
 followed by `git push origin [new_branch_name]` to push the renamed branch)
```bash
git push origin [new_branch_name]
```
The above command pushes the renamed branch to the remote repository with the new name.
    
## Deleting the Branches

(1) Delete a branch in the local repository:
Before deleting the branch, switch to a branch other than the one you want to delete. You cannot delete the branch you are currently on.
```bash
git checkout [other_branch]
git branch -d [branch_name]
```
Deletes the specified branch. If the branch has unmerged changes, Git will prevent the deletion, and you will need to use "-D" to force the deletion. <br>
Force delete a branch with unmerged changes:
```bash
git branch -D [branch_name]
```
Forces the deletion of the specified branch, even if it has unmerged changes. Use this with caution, as it discards any changes in the branch.

(2) Delete a branch in the remote repository:
```bash
git push origin --delete [branch_name]
```

(3) Remove any references to deleted branches from your local repository:
```bash
git fetch --prune
```
The above command is used to update your local Git repository by fetching changes from the remote repository and pruning (deleting) any remote branches that no longer exist on the remote(To delete a file, just push to branch after changes).

## Viewing Commit History
View commit history: <br>
command will display the commit history with the most recent commits listed at the top. You can use the arrow keys to navigate through the log, and press q to exit the log viewer.
```bash
git log
```

View commit history in a single line: <br>
To show each commit on a single line, displaying only the commit hash and the commit message.
```bash
git log --oneline
```

View the commit history of a specific branch:
```bash
git log [branch_name]
```

Limit the number of commits displayed or specify a range of commits:
```bash
git log -n 5
```

Show the last 5 commits in a single line:
```bash
git log --oneline -n 5
```

Show commits from a specific commit to the latest:
```bash
git log [commit_hash]..HEAD
```
 
## Stashing, Reverting, and Resetting Changes

Temporarily save and untrack your local changes that you have not staged yet:
```bash
git stash
```
The above command will save your uncommitted changes to a stack and untrack them from your working directory.
It is useful when you need to switch branches or work on another task but do not want to lose your uncommitted changes. You can then switch branches or work on another task without having to worry about losing your changes. <br>

Restore your uncommitted changes:
```bash
git stash pop
```
The above command will restore your uncommitted changes to your working directory and re-track them. <br>

Show stashed changes:
```bash
git stash list
```
The above command will show you a list of all the stashed changes that you have made. <br>

Revert changes by creating a new commit:
```bash
git revert [commit_sha]
```
The above command creates a new commit that undoes the changes introduced by the commit with the hash commit_sha, after running the `git revert` command, Git will open a text editor (such as `Vim` or the default text editor) for you to enter a commit message. This message typically describes the reason for the revert. ( `type ~ :wq`(write and quit)), Save and close the editor, If there are conflicts during the revert process, Git will mark conflicted areas in the affected files. Then Manually resolve conflicts in each file marked by Git.) <br>
`git revert [commit_sha]` - command in Git is a versatile command that is used to manipulate the commit history, move the branch pointer, and modify the staging area and working directory.
<br>There are different modes of git reset based on the options provided, they are: <br>

Soft Reset: Moves branch pointer, keeps changes staged.
```bash
git reset --soft [commit_sha]
```

Mixed Reset: Moves branch pointer, unstages changes, keeps changes in working directory.
```bash
git reset [commit_sha]
```

Hard Reset: Moves branch pointer, discards changes in staging area and working directory.
```bash
git reset --hard [commit_sha]
```

Reset specific file: Unstaged changes for a specific file.
```bash
git reset [file_name]
```

(Revert vs. Reset: <br>
Revert: Safely undoes changes, preserving commit history. <br>
Reset: Versatile command for moving branch pointer, unstaging changes, or discarding changes. Requires caution, especially with --hard option.)

---

## 📜 License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
