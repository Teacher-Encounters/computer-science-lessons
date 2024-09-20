# Git Source Control

You will learn

* How to initialise git repository
* How to commit code
* How to push code to GitHub

Open a terminal, navigate to the directory of your project. For example.

```
cd hello-git
```

Initialise the git project using this command

```
git init
```

If you have files ready to commit, make sure they are saved, and then the following commands will commit all your current changes.

```
git add .
git commit -m 'some sensible comment'
```

If you forget to add a comment to the commit, it will prompt you for one using an arcane text editor called 'vim'....good luck with that.

Lastly, if this is a git project which is hosted on GitHub, and you have setup the remote repository connection, you will need to run this command to push changes.

```
git push
```
