# Contributing

Thank you for your interest in contribuing to the courses.

There are several ways you can contribute.

* You can submit an issue to report a bug or to request an improvement.
* You are encouraged to take part in discussions around an issue or pull request.
* You may send in a pull request to improve the courses by adding new content, fixing issues in existing content, or improving the content.

You can read more about the different contributions here:

* [Submit an issue](#submit-an-issue)
* [Resolve an issue](#resolve-an-issue)
* [Create or update a pull request (PR)](#create-or-update-a-pull-request-pr)
* [Resolve merge conflicts](#resolve-merge-conflicts)

## Submit an issue

Submitting an issue to a repository is easy! An issue can be a problem, a solution, or a question.

1. Find the correct repository to submit your issue to.
1. Search open issues to make sure the issue you having have not been submitted by someone else.
1. Open a new issue. If the repository has different issue templates choose the template that best suits the issue you are experiencing.
1. Fill in a short but descriptive issue title. It is recommended to reference the lab, exercise and task, where the issue exists, e. g. Lab 4, Exercise 1, Task 3.
1. Fill in the issue description. If you chose an issue template, follow the guidance in the template text.
1. Submit the issue.

## Resolve an issue

You may work on any issue. Issued labeled with ````good first issue```` has been deemed easy to resolve, although the level of ease can vary from issue to issue.

> If you are new to contributing, then you might want to start with an issue labeled with ````good first issue```` since they are meant for you as new contributor to have something easy from where to start learning the process and workflow.

If you find an issue you would like to resolve then please comment on that issue that you are working on it. This helps others in the community to know that this is being worked on, and keeps other contributors from working on the same issue.

After you have [created a pull request (PR)](#create-or-update-a-pull-request-pr) the PR will be reviewed by the maintainer.

It is rare, but issues can be labeled on hold by the maintainer and these issues should normally not be worked on. The reason why it has been put on hold should have been mentioned as a comment on the issue.

## Create or update a pull request (PR)

If you are new to contributing in general then please read the [Getting Started as a Contributor][1] which will help you set up an environment for developing.

Make sure there is an issue that describes your problem. If there is no issue then please create an issue prior to sending in a PR so that others in the community can discuss. You may create the issue and then directly submit in a PR.

Here is the general process of submitting a PR:

1. Pick out the issue you’d like to work on, see [Fixing an issue](#resolve-an-issue).
1. Post a comment on the issue that you are working on resolving the issue.
1. Create a new working branch based on branch ````main````. [See Making changes and pushing them to the fork][3].
1. Submit a PR targeting the branch ````main```` of the upstream repository.
1. Address any comments brought up by the reviewers by either discussing them or resolve them by pushing changes to your working branch (to the same branch from which the PR was submitted).

### Open a Pull Request

A [pull reqest][2] allows you to submit the changes you made in your working branch of you fork to the upstream repository. There are many ways of opening a pull request, but this document covers two common methods.

#### New pull request from working branch

First browse to your fork. If you just pushed a working branch to you fork GitHub will know that and suggest to send in a pull request, Just click on the button **Compare & pull request**.

If that is not shown, another way to open a PR is to choose the working branch in the list of branches of your fork, let the page refresh, and then click the button **New pull request**.

Once you have used either option to get to the **Open a pull request** page you should make sure you are comparing the right branches. If you used either of the above methods to get to the page the compare should already be correct.

The **base** is the repository and branch the pull request will be targeting (or merged) *into*. Normally this should be the upstream repository, and normally the branch should be master.

The **head** repository is the repository where the working branch exists and the compare is the branch being compared to the **base** branch (*main*).

> If GitHub tells you that your branches cannot automatically be merged, then you probably have merge conflicts. You can resolve these before or after sending in a pull request. The merge conflicts must be resolved before the pull request can be merged, and a reviewer might ask you to resolve them before a review can be done.
>
> For help fixing merge conflicts see the section [Resolve merge conflicts](#resolve-merge-conflicts)

## Resolve merge conflicts

If another pull request is merged while yours is in review, you will need to add those new changes into your working branch before your pull request is allowed to merge. To do this we will ‘rebase’ the branch. This means that the changes you made in your working branch for your pull request will be ‘replayed’ on top of the changes that were recently merged into ````main````, as though you originally created your branch/fork from the current point that the ````main```` branch is at.

*Note: Since it’s replayed you might get conflicts several times during the rebase process (for the first rebase command, and for each following rebase --continue).*

Here are the steps to rebase your branch:

1. Rebase the local ````main```` branch from the base ````main```` branch.
1. Resolve merge conflicts.
1. Rebase your working branch.
1. Resolve merge conflicts.
1. Update your pull request.

### 1. Rebase the local branch ````main```` from the base branch ````main````

In Visual Studio Code, you need to do the following:

1. Open the cloned repository.
1. In the command palette, execute **Git: Checkout to...** or click on the branch name in the source control section of the status bar. Checkout the ````main```` branch.
1. In the command palette, execute **Git: Fetch From All Remotes**.
1. In the command palette, execute **Git: Rebase Branch...** and select ````origin/main````
    > Note: If you used the main branch as your working branch, then at this point you will probably get merge conflicts that need to be resolved. If you used ````main```` as your working branch, you can skip to step 3 to learn how to resolve the merge conflicts.

1. Force push to your fork’s master branch to your forked repository. Make sure there were no conflicts before running this command. From the command palette, execute Git: **Push to..**. and select **My**.

### 2. Rebase your working branch

In Visual Studio Code, you need to do the following.

1. Open the cloned repository.
1. In the command palette, execute **Git: Checkout to...** or click on the branch name in the source control section of the status bar. Checkout your working branch.
1. In the command palette, execute **Git: Rebase Branch...** and select ````my/main````

*NOTE! At this point you will most likely get merge conflicts that need to be resolved before you continue with the next step. See step 3 to learn how to resolve the merge conflicts.*

### 3. Resolve merge conflicts

In Visual Studio code, the files with merge conflicts will be shown in the **Source Control** section of the side bar. Open them from there. Merge conflicts are clearly marked in the source code. You can **Accept Current Change** (your change), **Accept Incoming Change** (the upstream), **Accept Both Changes** or **Compare Changes**. Make your choice to resolve all conflicts ans save the file.

After resolving all conflicts, you have to stage the changes. You can do this using the **Source Control** side bar or by using one of the **Git: Stage** commands from the command palette. Then commit your changes to the local repository.

### 4. Update your pull request

In Visual Studio code, push your branch to your forked repository.

[1]: http://
[2]: https://help.github.com/articles/using-pull-requests/
[3]: GettingStartedAsContributor.md/#make-changes-to-an-existing-pull-request-of-yours
