---
description: 'Created by Alyson La, @realalysonla, updated by Nicole Maneth'
---

# Part 2: Push Your App to Github

### Things you need before you get started <a id="things-you-need-before-you-get-started"></a>

#### Git & GitHub <a id="git--github"></a>

* Check if Git is installed
  * In the terminal type `git --version` \(1.8 or higher preferred\)
* If not, download Git [here](http://git-scm.com/downloads). Then, setup your local Git profile - In the terminal:
  * Type `git config --global user.name "your-name"`
  * Type `git config --global user.email "your-email"`
  * _To check if Git is already config-ed you can type_ `git config --list`
* Create a free [GitHub](https://github.com/) account or login if you already have one

**COACH:** Talk a little about git, version control, and open source

### Push your app to GitHub using the command line <a id="push-your-app-to-github-using-the-command-line"></a>

On your GitHub profile click “new repo” ![screen shot 2013-06-01 at 12 38 50 pm](https://f.cloud.github.com/assets/2623954/595307/eb70c6cc-caf2-11e2-9d2d-60deb31ac049.png) give it a name \(example: rails-girls\), brief description, choose the “public” repo option, and click “create repository”.

In the command line–make sure you `cd` into your railgirls folder–and type:

```text
git init
```

This initializes a git repository in your project

Next check if a file called `README.rdoc` exists in your railsgirls directory:

```text
ls README.rdoc
```

If the file doesn’t exist, create it by typing:

```text
touch README.rdoc
```

**COACH:** Talk a little about README.rdoc

Then type:

```text
git status
```

This will list out all the files in your working directory.

**COACH:** Talk about some of your favorite git commands

Then type:

```text
git add .
```

This adds in all of your files & changes so far to a staging area.

Then type:

```text
git commit -m "first commit"
```

This commits all of your files, adding the message “first commit”

Next type:

```text
git remote add origin https://github.com/username/rails-girls.git
```

_Your GitHub Repository page will list the repository URL, so feel free to copy and paste from there, rather than typing it in manually. You can copy and paste the link from your GitHub repository page by clicking the clipboard icon next to the URL._

This creates a remote, or _connection_, named “origin” pointing at the GitHub repository you just created.

Then type:

```text
git push -u origin master
```

If this command results in an error like `fatal: unable to access  error:1407742E:SSL routines:SSL23_GET_SERVER_HELLO:tlsv1 alert protocol version`then we'll install git directly from the source.  Follow the default settings.  Once the installation finishes, you will have a new program called "Git Bash" on your machine.  You will use this command terminal for interacting with git throughout the tutorial.

This sends your commits in your “master” branch to GitHub

Congratulations your app is on GitHub! Go check it out by going to the same url you used above: https://github.com/username/rails-girls \(without the .git part\)

If you want to continue making changes and pushing them to GitHub you’ll just need to use the following three commands:

```text
git add .
git commit -m "type your commit message here"
git push origin master
```

**COACH:** Talk about what makes a good commit message \(active, descriptive and short\).

### What’s next? <a id="whats-next"></a>

#### Be a Part of the Open Source Community <a id="be-a-part-of-the-open-source-community"></a>

* Follow your fellow Rails Girls & coaches on GitHub
* Star or watch their projects
* [Fork](https://help.github.com/articles/fork-a-repo) a repo, then clone and push changes to your fork. Share the changes with the originator by sending them a [pull request](https://help.github.com/articles/using-pull-requests)!
* Create an issue on a project when you find a bug
* Explore other open source projects - search by programming language or key word

#### Learn more Git <a id="learn-more-git"></a>

* Check out [trygit.org](http://try.github.io/)
* Use a [Git Cheatsheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
* Look up Git Commands at [git-scm.org](http://git-scm.com/)

