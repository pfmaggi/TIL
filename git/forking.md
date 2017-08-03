# Git Fork on Gihub
One of the core value with github is that the code became social: you fork a project, modify it and push some pull requests.

I'm writing this as a remainder of the different steps.

# Forking
Forking on github is really easy, as a testament of the fact that this is a core value of the platform.
Github has some nice documentation on [Working with Forks](https://help.github.com/articles/working-with-forks/).  
What it's important to remember is to add the upstream repository to your local copy to be able to keep it in sync: [Configuring a remote Fork](https://help.github.com/articles/configuring-a-remote-for-a-fork/)

    $ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git

then you can check that the upstream repository is there:

    $ git remote -v
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (fetch)
    origin    https://github.com/YOUR_USERNAME/YOUR_FORK.git (push)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (fetch)
    upstream  https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git (push)

# Sync your fork
Once you've the upstream repository setup you can fetch the changes from there: [Sync your fork](https://help.github.com/articles/syncing-a-fork/)

    git fetch upstream

Check out local fork master branch:

    git checkout master

Merge the changes in upstream/master into the local changes:

    git merge upstream/master


# Creating Pull Requests from a fork
At the end, the idea to make so easy to work with forks is to make it easy to contribute to other people projects with a pull request: [Creating a pull request from a fork](https://help.github.com/articles/creating-a-pull-request-from-a-fork/). 
