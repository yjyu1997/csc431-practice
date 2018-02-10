# csc431: getting started with git 

Verify that you have [git installed][git] before beginning. You can check by
opening the terminal and running `git`. Also be sure that you have created a 
[Github account][github] and that I have added you as a collaborator to the
project. 

Open terminal and find a local directory you want to work in. I usually use `~/Documents`. 
Once there, run:

	$ git clone https://github.com/jerrybonnell/csc431-practice.git 

You now have a clone of this repository in your directory. Descend into this
directory by running: `cd csc431-practice` 

Before we do any work, let's talk a bit about housekeeping. 

## Branching

The main timeline of the code lives on a branch called `master`. It represents the 
official history of our project and, likewise, it is what we consider to be deployable 
code. It is a must that we keep this timeline as clean as possible. If you've ever
worked with version control before, you may have realized that merge conflicts are
an issue if everyone is working on the mainline at the same time.

To remedy this, Git has a concept called branching. Traditionally, every new feature
or bug fix implies a branch. For our project, you will make a new branch every
time you begin work, whether that is writing documentation, code, etc.      

For this dummy repository, we'll create a new branch, do some work, and then push 
the branch onto Github (and, with it, our changes). 

First check which branch we are on: `git branch`. The current branch, i.e. the checked-out branch, 
will be marked with a `*`. If the asterisk is next to something other than `master`, then 
we need to switch back to the master branch.

	$ git checkout master 

*Always make sure you are on master first!* Now we are ready to get any updates. Do the following: 

	$ git pull origin master 

This pulls down changes from the remote/online repository `origin` to the `master` branch on your computer.
Now we are ready to create our new branch. The following command will create the branch with `<branch_name>` 
and automatically switch to it. For this dummy tutorial, we'll use the 
branch name `practice/YOURNAME-branch`, where `YOURNAME` should be substituted with your actual name. 

	$ git checkout -b practice/jerry-branch

# Doing some work

Now we are ready to do some work. We are going to create a new text file and write something to it: 

	$ echo 'banana split!' > jerry.txt (use your name!) 

Let's save the changes we made. We'll stage the work we have done by using the following command: 

	$ git add jerry.txt 

This tells git to stage the file `jerry.txt` for the next commit. Do note that any files that are
not staged (even if they are in your folder!) will not be pushed to Github. To take a look at what
will be updated/deleted/added, you can issue this command:

	$ git status

Now we need to commit these changes, with a message informing what was worked on. 

	$ git commit -m "made file and wrote to it"

This commit saves the changes to our local repository. We need to push this, along with our new branch,
to Github. 

	$ git push origin practice/jerry-branch

Note the similar format to when we issued `git pull`. `origin` is the remote as last time and instead of
the `master` branch we are referring to the branch `practice/jerry-branch`.   

Log in to Github and navigate to this repository. You should see a *Compare & Pull Request* button at the top. 
Click that and submit the pull request. You're done. I'll get an email and approve the changes if it looks
good.

Next time you begin work, issue this following command to make sure your branches are 100% in sync with 
the remote repository. This will delete any local branches that are no longer needed.  

	$ git fetch -p

# Additional Info

I am including some additional incantations for cases that you may find yourself in when working. The first is
pulling down any new updates while you are working on a branch. 

	$ git pull origin master 

After your branch has been merged with master, it isn't necessary to keep the local branch around on your computer. 
Issue this command to delete a specified local branch. In this example, we used `practice/jerry-branch`.

	$ git branch -d practice/jerry-branch

# Resources 

* [Git basics - a general workflow][git-basics]
* [Basic Branching and Merging][git-branching]


[git]: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
[github]: https://github.com/join
[git-basics]: https://gist.github.com/blackfalcon/8428401
[git-branching]: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
