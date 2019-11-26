# all-the-git-commands-that-you-need-to-know
All the Git commands that one may need working with Github

## Git Commands Needed When You Own The Repository

### First create a repository either locally or on Github. Let's take this repository for example.

```bash
git clone https://github.com/BruceWangNo1/all-the-git-commands-that-you-need-to-know.git
```

### Most of time, you will probably be working on master branch. If you want to work on a new branch, let's say, a feature branch. Run:

```bash
git branch <branch_name>
git checkout <branch_name>
```

Or create a Git branch and checkout it in one command instead:

```bash
git checkout -b <branch_name>
```

### After you made changes to some files and want to commit them, I recommend you first check the status by running

```bash
git status
```

You will see files you changed. If there are new files you created that are yet to be committed, you will see them in a different color.

Then you need to add files you've changed and created.

```bash
git add README.md whateverFileThatHaveBeenModifiedAndChanged.txt
```

Commit changes by running

```bash
git commit -m "fixed some errors, added some features and etc."
```

Check out git logs by running

```bash
git log
```

Now the commit is only available in the local repository. Now you may want to push the commit on to the remote Github repository. You can do this by running

```bash
git push -u origin master
```

"origin" is the remote Github repository. And "master" is the branch in which you want commits to be pushed to the origin.

Procedures for other branches work the same.

## Git Commands Needed When You Make Pull Requests to Repositories That You Do Not Own

Let's take github.com/chrislusf/seaweedfs for example. I do not own this repository. And yet I make occasional changes to it, mainly working on AWS S3 Select like feature. 

### Clone seaweedfs repository to a local directry

```bash
cd ~/go/src/github.com/chrislusf/
git clone https://github.com/chrislusf/seaweedfs.git
```

### Fork seaweedfs repository. One click.

Forked seaweedfs is https://github.com/brucewangno1/seaweedfs.git

### Add a new remote origin in ~/go/src/github.com/chrislusf/seaweedfs [2]

```bash
git remote add forked_origin https://github.com/brucewangno1/seaweedfs.git
```

### Everything is the same before you push changes to your Github seaweedfs repository

```bash
git push -u forked_origin master
```

You can now make a pull request through the Github seaweedfs repository page. 

### After the maintainers of seaweedfs approved the pull request, there is a new git log and you need to update you local repository.

```bash
git fetch origin master
git fetch origin s3-select
```

Or you can git rebase [3]

```bash
git checkout master
git rebase origin/master
git checkout s3-select
git rebase origin/s3-select
```

## Reference:
1. [Git – Create New Branch and Checkout – In One Command](https://www.shellhacks.com/git-create-new-branch-and-checkout/)
2. [What to do if I want to make changes to a forked repository only to find that I can not because the forked package import itself](https://stackoverflow.com/questions/51245504/what-to-do-if-i-want-to-make-changes-to-a-forked-repository-only-to-find-that-i)
3. [How do I update a GitHub forked repository?](https://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository)

