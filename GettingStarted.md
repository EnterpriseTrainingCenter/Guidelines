# Getting Started as a Contributor

There are a lot of guides on the Internet that will show different aspects of what is described here, but this article will focus on a simple way to get started using the workflow we use for courses.

## Table of Contents

* [Create free GitHub account](#create-free-github-account)
* [Install Visual Studio Code](#install-visual-studio-code)
* [Install the markdownlint extension](#install-the-markdownlint-extension)
* [Install Git](#install-git)
* [Configure Git](#configure-git)
* [Clone repository from GitHub](#clone-repository-from-github)
* [Forking a repository on GitHub](#forking-a-repository-on-github)
* [Adding the fork as a remote in the local repository](#adding-the-fork-as-a-remote-in-the-local-repository)
* [Making changes and pushing them to the fork](#making-changes-and-pushing-them-to-the-fork)
* [Make changes to an existing pull request of yours](#make-changes-to-an-existing-pull-request-of-yours)
* [Switch between local working branches](#switch-between-local-working-branches)
* [Delete a branch](#delete-a-branch)

## Create free GitHub account

Create a free GitHub account by browsing to [GitHub][1] and clicking on the **Sign up** button.

Although enabling 2-factor authentication on your GitHub account is not required to contribute, it is recommended.

## Install Visual Studio Code

Although there are many PowerShell editors available and everyone has their own preference, most of the processes described here assume the use of Visual Studio Code.

To install Visual Studio code visit the official site [code.visualstudio.com][2].

## Install the markdownlint extension

Although the markdownlint extension is optional, it is recommended to avoid some common formatting issues.

````shell
code --install-extension DavidAnson.vscode-markdownlint
````

## Install Git

Download and install Git for Windows from the official site [git-scm.com][3].

The installation is straightforward using a wizard type of installation. Normally all defaults values suggested by the wizard can be used unless your environment need something special. There is one exception and that is that it might suit you better to use Visual Studio Code as the default editor for Git instead of Vim.

## Configure Git

Now you need to setup your name and e-mail in the global settings. This is used when you commit and push changes to a repository.

````shell
git config --global user.name "Your Name"
git config --global user.email "your@emailaddress.com"
````

## Clone repository from GitHub

To clone a repository from GitHub, using your web browser, navigate to the repository, go to the **Code** page. Then, on the right-hand top, click the **Code** button, and copy the URL of the repository to the clipboard.

In Visual Studio Code, open the command palette by clicking **View**, **Command Palette...** in the menu, or press SHIFT+CTRL+P or F1. In the Command Palette, search for the command **Git: Clone** and execute it by pressing ENTER.

The Command Palette, will ask for the URL of the repository to clone. Paste the URL you copied before and press ENTER.

Then, Visual Studio will ask for the location on your computer, where to store the cloned repository. Select the parent folder for the cloned repository. Visual Studio Code will automatically create a subfolder for the cloned repository.

Finally, Visual Studio Code will ask you to open the cloned repository. Click **Yes** to open it.

## Forking a repository on GitHub

To send changes from your local repository you first fork the upstream repository, because all changes must first be pushed to a working branch in your fork before sending in a pull request. To learn more about forks read the article [Forking Projects][4].

To fork an upstream repository, e.g. the course sw2019-1, browse to the same URL used when cloning, e.g. https://github.com/EnterpriseTrainingCenter/sW2019-1.

To the right of the page you will find a button named **Fork**. Click that and GitHub will create a fork (repository) in your own GitHub account.

## Adding the fork as a remote in the local repository

To be able to send changes (commit in a working branch) to a fork of an upstream repository you need to add a [remote][5] to the local repository.

To add a remote we use a remote name, and the URL to the fork.

The remote name can be whatever we choose, but we assume you want to use ````my```` as the remote name for a remote pointing to your fork.

When GitHub creates a fork of an upstream repo it creates a repository in your GitHub account (means your are the owner of the fork). So the URL to the fork would be https://github.com/{yourGitHubAccountName}/{repositoryName}

To add your fork as an remote, on your forked repository, on the top-right, click the **Code** button, and copy the URL.

In Visual Studio Code, in the open repository, in the Command Palette, exeute **Git: Add Remote...**, paste the copied URL and provide ````my```` as the name of the remote.

Now you have two remote references:

* The remote name **origin** pointing to the *upstream repository*.
* The remote name **my** pointing to your *fork* of the *upstream repository*.

## Making changes and pushing them to the fork

To make changes you should always use another branch than ````main```` to add those changes, let us call it the working branch. A working branch should normally be based on the branch ````main```` so that you can easily work on several other branches during the same period.

> Creating a working branch separate from the default ````main```` branch will allow you to create other working branches off of branch ````main```` later while your other working branches is still open for code reviews.
>
> Limiting your current working branch to a single issue will also both streamline the code review and reduce the possibility of merge conflicts.

To create a new working branch, from the Command Palette, execute **Git: Create Branch From...** and click the branch ````main````. Type a name for the new branch, e. g. the ID of the issue, you are working on.

When you have made changes you need to commit them to your local branch. Below we show how to commit and push using the command line, but it might be easier to commit (using git) from within Visual Studio Code. How to do that can be seen in this video.

[![How to commit changes and push them in Visual Studio Code](https://img.youtube.com/vi/B8RSMBSzFuA/0.jpg)](https://www.youtube.com/watch?v=B8RSMBSzFuA)

## Make changes to an existing pull request of yours

There might be a need to update the pull request, for example due to a review comment, or you realized that you missed something.

If you need to make more changes to a pull request you just push more commits to your working branch as mentioned in [Making changes and pushing them to the fork](#making-changes-and-pushing-them-to-the-fork).

Pushing a new commit to your working branch in your fork will automatically update any pull request that is based on that working branch.

## Switch between local working branches

You can swith between local working branches by executing **Git: Checkout to...** in the Command Palette or by clicking the current branch name in the source control section of the status bar.

## Delete a branch

Once a pull request with your changes have been successfully merged into the upstream repository you can delete the working branch. It is no longer needed at that point, any further work requires a new working branch.

To delete your branch follow these steps:

1. Switch to your local ````main```` branch.This ensures that you aren’t in the branch to be deleted (which isn’t allowed).
2. From the Command Palette, execute Git: **Delete Branch...** and click the branch to delete.
3. Finally, in the Terminal panel, type git push my :branch-name in the command prompt (a space before the colon and no space after it). This will delete the branch on your GitHub fork. Alternatively, it is also possible to delete the branch in your repository online using the web interface.

[1]: https://github.com/
[2]: https://code.visualstudio.com/
[3]: https://git-scm.com/
[4]: https://guides.github.com/activities/forking/
[5]: http://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes