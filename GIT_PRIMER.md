# Git Primer

This primer is taken from the [github git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf).

# **Setup**

## Configuring user information used across all local repositories

set a name that is identifiable for credit when review version history

```shell
git config --global user.name “[firstname lastname]”
```

set an email address that will be associated with each history marker

```shell
git config --global user.email “[valid-email]”
```

set automatic command line coloring for Git for easy reviewing

```shell
git config --global color.ui auto
```

# **Setup & Init**

## Configuring user information, initializing and cloning repositories

initialize an existing directory as a Git repository

```shell
git init
```

retrieve an entire repository from a hosted location via URL

```shell
git clone [url]
```

# **Stage & Snapshot**

## Working with snapshots and the Git staging area

show modified files in working directory, staged for your next commit

```shell
git status
```

add a file as it looks now to your next commit (stage)

```shell
git add [file]
```

unstage a file while retaining the changes in working directory

```shell
git reset [file]
```

diff of what is changed but not staged

```shell
git diff
```

diff of what is staged but not yet commited

```shell
git diff --staged
```

commit your staged content as a new commit snapshot

```shell
git commit -m “[descriptive message]”
```

# **Branch & Merge**

## Isolating work in branches, changing context, and integrating changes

list your branches. a * will appear next to the currently active branch

```shell
git branch
```

create a new branch at the current commit

```shell
git branch [branch-name]
```

switch to another branch and check it out into your working directory

```shell
git checkout
```

merge the specified branch’s history into the current one

```shell
git merge [branch]
```

show all commits in the current branch’s history

```shell
git log
```

# **Inspect & Compare**

## Examining logs, diffs and object information

show the commit history for the currently active branch

```shell
git log
```

show the commits on branchA that are not on branchB

```shell
git log branchB..branchA
```

show the commits that changed file, even across renames

```shell
git log --follow [file]
```

show the diff of what is in branchA that is not in branchB

```shell
git diff branchB...branchA
```

show any object in Git in human-readable format

```shell
git show [SHA]
```

# **Tracking Path Changes**

## Versioning file removes and path changes

delete the file from project and stage the removal for commit

```shell
git rm [file]
```

change an existing file path and stage the move

```shell
git mv [existing-path] [new-path]
```

show all commit logs with indication of any paths that moved

```shell
git log --stat -M
```

# **Ignoring Patterns**

## Preventing unintentional staging or commiting of files

Save a file with desired paterns as .gitignore with either direct string matches or wildcard globs.

```shell
logs/

*.notes

pattern*/
```

system wide ignore patern for all local repositories

```shell
git config --global core.excludesfile [file]
```


# **Share & Update**

## Retrieving updates from another repository and updating local repos

add a git URL as an alias

```shell
git remote add [alias] [url]
```

fetch down all the branches from that Git remote

```shell
git fetch [alias]
```

merge a remote branch into your current branch to bring it up to date

```shell
git merge [alias]/[branch]
```

Transmit local branch commits to the remote repository branch

```shell
git push [alias] [branch]
```

fetch and merge any commits from the tracking remote branch

```shell
git pull
```

# **Rewrite History**

## Rewriting branches, updating commits and clearing history

apply any commits of current branch ahead of specified one

```shell
git rebase [branch]
```

clear staging area, rewrite working tree from specified commit

```shell
git reset --hard [commit]
Temporarily store modified, tracked files in order to change branches

```

## **TEMPORARY COMMITS**

Save modified and staged changes

```shell
git stash
```

list stack-order of stashed file changes

```shell
git stash list
```

write working from top of stash stack

```shell
git stash pop
```

discard the changes from top of stash stack

```shell
git stash drop
```

# **Version Control Best Practices**
This is copied from from [Git-tower's git cheet sheet](https://www.git-tower.com/blog/git-cheat-sheet/)

## Commit related changes 
A commit should be a wrapper for related 
changes. For example, fixing two different 
bugs should produce two separate commits. 
Small commits make it easier for other de-
velopers to understand the changes and roll 
them back if something went wrong. 
With tools like the staging area and the abi-
lity to stage only parts of a file, Git makes it 
easy to create very granular commits. 
## Commit often 
Committing often keeps your commits small 
and, again, helps you commit only related 
changes. Moreover, it allows you to share 
your code more frequently with others. That 
way it's easier for everyone to integrate 
changes regularly and avoid having merge 
conflicts. Having few large commits and sha-
ring them rarely, in contrast, makes it hard to 
solve conflicts. 
## Do not commit half-done work 
You should only commit code when its com-
pleted. This doesn't mean you have 
to complete a whole, large feature before 
committing. Quite the contrary: split the 
feature's implementation into logical chunks 
and remember to commit early and often. 
But don't commit just to have something 
in the repository before leaving the office 
at the end of the day. If you're tempted 
to commit just because you need a clean 
working copy (to check out a branch, pull in 
changes, etc.) consider using Git's **Stash** 
feature instead. 
## Test code before you commit 
Resist the temptation to commit some-
thing that you "think, is completed.Test it 
thoroughly to make sure it really is comple-
ted and has no side effects (as far as one can 
tell). While committing half-baked things 
in your local repository only requires you 
to forgive yourself, having your code tested 
is even more important when it comes to 
pushing/sharing your code with others. 
## Version control is not a backup System 
Having your files backed up on a remote 
server is a nice side effect of having a version 
control system. But you should not use your 
VCS like it was a backup system. When doing 
version control, you should pay attention to 
committing semantically (see **related chan-
ges**) - you shouldn't just cram in files. 
## Write good commit messages 
Begin your message with a short summary of 
your changes (up to 50 characters as a gui-
deline). Separate it from the following body 
by including a blank line. The body of your 
message should provide detailed answers to 
the following questions: 
> What was the motivation for the change? 

> How does it differ from the previous 
implementation? 

Use the imperative, present tense (**change**, 
not **changed** or **changes**) to be consis-
tent with generated messages from com-
mands like git merge. 
## Use branches 
Branching is one of Git's most powerful fea-
tures - and this is not by accident: quick and 
easy branching was a central requirement 
from day one. Branches are the perfect tool 
to help you avoid mixing up different lines 
of development You should use branches 
extensively in your development workflows: 
for new features, bug fixes, ideas... 
## Agree on a workflow 
Git lets you pick from a lot of different work-
flows: long-running branches, topic bran-
ches, merge or rebase, git-flow... Which one 
you choose depends on a couple of factors: 
your project, your overall development and 
deployment workflows and (maybe most 
importantly) on your and your teammates' 
personal preferences. However you choose 
to work, just make sure to agree on a com-
mon workflow that everyone follows. 
## Help & documentation 
Get help on the command line 
S glt help <command> 
FREE ONLINE RESOURCES 
http://wvvw.git-tower.com/learn 
http://rogerdudler.github.io/git-guide/ 
http://www.git-scm.org/ 