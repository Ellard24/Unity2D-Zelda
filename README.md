# CS 419 Electric Slide Unity Project

## I. Setup Instructions

**You should only have to do this part once.**

_[Note you can follow these lengthier instructions if you want](http://www.studica.com/blog/how-to-setup-github-with-unity-step-by-step-instructions)_ 

1. Download and install Git LFS (Large File Storage) [here](https://git-lfs.github.com/).
2. Clone the repository using either the GitHub GUI or in Powershell using `git clone git@github.com:mhueter/cs-419-project.git`.
3. Copy all of the project files into the newly-cloned repository folder on your machine.
4. Open the project folder in Unity.
5. In the Unity menu click   `Edit -> Project Settings -> Editor`
6. In the Editor menu, under `Version Control - Mode` select `Visible Meta Files`.
7. In the Editor menu, under `Asset Serialization - Mode` select `Force Text`.

**Set Up Git Config to Prevent Merge Conflicts**

1. In this repository, go into the hidden folder `.git`
2. In that folder, open the `config` file in a text editor.
3. Paste the following:
```git
[merge]
    tool = unityyamlmerge
[mergetool "unityyamlmerge"]
    trustExitCode = false
    keepTemporaries = true
    keepBackup = false
    path = 'C:\\Program Files\\Unity\\Editor\\Data\\Tools\\UnityYAMLMerge.exe'
    cmd = 'C:\\Program Files\\Unity\\Editor\\Data\\Tools\\UnityYAMLMerge.exe' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
```
4. This will instruct your repo to use the unityyamlmerge tool to try and prevet scene merge conflicts.
5. There might be extraneous files after merging such as `.orig`. Feel free to delete them.

_Note: You can edit your [global config](https://stackoverflow.com/questions/2114111/where-does-git-config-global-get-written-to) if you don't feel like changing this every time you have a new Unity project_

[Click Here](http://werc.iridia.fr/Blog/2016/02/11/0/) for more information / instructions on how I figured this out.


**Now You're set up!**

---

## II. Daily Workflow

So we're using [Git LFS](https://www.youtube.com/watch?v=uLR1RNqJ1Mw)! I have an account with them and we can currently store 50 GB, which our project will never get that big.

Basically what this means is that large files are automatically put into the LFS storage so we won't ever hit our GitHub repository size limit.


**Implications:** after you initially copy the project contents from Google Drive, we _never_ have to use it again for version control. We can use git / GitHub from here on out.
I think we should use Google Drive for assets that we want to show each other _before_ they actually get added to our project. Once you want them in the project, just import them normally
and then commit/push the changes.

### Here's a typical workflow for git for our team:

_Note: I'm going to demonstrate command line (CLI) commands but you can do the same things with the [GUI](https://desktop.github.com/)_

#### Before starting project work every day

1. `git checkout master` and `git pull` to get the latest updates.
2. Make sure your work is on a branch. To create a branch `git checkout -b <branch-name>`
3. Check GitHub for [any open Pull Requests](https://github.com/mhueter/cs-419-project/pulls) that other members want.

#### While working on the project
1. While you work, occasionally type `git status` to see what you've changed. If you want to view your changes per file, type `git diff <filename>`.
2. When you get to a point where you've changed stuff and made something work, `git add .` to stage all the changes in your current directory.
3. Right after staging the changes, use `git commit -m "<your-commit-message-here>"`.
4. Committing keeps track of your progress locally.

#### When you finish a project work session
1. `git pull` to get latest updates on your branch (in case someone is also working on it remotely)
2. `git push` to publish your local changes up to GitHub so everyone else can be up-to-date

Feel free to email or message me [hueterm@oregonstate.edu](mailto:hueterm@oregonstate.edu) if you have any git questions!


