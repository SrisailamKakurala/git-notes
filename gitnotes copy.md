# ====================== Configuration ========================= #

# set a name to identify your commits
git config --global user.name "Your Name"
# get the name of changer
git config --global user.name 

# set an email that will be associated with each committer
git config --global user.email "your.email@example.com"
# get the email of changer

# sets Visual Studio Code as the default editor for Git commit messages
git config --global core.editor "code --wait"
# get the default editor for git commit msgs
git config --global core.editor

# set auto command line coloring for Git for easy reviewing
git config --global color.ui auto










# =================== Status codes/ Stages ===================== #

??: Untracked files (U) - New files not added to the repository git does not know these files existence.
A: Added (A) - New files added to the staging area, git knows these files existence.
C: Commited (C) - Now the git tracks the changes in the file.
M: Modified (M) - Files with changes that are not yet staged.
MM: Modified and staged (M) - Files with changes that are both staged and unstaged.
R: Renamed (R) - Files that have been renamed.
D: Deleted (D) - Files that have been deleted but not yet committed.












# =================== To see the commits ===================== #

git log --oneline 

or 

git log

# Git maintains a log of all references (HEAD changes) called the reflog. You can use the reflog to find the commit you reset from.
git reflog


# ex: 
b6d322f (HEAD -> main) salary3
1f5a810 salary2
131fc0e salary1



# to view commits and merges in a graph
git log --oneline --graph

<!-- flow is from bottom to up -->

*   ea4d421 (HEAD -> main) Merge branch 'feature/navbar'
|\
| * b038581 (feature/navbar) feature one line
* | 2ead91a main one line
|/
* 5230be1 navbar
* 142c8e6 readme
* 7a6f7ae gitignore
* 37626e5 salary3
:









# ================================== To see the status =============================== #

# ye sirf unka stauts btata h jo committed nahi h or commit krne k bd kch changes ki gyi
# U , A , AM, M

git status

or 

git status -s









# ===================== To make a file and write some initial text ==================== #

----- makes README.md and write the following echo text in it
echo "# My First Repo" > README.md 








# ===================== Deleting the commits and moving back =========================== #


# moving the head one/two position(s) back, All changes made in the last commit will be lost, and any uncommitted changes in the working directory will be discarded.
git reset --hard HEAD~1
git reset --hard HEAD~2

# The changes from the last commit are preserved in the working directory and are also staged. This is useful if you want to rewrite the last commit without losing any changes.
git reset --soft HEAD~1


#  The changes from the last commit are preserved in the working directory but are unstaged. This is the default mode if no --soft, --mixed, or --hard option is provided.
git reset --mixed HEAD~1


# This command resets the current branch to the commit with the hash 37626e5 and resets both the staging area and the working directory to match this commit. All changes after this commit will be lost, and any uncommitted changes in the working directory will be discarded.
git reset --hard 37626e5


# it leaves the working directory unchanged. This is equivalent to git reset --mixed 37626e5. The changes after this commit are preserved in the working directory but are unstaged.
git reset 37626e5


# resetting a file
git reset [--soft | --mixed | --hard] <file>

== Moves HEAD: No




mixed --- resets the staging area --- from commit(C) stage to untracked(U) stage
soft --- moves the staging area back --- from commit(C) stage to Added(A) stage
















# ================================ Branching and merging ================================ #


# to see the current branch and all branches
git branch

# to make new branch
git branch <branch name>
ex: 
git branch feature/navbar


# to switch branch - by default we'll be in main branch
git switch feature/navbar

git switch main


# create and switch branch
git switch -C feature/footer


# Merging Techniques: ff merge, three way merge, squash merge, recursive strategy merge, rebase & merge
# in ff merge we'll shift the head pointer to a new commit instead of merging

# Merging the branches - feature/navbar branch with main branch
# to do merging we need TO BE ON THE MAIN BRANCH
# after switching to main, run this command
git merge <branch name>
ex: git merge feature/navbar


# since we merged the navbar ... now we don't need that branch, so we delete it

git branch -d <branch name>

ex: git branch -d feature/navbar










# ====================================== STASHING ============================================ #

# do this before going to another branch without commiting - git memorizez the uncommited changes made 
git stash 
# later when u return to the main file run this command to apply the memorized changes made which are uncommitted
git stash apply
# to delete the uncommited changes in git's memory
git stash clear









# ======================================== Fetching from GitHub ================================ #

git clone [url]

git pull -u origin main

# git fetch downloads changes from a remote repository to your local repository, while git pull downloads changes and immediately merges them into your current branch.


# the non-mergers should use pull to get the merged code.. instead of merging themselves again
git pull 

# the guy who is responsible of merging should use get fetch 
# first fetches, then checks the code, then merges if everything is ok
git fetch


# git pull = git fetch + git Merge
