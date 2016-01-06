---
title: "Move a Sub-directory in a SVN repository to a Git repository"
date: 2016-01-07 17:24:34
layout: post
author: "k2byew"
---
Got a massive SVN repository with many child projects living inside directories, and it will be nice to move one of these child projects onto its own Git repository.
Commits and comments will be lost if it's a simple copy and past into a new Git repository. To retain it, a merge is required.
This can be easily done with [SmartGit](http://www.syntevo.com/smartgit/).

1. Create a Git repository - this will soon hold the child project
2. Do a initial commit into the Git repository, eg. README.md. This also creates a master branch
3. Clone the partial SVN repository containing the child project, this will create a local git-svn master branch: `master`
4. Add the Git repository as an alternative remote repository onto the SVN repository: Remote->Add
5. Checkout the Git repository's master branch as a local branch, SmartGit will suggest the name: `master-2`
6. Now both the SVN and Git repository have a local branch, git-svn `master` can be merged into the git-master branch: `master-2`
7. Commit and push `master-2` into the Git repository, SVN history will be maintained because of the merge
