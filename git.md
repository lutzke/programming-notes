# git(hub)

notes from the video by Brian Yu: https://www.youtube.com/watch?v=MJUJ4wbFm_A



## what is git?

* what does Git do?
  * keep track of changes to code
  * synchronizing code between different people
    * merge changes different people have made independently to files in the same folder, or even the same file
    * both users then download the merged copy and continue working
  * test changes to code without losing the original
    * easily go back to prior 'snapshots'
    * process:
      * branch code out
      * make changes
      * merge back in once you're satisfied
  * revert back to old versions of code



## commands

* `git clone`
  * `git clone <url>`
  * make a copy of a repository on your local machine, so you can begin making changes
  * a different thing than cloning is forking: a 'fork' creates your own copy of someone else's repository
  * copy the link to the repository's git file, in order to clone it
* `git add`
  * `git add <filename>`
  * after you've cloned a repo to the local machine and you've made changes to a file, you want to tell git to save the changes you've made to that file
    * "git, the next time you track changes to the repo, track changes to this file."
* `git commit`
  * once you've `add`ed all the files you want to commit...
  * `git commit -am "message"`
    * `-am` adds all the files you've changed, and adds a commit message
    * `-m` just adds the message
  * committing basically saves a new version of the repository, while also remembering the old versions
* `git diff`
  * shows lines added/removed (or changed) in files tracked by git, which will be added to the next commit
* `git status`
  * shows you some information about what's happening right now
    * what changes have I made to my local repository?
    * is my branch ahead of `master`?
* `git push`
  * `push` our changes up to the remote repository, so our collaborators (or the world!) can see our changes
  * more explicitly, state the branch, e.g. `git push origin master`
* `git pull`
  * `pull` changes down from the remote repository (if it's ahead of local, i.e. if it contains a more recent version)
  * changes made by another collaborator can be `pulled` onto your local machine



## merge conflicts

* what happens if two people change the same line, and then git tries to merge those changes?
  * merge conflict!
* e.g. pulling down from the repo, but those changes conflict with your local copy
* `<<<<< HEAD` ... `======`
  * everything between these two are your local changes
* `======` ... `>>>>>> 123de456fa789ce0`
  * everything between these two are the conflicting commit
* we can manually resolve the commit by removing those `<<< === >>>` lines, and also removing the conflicting line that we do not wish to keep
* note: git cannot keep track of changes to a line (i.e. insertion/deletion of characters), only insertion/removal of entire lines
  * so, any change to a line will show up as one line removed and one line added; you removed the old one and added the new one



## more commands

* `git log`
  * shows history of commits
    * commit ID
    * author
    * date and time
    * commit message
* `git reset`
  * you made a change locally, but you want to 'undo' it and roll back to a previous version
  * recall that each commit has a hash, or unique identifier
  * `git reset --hard <commit>` will revert to the commit with hash beginning with the characters you enter
    * there is no undoing this! careful!
  * you can also go back to the latest version of the branch:
    * `git reset --hard origin/master`
* `git branch`
  * `git branch` lists existing branches
    * the active branch is bold and green, with an asterisk beside it
  * `git branch <branch_name>` creates a new branch, provided that name is not already taken
  * you want to add a new feature, and test it, without affecting master, which works fine as-iswhen you're ready to make your version with the new feature the main version, you can merge it back into main
  * each branch is a version of the repository
    * each branch has its own commit history and current version
* `git checkout` 
  * `git checkout <branch_name>` 
  * switches you to a different branch
  * **to create a new branch, and then switch to it:**
    * `git checkout -b <branch_name>`
* `git merge`
  * `git merge <branch_name>`
  * merges a branch into the current branch
    * this is subtle: to merge into master, `checkout` master and then `merge` the branch into it. not the other way around!
  * checkout master and then `git merge test` to merge the test branch into master
    * merge conflicts may occur!
  * the old branch is still around. to delete it...:
    * `git branch -D <branch_name>`
      * `-D` for delete



## pull requests

* if you've made a change to a repository in your own fork, you may want to request to merge your changes back into the original version
  * they `pull` your changes into their repo
  * pull requests may be approved or rejected