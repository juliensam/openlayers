---
layout: master
title: Git Forking
---

# Creating a fork #

The [central OpenLayers repository](central) is the canonical repository from which OpenLayers releases are generated.  To contribute to OpenLayers, you'll create a fork of this repository (see the [GitHub docs](http://help.github.com/forking/) for details on forks).  To keep your repository updated, you can pull in changes from this central (or upstream) repository.

The easiest way to create a fork of the central repository is to click on the "fork" button on the project page for the [central repository](central).  After finding the button and clicking on it, follow the directions given there.

[central]: http://github.com/openlayers/openlayers "OpenLayers Central Repository"

Now, you'll want to create a local clone of your newly created fork.  These examples assume your user name is "joedeveloper".  Change the syntax depending on your GitHub user name.

    git clone git@github.com:joedeveloper/openlayers myol3

This creates a local clone of your forked repository in a directory named "myol3".  At this point, you can change into the "myol3" directory and start working with your fork.

    cd myol3

# Configuring remotes #

In git, a "remote" refers to a tracked repository.  Your local repository can be configured to track any number of remote repositories.

The `git remote` command can be used to list your currently configured remotes.

    git remote -v

Calling `git remote -v` lists all configured remotes with verbose output.  Below is a sample 

    origin	git@github.com:joedeveloper/openlayers.git (fetch)
    origin	git@github.com:joedeveloper/openlayers.git (push)

From the perspective of this local repository, the "origin" is the repository you created when you forked the central repository.  It is useful to create a reference to the central repository as well.  Here we'll refer to this remote repository with the name "upstream".  So, "origin" will be your fork and "upstream" will be the central repository.

    git remote add upstream git://github.com/openlayers/openlayers.git

Running the `git remote add` command configures your local repository to track the remote central repository using the name "upstream".

At this point, you should see two remotes configured when you list all remotes.

    git remote -v

The output should look something like the following:

    origin	git@github.com:joedeveloper/openlayers.git (fetch)
    origin	git@github.com:joedeveloper/openlayers.git (push)
    upstream	git://github.com/openlayers/openlayers.git (fetch)
    upstream	git://github.com/openlayers/openlayers.git (push)

# Pulling in upstream changes #

Before making changes to your fork, you'll want to make sure you're updated with the latest changes from the upstream central repository.  Assuming you are working on your "master" branch and you have no local changes, you can use `git pull` to bring in changes from the master branch of the upstream repository.

    git pull upstream master

You'll only want to call `git pull upstream master` if you are working on your "master" branch and you have no local changes.