# Git and GitHub Guide

## Overview of Git and GitHub
Git is a distributed version control system designed to track changes in source code during software development. It enables multiple developers to work on the same project simultaneously by using branches and merging changes. Git maintains a complete history of all changes made to a project, allowing developers to revert to previous versions, compare changes, and collaborate without conflicts.

GitHub is a cloud-based platform built on top of Git that provides a web interface for hosting and managing Git repositories. It enhances Git’s capabilities with additional features such as pull requests for code review, issues for tracking tasks and bugs, and project boards for project management. GitHub also supports continuous integration and deployment with GitHub Actions, and it fosters a vibrant community where developers can share, contribute to, and collaborate on projects.
## Key Differences Between Git and GitHub
- **Functionality:**
    - **Git:** A tool for version control, allowing local and distributed management of code changes.
    - **GitHub:** A platform for hosting Git repositories with additional collaboration features and a user-friendly web interface.
- **Usage:**
    - **Git:** Used locally on your computer to manage project history and coordinate work between multiple developers.
    - **GitHub:** Used online to share repositories, collaborate on projects, and utilize enhanced features for project management and workflow automation.
## Version Control System (VCS)
A Version Control System (VCS) is a software tool that helps developers manage changes to source code over time. It keeps track of every modification to the code in a special database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

### Functionalities of a Version Control System (VCS)
- **Tracking Changes:** Records every modification to files, documenting who made changes and why.
- **Collaboration:** Allows multiple developers to work simultaneously on the same project without overwriting each other’s work.
- **Branching and Merging:** Enables the creation of branches to work on new features or fixes independently, and later merging them into the main codebase.
- **Reversion:** Provides the ability to revert files or projects back to a previous state to undo mistakes.
- **History and Audit:** Maintains a comprehensive history of changes, facilitating debugging and accountability.
- **Backup and Restore:** Acts as a backup system by recording all changes, allowing restoration of the project to any previous state.

### Benefits of Using a Version Control System
- **Enhanced Collaboration:** Facilitates teamwork and coordination among multiple developers.
- **Improved Code Quality:** Supports code review processes and the integration of changes, leading to higher quality code.
- **Time Efficiency:** Saves time by enabling quick identification and reversion of problematic changes.
- **Project Management:** Helps manage large projects by keeping track of all changes and ensuring everyone works on the latest version.
- **Risk Mitigation:** Reduces the risk of data loss and makes it easier to recover from mistakes or failures.
- **Audit Trail:** Provides a clear record of changes, which is useful for compliance and accountability purposes.

## Installing Git
To install Git, download the installer for your OS from the Git website or use package managers like apt-get for Linux. Follow on-screen instructions to complete installation. Git will be ready to use from the command line for version control in your projects. Below are the installation steps for Git on Windows, macOS, and Linux, each with their respective links:
- **Windows:** [Download Git for Windows](https://git-scm.com/download/win) and follow the installation instructions.
- **macOS:** [Install Git on macOS](https://git-scm.com/download/mac) using the installer package provided.
- **Linux:** Install Git on Linux via your distribution's package manager or [download directly from Git](https://git-scm.com/download/linux) and compile it from source.

### Checking the Installed Git Version
To verify the version of Git installed on your system, follow these steps:
1. **Open a Terminal Window:**
    - On macOS or Linux, you can use the built-in Terminal application.
    - On Windows, you can use Command Prompt, PowerShell, or Git Bash.
2. **Run the Command:**
    ```sh
    git --version
    ```
This command will display the version of Git currently installed on your system. Git is a stable and reliable software, with breaking changes exceptionally rare.

## Connecting Git to GitHub on Your Local Machine
Here are a few steps for connecting to GitHub after installing Git on your machine locally:
1. **Get a GitHub account:**
    - Sign up for a free GitHub account if you don't already have one.
2. **Set up Git with your user name and email:**
    - Configure Git with your name and email to associate commits with you.
    ```sh
    git config --global user.name "Your name here"
    git config --global user.email "your_email@example.com"
    ```
3. **Set up SSH on your computer:**
    - Generate SSH keys if they do not exist to enable secure communication with GitHub.
    ```sh
    ssh-keygen -t rsa -C "your_email@example.com"
    ```
4. **Copy your public key into your clipboard:**
    - Copy the SSH public key to your clipboard for later use.
    ```sh
    pbcopy < ~/.ssh/id_rsa.pub
    ```
5. **Paste your SSH public key into your GitHub account settings:**
    - Add the copied SSH key to your GitHub account under SSH keys.
    - Go to GitHub Account Settings > SSH Keys > Add SSH Key.
6. **Test your SSH connection:**
    - Verify that your SSH key is properly set up by testing the connection to GitHub.
    ```sh
    ssh -T git@github.com
    ```
    - If it says, "Hi username! You've successfully authenticated, but GitHub does not provide shell access," it worked.

# Terminologies
This portion looks into key terms used in the Git version control system. It defines the meaning of commonly utilized terminologies and terms, providing a solid basis for understanding Git workflows and command syntax.

### 1. Repository
A repository (or "repo") is a directory where your Git projects live. It can be local to a folder on your computer or it can be a storage space on GitHub or another Git host.
* **Example:** Creating a new repository, and it sets up all the necessary files and directories inside a .git folder.
    ````
    git init
    ````
* **Directory Structure (.git):** Contains all the metadata and objects for the repository. Key components include:
    - **objects/:** Stores all the content for your repository (files, commits, trees, etc.) in a compressed format.
    - **refs/:** Contains pointers to commit objects, including branches (refs/heads/) and tags (refs/tags/).
    - **HEAD:** A pointer to the current branch reference, indicating the current commit.
    - **config:** Contains configuration settings for the repository.

### 2. Clone
Cloning creates a copy of an existing repository, including all files, commits, and branches. This is often used to obtain a local copy of a remote repository.
* **Example:** Cloning a remote repository.
    ````
    git clone <https://github.com/username/repository.git>
    ````

### 3. Branch
A branch is a separate line of development that allows you to work on different features or bug fixes independently. The default branch in Git is typically called main.

* **Example:** Create and switch to new branch from base branch
    * Creating a new branch
        ````
        git branch <new-branch>
        ````
    * Switching to a new branch
        ````
        git checkout <new-branch>
        ````
        **OR**

    * Create and switch to a new branch in a single command
        ````
        git checkout -b <new-branch>
        ````

### 4. Commit
A commit is a snapshot of your repository at a specific point in time, accompanied by a message describing the changes. Commits are used to record the history of your project.

* **Example:** Making a commit.
    ````
    git add .
    git commit -m "Write a Commit Message"
    ````

### 5. Push
Pushing sends your commits from your local repository to a remote repository or a branch, making your changes available to others. This is typically done to share updates with a team.

* **Example:** Pushing changes to a remote repository or a branch.
    * Pushing changes to a remote repository.
        ````
        git push origin 
        ````
    * Pushing changes to a specific branch of remote repository.
        ````
        git push origin <branch-name>
        ````

### 6. Merge
Merging combines the changes from one branch into another branch, integrating the histories of both branches. This is often used to incorporate feature branches into the main branch.

* **Example:** Merging a branch A into the branch B.
    ````
    git checkout <branch-A>
    git merge <branch-B>
    ````

### 7. Fetch
Fetching downloads commits, files, and refs from a remote repository into your local repository or a branch without merging them. This allows you to review changes before integrating them. 

* **Example:** Fetching changes.
    * Fetching changes from a remote repository.
        ````
        git fetch origin 
        ````
    * Fetching changes from a specific branch of that repository.
        ````
        git fetch origin <branch-name>
        ````

### 8. Pull
Pulling fetches the latest changes from a remote repository or a remote branch and merges them into your local repository or local branch. This is a combination of `git fetch` and `git merge`.

* **Example:** Pulling fetches.
    * Pulling from a remote repository.
        ````
        git pull origin 
        ````
    * Pulling from a specific branch of that repository.
        ````
        git pull origin <branch-name>
        ````

### 9. Revert
Revert creates a new commit that undoes the changes made by an earlier commit, while preserving the commit history.

* **Example:** Reverting a commit.
    ````
    git revert <commit-hash>
    ````

### 10. Log
Log shows the commit history for the repository, allowing you to see the sequence of commits along with their messages and authors.

* **Example:** Viewing commit history.
    ````
    git log
    ````

### 11. Checkout
Checking out a branch or a commit switches the working directory to the specified branch or commit. This changes the files in your working directory to match those in the checked-out branch or commit.
* **Example:** Checking out.
    * Checking out a specific commit.
        ````
        git checkout <commit-hash>
        ````
    * Checking out a specific branch.
        ````
        git checkout <branch-name>
        ````

### 12. Remote
A remote is a common repository that all team members use to exchange their changes, stored on a server. It allows collaboration by sharing code and updates.

* **Example :** Adding a remote repository.
    ````
    git remote add origin <https://github.com/username/repository.git>
    ````

### 13. Rebase
Rebasing re-applies commits from one branch on top of another base tip, resulting in a linear project history. This can be used to streamline a series of commits.
* **Example :** Rebasing the current branch onto `branch`.
    ````
    git checkout <new-branch>
    git rebase <branch>
    ````

### 14. Stash
Stashing temporarily shelves (or "stashes") changes you’ve made to your working directory so you can work on something else. This is useful when you need to switch branches without committing incomplete work.
* **Example :** 
   * Stashing changes saves your current changes and cleans your working directory.
        ````
        git stash
        ````
    * Switch to the other branch, make your fix, commit it, and switch back to your original branch
    * Restore your saved changes.
        ````
        git stash pop
        ````
    * or if you want to apply without removing from stash
        ````
        git stash apply
        ````
    * If you used `git stash apply` and no longer need the stash, you can remove it manually:
        ````
        git stash drop
        ````

### 15. Reset
Reset resets the current branch to a specified state, which can be used to unstage changes or remove commits from the history.
* **Example :** Here are the three types explained.
    * `--soft`: Moves the HEAD and updates the index (staging area) but does not touch your working directory. Changes from the undone commits remain staged for a new commit.
        ````
        git reset --soft HEAD~<n>
        ````
    * `--mixed` (default): Moves the HEAD and updates the index but keeps your working directory as is. Changes from the undone commits will be left in your working directory but are unstaged.
        ````
        git reset HEAD~<n>
        ````
    * `--hard`: Moves the HEAD, updates the index, and also updates your working directory to match the specified commit. This discards all changes from the undone commits and is destructive.
        ````
        git reset --hard HEAD~<n>
        ````
    *  Here you can reset specific commit hash.
        ````
        git reset <commit-hash>
        ````
    

`HEAD` refers to the current branch pointer in Git. `HEAD~<n>` specifies the commit that is `<n>` commits before the current HEAD.


* Use Cases
    * **Soft Reset:** Useful for undoing recent commits while retaining the changes in the staging area.
    * **Mixed Reset:** Useful for un-staging recent changes without losing your work.
    * **Hard Reset:** Used when you want to discard recent commits and changes entirely.









## Example Workflow
Here’s an example workflow that includes all the steps mentioned above:

1. **Initialize a new repository:**
    ```sh
    git init
    ```

2. **Make changes to your files.**

3. **Stage the changes:**
    ```sh
    git add .
    ```

4. **Commit the changes:**
    ```sh
    git commit -m "Initial commit"
    ```

5. **Add a remote repository (if you have one):**
    ```sh
    git remote add origin <remote-repository-URL>
    ```

6. **Push the changes to the remote repository:**
    ```sh
    git push -u origin master
    ```
