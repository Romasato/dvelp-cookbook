# Git

Our quick guide to working collaboratively with Git and GitHub.


## Contributing to a Repo

* Create a feature branch
* Write good commits
* **Rebase** frequently to incorporate upstream changes
* Create a GitHub pull request to have your branch reviewed
* **Fast-Forward** Merge into master
* Delete local and remote feature branches after merging


## Create a Feature

Create a new, local branch off `master`.

```
git checkout master
git pull
git checkout -b ${branch_name} # (* - check fusnote)
```

N.B. Branch names should be indicative of their function and be hyphenated e.g. `blog-comments`

## Commit

Make frequent, coherent commits that you will thank yourself for later.

```
git status
git add --all
git commit --verbose
```

Use the following template for writing a [good commit message]:

    Present-tense summary under 50 characters

    * More information about commit (under 72 characters).
    * More information about commit (under 72 characters).

    http://project.management-system.com/ticket/123

[good commit message]: https://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message


N.B. Be sure to ignore files that contain sensitive data or that are specific to your local environment or workflow.


## Rebase Upstream

Rebase frequently to incorporate upstream changes.

```
git fetch origin
git rebase origin/master
```


## Request a Review

Before merging, code should be reviewed by another member of the development team. This is where we conduct a systematic evaluation of our source code before it is deployed to reduce risk and remove a single individual being a point of failure.

Every member of the development team should ask for their code to be reviewed for the following reasons:

* Make sure we’re following best practice as a development team
* Error detection
* Vulnerability identification
* Share learnings and techniques within the team

We should always have our code reviewed and approved before deployment. Exceptions should be rare but may be made in circumstances where the change is only trivial (e.g. copy change), or a hot-fix is required and no one else is available to do the review. In these scenarios the code should still be reviewed as soon as possible.

If you've created more than one commit, use interactive rebase to squash them into cohesive commits with good messages:

    git rebase -i origin/master


Share your branch.

    git push origin ${branch_name}

Create a [pull request] on Github and have a team mate review it for you. They will make comments and ask questions via the web interface, or discuss it with you directly. After receiving comments and fix them, be sure that all fixed conversations (reviewer comments) are marked as `resolved conversation`. That small click will save reviewer time.

[pull request]: https://help.github.com/articles/using-pull-requests

## Submit a review

Every member of the development team can ask you to do a review for the [following reasons](#request-a-review). As a reviewer, you will be able to:

* Comment PR: Submit general feedback without explicit approval
* Approve PR: Submit feedback and approve merging these changes
* Request changes: Submit feedback that must be addressed before merging

 In case when several people reviewing same PR and someone request changes - PR can't be merged without approval of that person. If you want to suggest several code changes, just use `comment` instead of `request changes`. That PR can be merged in worth case without your approval.

 N.B. Try to leave all comments if needed in the first review iteration. The best scenario with required changes will be 2 review iterations: 1st for leaving comments, 2nd for check fixes and approve PR.

## Merge

Rebase your branch interactively to squash un-necessary commits like "Remove whitespace".

```
git fetch origin
git rebase -i origin/master
```

Force push your branch. This allows GitHub to automatically close your pull request and mark it as merged when your commit(s) are pushed to `origin/master`. It also makes it possible to [find the pull request] that brought in your changes.

```
git push -f
```

[find the pull request]: http://stackoverflow.com/a/17819027

Double check your commits, scan the files you changed and merge in to master!

```
git log origin/master..${branch-name}
git diff --stat
git checkout master
git merge ${branch_name} --ff-only
git push
```

## Cleanup

Delete your remote feature branch.

```
git push origin --delete ${branch_name}
```

Delete your local feature branch.

```
git branch -d ${branch_name}
```


## Extra, Extra

Git is awesome and we use it alot, so get yourself some [good aliases] to help speed things up!

[good aliases]: https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/git/git.plugin.zsh


******
###### Note that you can set shell variables like this `branch_name=“newsletter-signup”`, and run most of the commands without having to change anything. Here's the list of variables needed:

```
branch_name=“”
repo_name=“”
```
