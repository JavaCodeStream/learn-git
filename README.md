# learn-git
 Documentation for Git
 Git Commits
=============
-	Git manages many version of projects with commits.
-	Each version of a project is called a commit.
- 	ex: Commits A and B only differ by one file. a small improvement in the product.

-	Is Git Efficient?
	- Each commit is a snapshot of the entire project
	with many small changes of the files, we might think git stores
	many copies of those file on each commit. behind the scenes, Git is very efficiant at storing commits.
	- Each unique file is stored only once.

-	project history
	The collection of commits contain the history of the project.
	- you can review the history
	- you can "undo" a change.

Branches
===========
-	All commits belong to a branch.
	An independent line of development of the project.
-	By default, there us a single branch, called master
-	Creating branches
	- to maintain a stable project at the same tie taht yiu are working on it,
	  create a separate branch.
	- master A -- B
	  featureX A -- B -- C

	- master branch does not know about the featureX branch,
	- the independence of branches allows teams to scale their work.

Merging
==========
-	after a merge, the master branch contains the new feature.

Distributed Version control system
==================================
-	A distributed version control system is a type of version control system.
-	Each user has a local copy of the complete history of the project, which is known as a repository.
-	two users on the team and each has a copy of a remote repository on their local computer.
-	Even though repositories are distributed among team members there's also a single remote repository that is designated as the source of truth or official state of the project. This repository is usually hosted in a data center or in the cloud.
-	user has a local copy of the complete history of the project, they can continue to work while offline. And finally, content is synchronized between repositories by pulling content from or pushing content to a remote repository.

what is Git
===========
-	distributed version control system
-	Open source software
-	A Git repository contains a series of snapshots of the project over time which are known as commits
-	Each commit contains all of the directories and files of the project at the time the snapshot was taken
-	Is Git and GitLab same?
	- Git is the actual technology for source control, and GitLab is the Web UI or interface for Git. There are many others in the market such as Bitbucket, Github etc.
-	Does GitHub own GitLab?
	- Both GitLab (and GitLab.com) and GitHub (and GitHub.com) are products providing Git repository hosting service. GitLab has GitLab CE (open source) and GitLab EE (enterprise), along with GitLab.com (GitLab CE hosted and managed by company). Similarly GitHub has GitHub Enterprise and GitHub.com.
-	Git UI vs Command line
	- free graphical tool called Sourcetree which is a Git client for Windows and the Mac operating system.
	- command line git command (ex: $ git --version)
	- You have the choice of working with Git using a command line interface and, or using a graphical user interface.
-	Git syntax
	- Git is accessed using Git commands. All Git commands start with the word git followed by a space and then the specific command.
	- git [command] [--flags] [arguments]
	- ex: git status --short, git add file1.txt, git help <command name>, (concise help) git <command_name> -h
-	Git account setup username and email
	- for Git It's important to set your correct username and email address in Git. This information is included in any commit that you make to the repository.
	- git config command to specify or read configuration information

Git Locations
==============
- locations related to Git managed content.
- working tree
	- We know that a commit is a single snapshot of the project. The working tree is the location on your computer that contains the directories and files of a single commit. This is where you can view and edit the files of the project, preparing them for the next commit.
	- you check out a commit to place its directories and files into the working tree.
- staging area
	- the staging area, which is also sometimes called the index. The staging area contains a list of files that are planned to be included in the next commit that you make.
	- You prepare the staging area just the way that you want it, so that the next commit is a meaningful snapshot of the project.
	- you use the add command (git add ) to add new or modified files to the staging area.
	- my project/working tree/.git
- local repository
	- The local repository contains all of the commits that have been made for the project.
	- These commits represent the version history of the project.
- project directory
	- The first three locations that we discussed, the working tree, staging area, and local repository are commonly all contained in a single directory on your local computer. This is called the project directory.
	- On your local computer, you have a project directory that contains the working tree as well as a hidden.git directory. The staging area and local repository are located in this directory.
	- Notice that if you delete your project directory, you are also deleting your local repository and staging area, because they are in the.git directory.
- remote repository
	- The remote repository is usually located in a data center or in the cloud.
	- The remote repository contains the commits of the project, and is often considered the source of truth or official state of the project.
	- When the local and remote repositories are synchronized, they contain exactly the same commits.

Create a local repository
==========================
- execute the git init command in an empty directory to initialize or create a repository
- mkdir myproj
  cd myproj
  $ git init
  initialize empty git repository in myproj/.git/
- In your project directory you now have an empty working tree and a hidden dot git directory. The dot git directory contains an empty staging area and a local repository containing no commits
  $ cd .git  

Commit to local repository (working tree --> *git add* --> staging area --> *git commit* --> local repo --> *git push* --> remote repo)
=============================
- git status
	- git status is used to view the status of files in the working tree and staging area.
	- $ git status
- git status with an untracked file.
	- $ touch file.txt
	  $ git status -s (short message)
- git add
	- Git add adds untracked or modified files to the staging area.
	- After executing git add, git again responds with helpful information and advice on what to do next. It shows that there are changes in the staging area that could be committed to the repository.
	- We can execute git add dot(.) to stage both of the files at once without typing their file names.
	$ git add .
- git commit
	- Git commit creates a snapshot of the current project and stores the result as a commit in the local repository.
	- This includes content that you have recently added to the stage,as well as the content that was in the previous commit. The result is a commit that is an entire snapshot of the project.
	- When executing git commit, you can use the -m flag to specify a short commit message.
	$ git commit -m "my first commit"
	- Git status will then show that the working tree and staging area are clean.
- git log
	- git log is used to view the commit history.
	- Add the --oneline option to git log to see a condensed version of the log.
	$ git log --oneline
	$ git log --onelone -2 (view only the two most recent commits.)

Create a remote repository
===========================
- A remote repository is usually a professionally managed repository that is hosted in a data center or in the cloud. It often acts as the central source of truth or official state of the project.
- And it often integrates with other systems like issue trackers and continuous delivery pipelines.
- On-premise options include Bitbucket Server, GitHub Enterprise, as well as some open source on-premise options.
- Because nobody works with the repository locally, there is usually no working tree or staging area on a remote repository. The root directory of a remote repository is similar to the ".git" directory in a local repository
- By convention, remote repository names end with ".git".
- A git hosting provider usually provides a simple interface for creating a remote repository.

Push to remote repository
=============================
- the two fundamental options when starting to work with a remote repository, git clone and git remote add.
	- If you do not have an existing local repository, then you will clone the remote repository, creating a local repository that is associated with the remote repository.
	- If you already have a local repository with commits that you want to push to a remote repository, then you will add the remote repository to your local repository.

- clone a remote repository (local repo <-- *git clone* <-- remote repo)
	- A reference to the remote repository is included in the local repository. This allows you to synchronize the repositories.
	$ git clone <url/to/projectname.git> [localprojectname]
	$ cd projectname
	$ git remote -v (information on the remote repository)
	- The URL that was used to clone the remote repository is shown.
	- Instead of including that URL in git commands, you can use the alias named 'origin'.

- add remote repo to an existing local repo
	- the scenario where you have commits in a local repository and you want to add an association to a remote repository so that you can synchronize them.
	- use the git remote add command to add information about the remote repository to the local repository.
	- git remote add <name> <url>
	$ git remote add origin https://gitlab.com/me/repoA.git

- Git push [git push [-u] <repository> <branch>]
	- writes commits for a branch from the local repository to the remote repository. A successful push synchronizes the branches on the local and remote repositories so that they contain exactly the same commits.
	- serves as a good back up of the local repository.
	$ git push -u origin master (the commits from local master branch are written to remote master branch)
	- git informs you that a tracking relationship has been set up between the local and remote branches because you specified the -u flag.

Git's Graph Model
==================
- Git's Graph model (a Directed Acyclic Graph). A graph model defines the relationship among the commits in a repository.
- A directed graph means that the nodes are connected in a certain direction. The direction is represented using arrows
- Acyclic means no cycles or non-circular.

- Git's DAG
	- Git uses a directed acyclic graph to represent commit history. Commits point to their parent commits.
	- The entire graph contains a project's history.
	- Each node in Git represents a commit. The arrows point at a commit's parents.
	- A branch occurs if a commit has more than one child.
	- A merge occurs when a commit has more than one parent
	- When you use Git clients, you will often see the commit graph. The most recent commit is at the top. Notice that the graph does not have arrows. The arrows are implied by the vertical order of the commits.
	- Using a command line, the Git log command with the graph option shows you a similar diagram.
	$ git log --oneline --graph

	* f1234d(HEAD -> master) Merger branch 'feature1'  
	|\
	| * add feature 1
	| * add feature 1 WIP
	|/
	* add fileA.txt

Git IDs
==========
- Git Object store
	- Internally, Git uses objects to store four types of things.A commit object is a simple text file that contains information such as the commit user information, commit message, a reference to the commit's parent or parents, and a reference to the root tree of the project.
	- That information is all that Git needs to rebuild the full contents of a commit.
	- An annotated tag is a reference to a specific commit.
	- tree- directories and filenames in the project
	- blob - is an object that stores the content of a file that is being managed by Git.
	- typical Git user may only interact with commit objects and tags, letting Git worry about the details related to trees and blobs.
	- Git keeps these objects internally in something called the object store.

- Git ID
	- A Git ID is the name of a Git object.
	- All of the objects stored by Git are named with a 40-character hexadecimal string.
	- These strings are commonly known as Git IDs, but they are also known as object IDs, SHA-1s, hashes and checksums.
	- The 40-character hexadecimal string is the result of a mathematical computation based on the content. Statistically speaking, the SHA-1 value is unique for a given piece of content.
	- SHA-1 values are designed to avalanche. Which means that small changes in the content, leads to a large difference in the SHA-1 values.
	- he Git hash-object command can be used to create SHA-1 values from file contents. You probably won't use this command very often, but Git uses it behind the scenes to create Git IDs.
	$ git hash-object <file>
	- Git hash-object is an example of a low level or plumbing command in Git. You probably will not commonly use plumbing commands, but they're useful for scripting and can be useful for helping you to understand Git.
	- Git sometimes shortens them to the first seven characters. Here you can see that the Git log command with the one line option returns a shortened Git ID for the commit object.
	$ git log
	$ git log --oneline
	$ git show 43fd

Refereces
============
- Commits can be associated with references. A reference is a user-friendly name that points to a commit's SHA-1 value or another reference. If a reference points to another reference, it's called a symbolic reference (HEAD pointing to master)
- We could then call the git show command (shows details related to the commit object.), passing it either the full SHA-1 hash, part of the SHA-1 hash, the master reference, or the HEAD reference, since they all point to the same SHA-1 hash. In this example, we passed the HEAD reference.
 $ git show 435fde0nwqwd823rn0923dkl2n923hdlk2
 $ git show 435fde0
 $ git show HEAD
 $ git show master

- Branch label and HEAD
	- Master is the default name of the main branch in the repository. A branch is an independent path for a set of commits. If we never create a branch in a repository, then by default, all commits are part of the master branch.
	$ git status (informs us that we are currently on the master branch. Any commits that we would make at this point would be to this branch.)
	- A branch label points to the most recent commit in the branch
	- Git implements branch labels as references. These references are stored in the .git directory of the local repository.
	- changing from the project directory to the .git directory.
		- a refs directory. References are stored in this directory. it contains a heads directory and a tags directory. local branch references are in the heads directory.
		- HEAD is implemented in Git as a reference. There's a single HEAD reference in a local repository and it points to the current commit.
	- The master branch label reference points to the most recent commit. The HEAD reference points to the master branch label.

- Tags
	- A tag is a reference attached to a specific commit. It acts as a user-friendly label for the commit.
	- There are two types of tags.
		- The first type is a lightweight tag. This is implemented as a simple reference, much like a branch label or HEAD. It refers to the commit object.
		- The second type of tag is an annotated tag. An annotated tag is similar to a commit object in that it includes metadata such as tag author information, tag date, tag message, and the ID of the commit object referenced by the tag.
	- Annotated tags can be signed and verified with GNU Privacy Guard. This enables someone like a product manager to sign off on a release
	- $ git tag (list all tags in the repository)
	  $ git show v1.0
	- to tag a commit with an annonated tag.
	  $ git tag -a [-m <msg> | -F <file>] <tagname> [<commit>] (<commit> defaults to HEAD)
	  $ git tag -a -m "featureX release" v2.0 development




Branches
==========
- All commits of a project belong to a branch. By default, commit belong to the master branch.
- A branch is a set of commits starting with the most recent commit in the branch and tracing back to the project's first commit.
- Creating a branch only creates one tiny file, a reference.
	- Branches enable experimentation. Team members can isolate their work so that it doesn't impact others until the work is ready.
	- Branches are not aware of other branches.
	- Branches enable multiple team members to concurrently work on the project, without stepping on each other's work. Merging the work together later usually is not too difficult.
- Branches can be short lived or long running.
	- Short lived branches are commonly called topic or feature branches, and usually contain one small change to the project. For example, a topic branch may contain a new feature, a bug fix, a hot fix, a configuration change, or any other change that the project requires. When it's ready, a topic branch is merged into a long running branch.
	- Long running branches like the master branch live longer than topic branches, and can even live for the life of the project.
- Listing of branches
	- Use the git branch command to see a list of branches in the local repository
	  $ git branch
	  - The branch that you are currently on has an asterisk.

- Creating a branch
	- Creating a branch simply creates a new branch label reference. You remain on the original branch
	$ git branch featureX
	$ git branch
	* master
	featureX
	- the HEAD reference still points to the master branch label after creating the feature X branch

- Checkout
	- Check out is usually related to branches and does two main things.
		- First, updating the HEAD reference.
		- second, it updates the working tree with the files from the checked out commit. Once you have checked out a branch, you can work on and commit to the branch.
	- Use the git checkout command to checkout a branch or commit. To checkout a branch, specify a branch name as the argument. To checkout a specific commit, specify it's SHA-1 as an argument.
	$ git checkout <branch_or_commit>
	$ git checkout featureX
	- To create and checkout a branch,
	 - $ git branch featureX
	 - $ git checkout featureX
	 - you've created a feature X branch, but the HEAD reference is still pointing to the master branch label. You can then use the git checkout command to checkout the feature X branch
	- To combine creating and checking out a branch into a single command,
	 - use the -B option with git checkout. This command is only for new branches. It fails if the branch already exists.
	 $ git checkout -b featureX
	 - creating a branch from a commit and checkout.
	 $ git checkout -b featureX 423fd20

- Detached HEAD
	- Usually you checkout a branch, which checks out the commit that the branch label points to, but you also have the option of directly checking out a commit.
	- For example, you might checkout a commit to temporarily view an older version of the project.
	- Checking out a commit rather than a branch leads to a detached HEAD state. This means that instead of the HEAD reference pointing to a branch label, HEAD points directly to the SHA-1 of a commit. So a detached HEAD basically means that the HEAD reference is detached from a branch label. Git will warn you that if you continue you will be in a detached HEAD state.
	- Temporarily viewing the files of a commit while in a detached HEAD state is perfectly fine. However, if you want to work on files of the checked out commit and create new commits, you should create a branch on that commit first.
	- we've checked out commit B, creating a detached HEAD. If we want to create commits based off of commit B, we should first create a feature X branch label, and checkout that branch.

- Deleting a branch label
	- Deleting a branch really just means that you're deleting a branch label. Deleting a branch label normally does not delete any commits, at least not right away.
	- we created a feature X branch. This simply added the feature X label to the latest commit. If we then immediately delete the feature X branch, all that happens is that the feature X label is deleted. This shows how truly lightweight git branches are.
	$ git branch -d featureX
	$ git branch
	- Branch labels are commonly deleted after a topic branch has been merged.

- Danlgling Commits
		- what could happen if you tried deleting a branch label with unmerged work?
		- Let's say that you created a feature X branch off of commits C of the master branch as shown. Then you did some work on feature X and made commit D.. At that point, if you tried to delete the feature X branch label, there would be a problem because commit D does not belong to any other branch. Git normally will not let you do that. Here we tried to delete the feature X branch label. You can see that it responds by saying that the branch is not fully merged. This means that you could lose some commits that would not belong to any branch.
		- specify the D option with git branch to really delete the branch label.
		- The feature X label will be deleted, and you're left with a dangling Committee D. Commit D doesn't belong to any branch. Git will periodically garbage collect, looking for and deleting older dangling commits.
		- Undoing an accidentally branch delete using git reflog
			- Let's say that you accidentally deleted a branch label, and you left some dangling commits.
			- git reflog to undo that. Git reflog is a command that returns a local list of recent HEAD commits. This list is in the local .git directory, but not in the repository. So this only works locally.
			$ git reflog (returns list of the recent commits that HEAD pointed to. )
			- Since that commit object has not been deleted from the object store, we can copy that SHA-1, and call get checkout with the -b option, creating a feature X branch.
			$ git checkout -b featureX 434def0


Merging
=========
- Merging combines the work of independent branches. Usually, this involves merging a topic branch, such as the featureX branch, into what is called a base branch, such as the master branch.
- There are four main types of merges, fast-forward merge, merge commit, squash merge, and rebase.
	- fast-forward merge
		- A fast-forward merge moves the base branch label to the tip of the topic branch.
		- A fast forward merge is possible only if no other commits have been made to the base branch since the topic branch was created.
		- perform a fast-forward merge (we are on featureX branch with HEAD pointing to it and now ready to be merged with master)
		$ git log --oneline --graph --all
		$ git checkout master
		$ git merge featureX (git responds saying its a Fast-Forward megre. by default tries a FF merge unless we tell)
		$ git log --oneline --graph --all
		$ git branch -d featureX (after featureX branch got merged with master, we can thene delete the branch.)
		$ git log --oneline --graph --all\
		- produces a liner commit graph, with fast-forward the resulting commit history is liner.

	- Merge Commits
		- A merge commit combines the work of the tips of the feature and base branches and places the result into a single merge commit
		- Combining the work of multiple commits may result in what's called a merge conflict, if both branches change the same thing in different ways.
		- Performing a merge with a merge commit is basically the same as performing a fast-forward merge. The steps are to check out the base branch, merge the topic branch, and then optionally to delete the topic branch label. Git will automatically attempt to create a merge commit if the merge is not fast forwardable.
		- merge commit has multiple parents.
		$ git checkout master
		$ git merge featureX
		$ git branch -d featureX
		- In some cases, you might have a situation where a merge is fast forwardable, but you would rather have a merge commit. For example, your team's policy might be to always merge feature branches using merge commits. A no fast-forward merge means that a merge commit will always be created, even if the merge is fast-forwardable.
		- merge commit with no fast-forward
			- $ git checkout master
			- $ git merge --no-off featureX
			- $ git branch -d featureX
		- produces a non-liner commit graph

Resolving Merge Conflict
==========================
- what is Merge Conflict?
	- If you perform a merge with a merge commit, Git takes on the responsibility of combining the work of multiple branches and placing the result into a single merge commit.
	- Git will try to do this automatically. However, there are cases where multiple branches make different changes to the same part of a file.
	- In that case, a merge conflict occurs and a person needs to make a decision on how to resolve it.
	- Git also can automatically merge changes to different parts of the same file. In Git, a part of a file is called a hunk.

- Resolving a merge conflict
	- Resolving a merge conflict between two branches involves three commits. master, featureX, base commit
	- Here are the basic steps to resolve a merge conflict.
		- You start out just like with any other merge by checking out the base branch.
		- In this case, the base branch is the master branch.
		- You then attempt to merge the 'feature X' branch into the master branch.
		- Git will inform you that there is a merge conflict, both branches modified the same hunk in fileA.txt in different ways.
		- At this point, Git has modified fileA.txt, showing you exactly where the conflicts are, and has placed the file in your working tree.
		- This is the part that requires human judgment. Once fileA.txt looks the way that you want it to, you stage it so that it becomes part of the merge commit.
		- The key point here is that, when attempting a merge, files with conflicts are modified by Git and placed in the working tree. You need to fix those files before executing a successful merge.
		- You then commit. At this point, the branches are merged.
		- you can then optionally delete the 'feature X' branch label.

		$ git log --oneline --graph --all
		$ git checkout master
		$ git merge featureX (git auto merges with CONFLICT)
		$ git status (says you have unmerged paths and says either resolve the conflict or abort the merge (git merge --abort))
		conflicted hunks are surrounded by conflict markers <<<<<< and >>>>>>>
		fileA.txt
		feature 1
		<<<<<<< HEAD
		feature 3
		==========
		feature 2
		>>>>>>> featureX
		- text from HEAD is between <<<<<< and ========
		- text from the branch to be merged is between ======= and >>>>>>
		- Fix fileA.txt manually.
		$ git add fileA.txt
		$ git commit -m "fixed merge conflict"  (this is the last step which resolved the conflict)
		$ git log --oneline --graph --all
		* (HEAD -> master)
		|\
		| * added feature 2
		* | added feature 3
		|/
		* added feature 1


Tracking Branch
================
- A tracking branch is a local branch that represents a remote branch. Locally, a tracking branch name starts with the remote name then a forward slash and then the branch name.
- If you clone a repository, you'll have a default local tracking branch.
- In this example, the remote repository contains a master branch with three commits. On the remote repository, the head reference points to the default branch that will be checked out when the repository is cloned. In this case, the default branch is named master. When we clone the remote repository, the same three commits, master branch label and head reference will be copied to the local repository. You can see that the commit graph on the remote repository looks exactly like this part of the commit graph locally. After the clone, you will have the master branch checked out. You can see that there is an additional branch label on the local repository. This is the tracking branch. It represents the remote master branch. Origin is a shortcut for the URL to the remote repository, and master is the name of the branch on the remote repository. Because the clone just happened, these two repositories are synchronized.

remote repo:
A <- B <- C
		  |
		  master
		  |
		  HEAD


after clone

         origin/master
		  |
A <- B <- C
		  |
		  master
		  |
		  HEAD

- A tracking branch is related to its associated remote branch and local branch, but they are decoupled.
- Tracking branches updates separately from both the remote branch and the local branch. This is because tracking branches are only updated with network commands like clone, fetch, pull and push. The tracking branch acts as a sort of intermediary between the local and remote branches.

remote repo
A <- B <- C <- D
			   |
			   master
			   |
			   HEAD

local repo

		 origin/master
		  |
A <- B <- C <- E
			   |
			   master
			   |
			   HEAD

- We are now in a state where the three master branch labels point to different commits. The local master branch label points to commit D, the master tracking branch label points to commit C, and the remote master branch label points to commit E.

- Viewing Tracking branch names		  
	- $ git branch --all (shows local and tracking brnch names)
	- You can see here that you are locally on the master branch, and that there is a tracking branch named origin slash master. Git is telling us that we are up to date with the tracking branch, which means that as of the last time that we issued a network command like fetch, we have the latest commit in our local repository, and our local master branch label points to that same commit.
	- The git status command will inform you if the cached tracking branch information is out of sync with your local branch.
	- Use git log with the all option to see a combined log of the commits of all local and tracking branches.
	- Tracking branches are local branches that represent remote branches. They are named <remote>/<branch> for example origin/master. They can become out of sync with local branches, and they are updated with network commands like clone, fetch, pull, and push.

Fetch, Pull and Push
========================
- Network command
	- Most commands in Git only interact with a local repository.
	- However, these four commands, which we will call network commands, communicate with the remote repository.
	- Clone
		- The Clone command copies a remote repository and creates a local repository
	- Fetch
		- The Fetch command retrieves the latest objects and references from the remote repository.
	- Pull
		- The Pull command combines a fetch and a merge.
	- Push
		- The Push command adds new objects and references to the remote repository.

- Fetch (git fetch)
	- The git fetch command retrieves new objects and references from another repository. It mainly updates all of your tracking branch information.
	- Git fetch allows you to download and view changes on the remote repository without having to immediately merge them into your current work.
	$ git log --oneline --graph --all
	$ git fetch (sync the tracking branch)
	$ git log --oneline --graph --all (it will show the tracking branch is ahead of our local master branch)
	- A fetch does not impact the local branch labels. After the fetch, the tracking branch has the same commits as the remote repository's master branch
	- After a fetch, executing git status will inform you if your current local branch is behind the tracking branch.

- Pull (git pull [<repo>] [<branch>])
	- Git pull is a network command that combines git fetch and git merge FETCH_HEAD. FETCH_HEAD is an alias for the tip of the tracking branch.
	- First new objects and references from the remote repository are fetched. If new objects are added to the tracking branch, the tracking branch is merged into the local branch.
	- this is similar to topic branch merging with base branch.
	$ git pull
	- When you execute the git pull command you can specify merging options. The default behavior is the same as the ff option. This well perform a fast-forward merge if possible, otherwise it will create a merge commit.
		- The no-ff option will always pull using a merge commit.
		- The ff-only option only accepts fast-forward merges. It will cancel the merge rather than perform a merge commit. You will then have to decide how to deal with the merge using a separate command.
	GIT PULL WITH UNCOMMITTED CONFLICTING CHANGES
	- What if you have modified fileA.text before executing git pull????
		- executing a pull can update files in your working tree.What if you have modified fileA.text before executing git pull? You wouldn't want git to replace your file. Git detects this situation and will abort the merge rather than letting you lose uncommitted changes. Let's look at an example. First, we modify fileA.text, causing it to have uncommitted changes in the working tree.
		- We then execute git pull. Git fetches some objects, but then when it tries to perform a merge, it notices that you have local changes to a file that it will be replacing. It suggests that you commit or stash your changes before the merge, then it aborts the merge.
		- Stashing is a way to save files modified in the working tree for later access.
		- Git pull only aborts the merge if you have uncommitted changes that would be overwritten by git.
	GIT PULL WITH SAFE UNCOMMITTED CHANGES
	- If you've created a file, that's not going to be replaced by git it lets the merge continue.
	- create a new file.
	- $ git pull

- Push (git push [-u] [<repo>] [<branch>])
	- The git push command is used to add commits to a remote repository.
	- You are pushing the commits of your current branch.
	- You optionally specify the repository you want to push to. This can be a name like origin or URL. You then optionally specify the branch name on the remote that you would like to push to.
	$ git push -u origin/master master
	- A general rule is to fetch or pull before you do a push. You don't have to do this but if you try to push when you don't have the latest remote changes, the push will fail. If you execute a fetch and no objects are retrieved, we can safely push.
	- If you're worried about a pull creating an unwanted merge commit, you can use the ff only option.

Rebase
========
- The Rebasing merge operation rewrite the commit history, so this should be done with caution.
- There is a general rule related to Rebase. Do not rewrite history that has been shared with others.
- If you've been working locally or if you know that no one else has used your branch you can safely Rebase it.
- There are two types of Rebase, a regular Rebase and an interactive Rebase.
- A rebase moves commits to a new parent or base.

before rebase

B <- C
|
A <- D

after rebase

A <- D
	 |
	 B'
	 |
	 C'

If we look at the example above, we have a situation that would typically involve a "merge commit" because commit D has been made after the featureX branch was made. However, there is another option and that is to rebase. What rebasing does is take commit B and C and moves them to a new parent commit D. The result is that you no longer need a merge commit and the merge can be fast forwarded. Because the commits have been moved, they are reapplied on top of the new commit. This creates a different ancestor chain and as a result each of the commit IDs change. So in this example commit B changes to B prime and commit C changes to C prime.

You can see that this is necessary because before the rebase commit B's parent was A. And after the rebase commit B prime's parent is D.

- To help understand how Rebasing works, we can look at DIFFS. We know that each commit contains a snapshot of the complete project, however, it can calculate the difference between two commits. This is known as a diff or a patch.
- We know that each commit contains a snapshot of the complete project, however, it can calculate the difference between two commits. This is known as a diff or a patch. So commit A has the entire project, commit B has the entire project. It can calculate diff AB which is the difference between commits A and B. The same goes for commits B and C. Diff BC is the difference between commits B and C.

A  <- (diff AB) <- B <- (diff BC) <- C

- When rebasing, git applies the diffs to the new parent commit. This is called "reapplying commits."

==================================================================================================================================
