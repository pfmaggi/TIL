# ArchLinux maintenance

We want to keep our system in order, and the best idea is to keep it up-to-date.

## First - update the installed packages
There's a first step similar to `brew update`, to update all the pacman db

    sudo pacman -Syy

And then there's the actual package update, similar to `brew upgrade --all`

    sudo pacman -Su