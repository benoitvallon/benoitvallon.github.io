---
layout:     post
title:      "Clean your Git history"
subtitle:   "Make your repositories cleaner and lighter"
date:       2016-03-05 18:31:25
author:     "Benoit VALLON"
header-img: "/img/2016-03-05-clean-your-git-history/post-clean-your-git-history.jpg"
comments:   true
categories: tips
tags:       [git]
---

# Clean your Git history

## Why

When I started my [.dotfiles repo](https://github.com/benoitvallon/dotfiles) it wasn't very obvious to me how to keep my atom packages in it. As a consequence I just decided to push into my [.dotfiles](https://github.com/benoitvallon/dotfiles) everything contained in the `.atom` directory under my user directory on my machine.

It was an easy and no brain solution that worked for a while but my repository and commits became hard to work with because of the numbers of files contained in every commit (+15000 for some commits). So I had to look for a solution to clean the repository retroactively.

## Remove private things (password/keys) from a Git repository

This technique can also be used to remove something that you did push in a repository which shouldn't be there. Passwords and API keys are good clients for those mistakes. Sometimes they are pushed inadvertently and of course you should remove them from your repository right away.

# The steps

## Only remove from the history

This version supposes that you already have `.gitignore` the things that you want to remove from your repository. If you haven't, just go to the next section.

```shell
git filter-branch --tree-filter 'rm -rf atom.symlink/packages' --prune-empty HEAD
git gc
git push origin master --force
```

## Remove from the history and gitignore

Let's suppose you have just pushed a `config.js` containing passwords and you want to remove it.

```shell
git filter-branch --tree-filter 'rm -rf config.js' --prune-empty HEAD

echo config.js >> .gitignore
git add .gitignore
git commit -m 'Remove config.js from Git history'

git gc
git push origin master --force
```

## For the curious, what is `git gc`

If you are like me you are now wondering what is the `git gc` command. Is there a garbage collector in Git? Almost indeed ;)

> git-gc - Cleanup unnecessary files and optimize the local repository.
**From [Git documention](https://git-scm.com/docs/git-gc)**

If you look at the description on the same site you will read that: "Runs a number of housekeeping tasks within the current repository, such as compressing file revisions (to reduce disk space and increase performance) and removing unreachable objects which may have been created from prior invocations of `git add`".

I strongly encourage you to go to [the git documention](https://git-scm.com/docs/git-gc) and read the rest of the description.
