# VIRTUAL INTELLIGENCE SERVICE (VIS)

Virtual Intelligence Service (VIS) is the fictional organization handling all intelligence for 132nd hosted events.

## Project Structure

The __BASIC__ folder in the root folder contains information relevant for all 132nd operations. This can be items such as ranges, acquisition times etc.

Other folders, like __OPAR__, __OPUF__ etc. are folders containing intelligence for those particular operations. This can be items such as target-folders, maps, target lists etc.

## Contributing

Git is made for collaborative efforts and have been around for decades. It is easy to think of Git as replaced by modern offerings like Dropbox and Google Drive, but those never really offer the control and robustness of Git when multiple people are working together. In particular, when working with non-binary files - git allows changes to only the actual lines of text changed. While not really advisable, this would even allow multiple people to work within the same document - not too different from Google Docs.

If you are already familiar with 'normal' github practices, the guidelines and processes outlined in this section might be familiar to you. If you are new to Git, then please read on for a brief introduction to the basics.

For a more complete introduction, [please see the github guide](https://guides.github.com/introduction/git-handbook/)

### What is 'Git'

A Git _repository_ - or project - is a collection of files and folders associated with a project, along with each file’s revision history. The file history appears as snapshots in time called commits. Commits contain the changes to the files in that particular branch at that time, and in a sense they could be thought of as uploads to a folder. Uploading in Git is called pushing. And you push to something called a 'branch'. Branches are analogous to branches on a tree. Where each of those branches are made up by lines of commits on a timeline. Those branches then merge together and into the main 'trunk' of the tree. We call this the master-branch: This is where the final versions live. The releases.

All work-in-progress or ongoing revisions of files should happen on separate branches. And when ready, merged into the master-branch. This way, anyone pulling (downloading) the files from the master-branch can be sure they only have the latest released versions and not drafts/WIPs.

Merging changes from one branch onto another is done via Pull-requests. When creating a Pull-requests, timestamps and changes to all the new commits are checked against the target branch. If there are detached changes to the same files (or same lines of text in non-binary files) this could lead to a merge conflict. Github is quite good at detecting these, and if one should occur - please ask for help on the wing's Discord.

### Best practices

There are a few tricks and ways to do certain things to minimize risk of merge conflicts and to generally keep a project tide and in good health.

#### 1. Always pull the latest version of the branch before doing any changes

Before branching out or 'starting your day' - always make sure you do a pull against the source branch (most often this will be the master-branch). This way, you minimize the risk of editing a version of the file older than the latest commit to the branch. An example would be if someone else edited the file and committed to the branch after your last commit. Your local file would be outdated, and you would most likely get a merge conflict on your next push.

Command-line command:

```git
git pull
```

#### 3. Learn the basic command-line commands

This can save you a lot of time in the long run. We have already mentioned the command to pull. We will mention a few more:

##### Clone (download) this repository

```git
git clone https://github.com/132nd-vWing/VIS.git
```

This will create a folder called 'VIS' in any folder you are in at the time of writing this command. If you are in C:/users/\<username>/Documents - then you would end up with a folder C:/users/\<username>/Documents/VIS wit all the files from the repo in them.

##### Check-out a branch

```git
git checkout <branch-name>
```

This will switch you from your current branch to another branch. It will also pull all the latest commits from that branch to your local working folder.

##### Add (stage) changes to commit

```git
git add .
```

This will stage all changes. Any changes that are staged will become a part of the next commit.

##### Commit changes to the branch

```git
git commit -m "Some description of what was changed"
```

This will create a commit, with a commit message. When creating the message, imagine yourself looking trough the list of ALL the commits in a years time - trying to find the commit containing the changes you just made. What would be a good, descriptive message helping you finding it faster. You can also reference issues here:

```git
git commit -m "Added missing image. Fixes #6"
```

Github is smart enough to recognize the 'fixes' word and the '#6'. It would now close issue no.6 and if you looked at the issue on Github, you would see it closed - with a reference to this commit! Pretty neat for traceability and control!

##### Push your changes to the repository

```git
git push
```

#### 3. Give branches a descriptive name

When creating new branches, give them a descriptive name. You should be able to decern what that branch is about just by reading its name:

```git
fix/issue-6-missing-image
wip/new-target-list
```

From the names above, we can quickly determine that the first one is a fix for some missing images in an existing document, and even what issue the branch is related to. The second one, we can probably guess that it is a new document about to get added.

While creating new branches might be best done via Github, here are some command-line arguments if you are so inclined. As always, if you run into problems - don't hesitate to ask on the wing Discord server:

```md
# Create a new branch
git branch my-descriptive-branch-name

# Check-out your newly created branch
git checkout my-descriptive-branch-name

# Make some changes to some files...

# Stage the files that where changed
git add .

# or

git add file1.md file2.md etc...

# Create a commit
git commit -m "My descriptive commit message"

# Push your changes to the branch
git push --set-upstream origin my-descriptive-branch-name

```

Note that the push command above is different then the one we learned earlier. It has some extra arguments to it to let git know where exactly we want to push our branch to. When the last step above is done, your new branch should show on github, and anyone doing a `git pull` would now also get this new branch as an option.

#### 4. Ask for help

If you are unsure how to get started, if you are doing the right thing or find anything unclear - don't hesitate to ask. It might save you and everyone else a lot of work. And generally make the experience of contributing a lot more enjoyable.
