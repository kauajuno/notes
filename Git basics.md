Git keeps track of the changes you make to a repository, that's basically it. Once you set up git it will monitor all the changes you make to the files in that repository.

To initialize git in some repository, use:

```
git init
```

Now git is already keeping track of the changes being made in that repository, but this isn't so useful if the repository doesn't have any **commits** yet. Commits are almost the whole point of git, they are snapshots of the current state of the files in the repository. To create a commit, we must inform git which modifications we want to include in the new snapshot.

For this example, let's suppose that the initial state of our project looks like this:

```
file1.txt
file2.txt
file3.txt
```

For the first commit, that corresponds to the initial state of a project, let's keep it simple and just add all the files that are currently in the repository. This can be done through the following command:

```
git add .
```

With this, every file that wasn't included in the previous commit (which in this case are all of them as there wasn't any commit before anyway) is included for the next one. Now let's do the commit:

```
git commit -m "first commit"
```

The message could be anything, but "first commit" sounds good for a first commit, right?

Now let's put git to its use. Create a new `file4.txt` in the project and edit something in `file2.txt`. After that, execute:

```
git status
```

To see what is the current status of the files in your project. You'll be able to see that `file2.txt` has changes that are not staged to commit and `file4.txt` not even being tracked.

Just for the sake of learning, let's add `file4.txt` to be staged for the next commit:

```
git add file4.txt
```

Run another `git status`. Git is going to show that `file4.txt` has changes that are already staged for the next commit, while `file2.txt` doesn't. Do the commit:

```
git commit -m "second commit"
```

Now after running another `git status`, you can see the indeed, git didn't include the changes made to `file2.txt` to the previous commit.

Lastly, to see all the commits took until now, run the command:

```
git log
```

It's going to show some information about each commit done in this project, such as author, date and branch. And what is a branch? Well, that's a concern for later. For now, congratulations on concluding the git basics!