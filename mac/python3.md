# Installing and maintaining Python3 on OSX

OS X, at least my El Capitan version, still came with python v2.7.10. I wanted to play a bit with Python and after 8 years of its introduction, make much more sense to start lean with python3.

Luckily brew includes some [detailed instructions](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Homebrew-and-Python.md) on how to setup both environment on top of what is supported by OS X.

## Install python 3
Installing python 3 is no more complicated that typing in the shell:

    brew install python3
    brew linkapps python3

## To update the tools...

Brew takes care of installing Pip, setuptools, and wheel. To update them

    pip3 install --upgrade pip setuptools wheel

## To install Python packages
Now that `pip` is available, just use it!

    pip3 install <package>

They will install into the site-package directory

    /usr/local/lib/python3.5/site-packages


## Setup inside emacs
Surprise, surprise!
Seems that, if I want to use python3 inside emacs, I need to tell him about it...
A couple of customization later (and deleting the anaconda-mode folder in my emacs, prelude based, condig directory) and I'm back enjoying python in emacs!

The actual custom variables:

    (custom-set-variables
        '(python-shell-exec-path (quote ("python3")))
        '(python-shell-interpreter "python3")
    )
