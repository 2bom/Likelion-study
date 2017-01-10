[GIT] How to use git.
==========

# $ git show HEAD
- It's similar with 'git diff'.
- The output of this command will display everything the git log command displays for the HEAD commit, plus all the file changes that were committed.

# $ git checkout HEAD filename.txt
1. Commit.
2. Modify some files.
3. If you want to come back the states of latest commit. Use checkout.

# $ git add filename_1 filename_2

# $ git reset HEAD filename
- We can unstage that file from the staging area using this command.

1. Modify a file and add the file into git(staging).
2. Reset it.
3. Not add the file again.
4. Commit > the file's changing is not included in commit.

\# This command works by using the first 7 characters of the SHA of a previous commit. For example, if the SHA of the previous commit is 5d692065cf51a2f50ea8e7b19b5a7ae512f633ba, use:

    $ git reset 5d69206

# $ git branch
- Check branches of project.

# $ git branch new_branch_name
- Make new branch.

# $ git checkout other_branch
- Switch to the other_branch.

# $ git merge sub_branch
- Merge sub_branch into master branch
- If there are some different parts in states it will crashed.

# $ git branch -d branch_name
- Delete branch.

# $ git clone remote_location clone_name
- Download resources from remote_location into clone_name.

# $ git fetch
- After you cloned science-quizzes, you had to run off to teach a class. Now that you're back at your computer, there's a problem: what if, while you were teaching, Sally changed the science-quizzes Git project in some way. If so, your clone will no longer be up-to-date.

  An easy way to see if changes have been made to the remote and bring the changes down to your local copy is with:

      git fetch

  This command will not merge changes from the remote into your local repository. It brings those changes onto what's called a remote branch. Learn more about how this works below.

# $ git merge origin/master
- In Lesson III, Git Branching we learned how to merge braches. Now we'll use the git merge command to integrate origin/master into your local master branch. The command:

  git merge origin/master

# $ git push origin branch_name_now
- git push origin your_branch_name
  will push your branch up to the remote, origin