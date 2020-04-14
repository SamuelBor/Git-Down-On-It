# Git Down On It: A Cheat Sheet for Essential Git Functions
### What is Git?

Git is a **distributed version-control system** (VCS) for tracking changes in source code, first developed in 2005 by Linus Torvalds. It allows collaborative work between software developers, by facilitating independent local branches that can be easily switched between, and a seamless merging process. By encouraging developers to save incremental commits of their code, projects can easily be rolled back to a previous, working version if something goes wrong. 

The **distributed** part of Git means that instead of 'checking out' just the current tip of the source code, developers 'clone' an entire repository onto their machines. This means that there is no single point of failure as every user essentially has a full backup of the main server.

There are many companies that offer **remote hosting** of repositories using Git, such as GitHub or GitLab. GitHub provides an expansive web interface to allow users to easily manage access controls, track bugs, request new features and write a 'wiki' page for every repository.


### What is Git Down On It?

There are many graphical implementations of the key Git functions, but the original interface was a command line interface. These terminal commands like these are still very relevant and useful today, which is why Git Down On It was created: to give beginner Git users a solid foundation of the commands they should know/be aware of. 

Although this information can be found elsewhere online, we often found ourselves trawling through documentation pages and Stack Overflow answers to find some of the most basic commands. This cheat sheet aims to consolidate this basic information into one, accessible page that can help beginners get started in the world of version control and software development. 


- - - -
## Glossary of Key Terms
**Repository:** A Git Repository tracks the changes made to files inside a specified project directory, building a history over time.

**Commit:** A Git Commit is used to save your changes to the local repository you are currently working on. For the sake of version control, commits are kept in a repository indefinitely. 

**Branch:** A Branch in Git points to an independent line of development within your project that is encapsulated from the rest of the work. For example, when adding a new feature to a project, you would develop it in a separate branch that does not affect the rest of the work, to allow for any bugs or conflicts.

**Master Branch:** The Master Branch in a Git repository is the main branch that all other branches spawn off of, and where all branches will subsequently be merged back into before formal deployment. This branch should be carefully protected as unconsidered changes can easily break a piece of software and cause merge conflicts.

**HEAD:** HEAD is a reference to the last commit of the currently checked out branch. If you change to a different branch with a different set of revisions, then HEAD will also change.

**Merge Conflicts:** Merge Conflicts occur when you attempt to merge two branches, but there has been a change in one that invalidates part of the other. The developer must then examine the conflict to manually assess which part of the merge should be kept intact.

**Remote Repository:** A Remote Repository is a shared repository that all members in a team use to exchange their changes to a project. These remotes are often stored on an external code hosting service, such as GitHub.

**Working Directory:** The Working Directory is the directory within which the `git init` command has been run. Any changes made to files within this directory are tracked by the repository and can be staged for commit by adding them to the current index with `git add`.  

**Current Index:** Staging Area for the next commit.


- - - -
## Getting Started
### Initialising a Repository

`git init <directory>` creates an empty Git repository in the specified directory. Specifying no directory parameter creates an empty Git repository in the current directory.

### Cloning an Existing Repository 

`git clone <repo>` clones the specified repository onto the local machine.

### Stage Changes for the Next Commit

`git add <file/directory>` stages the changes in the specified file or directory for the next commit.

`git add .` stages the changes in all tracked files for the next commit.

### Commit the Staged Changes

`git commit —m <message>` saves the staged changes, alongside a descriptive commit message. 

### List Staged, Unstaged and Untracked Files

`git status`  lists the files that are staged, unstaged and untracked, as well as the state of the working tree.


## Logging and Metadata
### View Commit History 

`git log` shows the entire commit history.

`git log -<limit>` shows a commit history, limited to the most recent <limit> commits.

`git log —oneline` shows the entire commit history, with each commit condensed to a single line.

`git log —graph —decorate` draws a text based graph of branches and commits.

### View Changes in Working Directory

`git diff` shows unstaged differences between your working directory and the current index.  

### View Last Person/Revision to Change a Line

`git blame <file>` shows which revision and author last modified each line of a specified file.


## Undoing Mistakes
### Alter a Commit 

`git commit —amend -m <message>` replaces the last commit with the staged changes and the last commit combined. If there are no staged changes then this can be used to amend the commit message.

### Undo a Commit

`git revert <commit>` creates a new commit that undoes all of the changes made in the specified commit, then applies to the current branch.

### Remove a File from Staged Area, but Preserve Changes

`git reset <file>` removes the specified file from the staged area, but does not overwrite any changes to the file. 

### Remove a File from Staged Area, and Overwrite Changes

`git reset —hard <file>` removes the specified file from the staged area, and **overwrites** changes to the file. 

### Reset Entire Staging Area to Match Most Recent Commit, Preserve Changes	

`git reset` resets the entire staging area to match the most recent commit, but does not overwrite any changes made to files.

### Reset Entire Staging Area to Match Most Recent Commit, Overwrite Changes	

`git reset —hard` resets the entire staging area to match the most recent commit, and **overwrites** any changes made to files.	

### Reset Staging Area to a Previous Commit, but Preserve Working Directory Changes

`git reset <commit>` resets the entire staging area to match a specified commit, but does not overwrite any changes made to files.

### Reset Staging Area to a Previous Commit, and Overwrite Working Directory Changes

`git reset —hard <commit>` resets the entire staging area to match a specified commit, and **deletes uncommitted changes** and **all commits after the specified commit**.
 
### Remove Untracked Files from the Working Directory

`git clean -n` shows which files would be removed from the working directory.

`git clean -f` executes the clean and removes untracked files from the working directory.


## Branches
### List Local Branches

`git branch` lists branches of the current repository that exist on your local machine.

### List All Branches (Local and Remote)

`git branch -a` lists all branches of the current repository, both local and remote.

### Create a New Local Branch

`git branch <branch_name>` creates a new local branch called <branch_name>.

`git checkout -b <branch_name>` creates a new local branch called <branch_name> and switches to it.

### Delete a Local Branch

`git branch -d <branch_name>` deletes the local branch called <branch_name>.

### Switch Branch

`git checkout <branch_name>` switches to the specified branch.

### Clone a Remote Branch

`git checkout -b <branch_name> origin/<remote_branch_name>` clones a branch from a remote repository onto your local machine and switches to it. 

### Delete a Remote Branch

`git push origin —delete <branch_name>` deletes a branch from a remote repository.

### Merge a Branch into the Active Branch

`git merge <branch_name>` merges <branch_name> into the current branch.

### Rebase the Current Branch 

`git rebase <base>` rebases the current branch onto <base>. This means if you are working on a direct branch of `Master` and `Master` changes, you can take your branch’s changes and reapply them on top of the new changes to `Master`.

`git rebase -i <base>` interactively rebases the current branch onto <base>. Allows commands to be entered to specify how each commit will be transferred onto the new base.


## Remote Repositories
### Add a New Remote Repository

`git remote add <name> <URL>` connects the current local repository to an existing remote repository. Once added, <name> can be used as a shortcut for <URL> in other commands.

### Retrieve a Specific Branch from a Remote Repository

`git fetch <remote> <branch_name>` fetches the latest version of a specific branch from a remote repository. If <branch_name> is not specified, fetches all remote branches.

### Fetch Latest Changes from a Remote Repository and Merge into Local Copy

`git pull <remote> <branch_name>` retrieves the remote repository’s copy of the specified branch and immediately merges it into the local copy. If no branch is specified, pulls and merges the latest copy of the current branch.

### Fetch Latest Changes from a Remote Repository and Rebase it into Local Copy

`git pull —rebase <remote> <branch_name>`retrieves the remote repository’s copy of the specified branch and rebases it into the local copy. If no branch is specified, pulls and rebases the latest copy of the current branch.

### Push Latest Local Commits on a Branch to a Remote Repository

`git push <remote> <branch>` pushes the current branch and its files/commits to the specified remote branch. If the specified remote branch does not exist, creates it. 

### Push Latest Local Commits on All Branches to a Remote Repository

`git push <remote> —all` pushes all of your local branches to the specified remote repository.


## Misc. Commands
### Update Local List of Remote Branches

`git remote update origin —prune`  fetches and updates remote branches for all remotes.

### Save Local Changes and Clean Working Directory

`git stash` stores the current changes in the working directory, and reverts working directory to match the `HEAD` commit. 

`git stash pop` reapplies the changes stored in the initial `stash` and applies them on top of the current working tree state.

`git stash clear`  removes all stored stashed entries.

`git stash show -p` shows the changes recorded in the stored stash entries in a `diff` format.

`git stash branch <branchname>`  creates and checks out a new branch containing the commit at which the stash was originally created, and applies the stored stash on top.
