---
layout: post
title:      "How to make a pull request to an open-source GitHub repo"
date:       2019-09-27 15:23:43 +0000
permalink:  how_to_make_a_pull_request_to_an_open-source_github_repo
---


If you want to contribute to an open-source project on GitHub, you'll first want to **fork** the repository by clicking the `Fork` icon at the top right of the repo's page:

![](https://i.ibb.co/Gf6gJMT/Screen-Shot-2019-09-27-at-10-52-02-AM.png)

This create a forked copy of the master repository on your GitHub account. You'll then want to locally **clone** your copy.

From your forked repository's page, click the green `Clone or download` button, then copy the clone link (choose SSH or HTTPS, depending on which works best with your setup — [check out GitHub's help docs for more information](https://help.github.com/en/articles/which-remote-url-should-i-use)).

![](https://i.ibb.co/8Y3zPX3/Screen-Shot-2019-09-27-at-10-55-58-AM.png)

In your terminal, run `git clone [paste in the clone link that you copied from the forked repo]`.

## Create a new branch
It's important to create a new **branch** of the repo after forking and cloning so that any work that you do on the code will be isolated from the master branch.

To create a new branch, make sure that you're working in the directory of the repository in your terminal (you can `cd` into the repo after cloning it), then run `git branch [name of your new branch`.

Make the name of your new branch descriptive — let other coders who are working on the repository know what you're working on with your branch.

After creating the branch, it's important to run `git checkout [your new branch's name]` to switch into it. Then all of the work you do will happen on that branch.

## Submitting a pull request
Make any changes or additions to the code, then **add** those changes to the branch you're working in using `git add` and **commit** the changes with a descriptive commit message with `git commit -m`.

**Push** your changes to GitHub using `git push origin [name of the branch you're working in]`. At this point, when you visit your forked copy of the repo on your GitHub account, there will be a green `Compare & pull request` button. Click that button, and a window will open that will allow you to submit a **pull request** to the owner of the master repo.

Add a title to your pull request and helpful details that outline the changes or additions that you made to the code, and click `Create pull request`.

That's it! The owner of the repository can now review your pull request and merge your changes and additions to the code into the master branch.


