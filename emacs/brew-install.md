# Installing emacs on macOS using brew

## Which version?
On top of the standard emacs version, that support macOS. There's a [friendly fork by Mitsuharu Yamamoto](https://bitbucket.org/mituharu/emacs-mac) that add more macOS features that [maybe disabled on the standard port for political reason](http://www.lunaryorn.com/posts/bye-bye-emojis-emacs-hates-macos.html): feature have been disabled in the past because they where not available on GNU based OSes.

## Use Mitsuharu Yamamoto's macOS Emacs port
The easiest way is using [this `brew tap`.](https://github.com/railwaycat/homebrew-emacsmacport)

    $ brew tap railwaycat/emacsmacport

and then

    $ brew install emacs-mac

if you using cask

    brew cask install emacs-mac

To disable this tap, please:

    $ brew untap railwaycat/emacsmacport

## Using the standard version
Personally I prefer to stick with the standard version, not for political reason, but simply because it does what I need, and I like to have a more cross-platform friendly setup.

To install, the best option is to use brew and here, again, we've two options: 
   - using plain vanilla brew
   - using brew cask system (that install prebuilt bynaries)

I prefer to not use brew cask, so that I can build emacs from the HEAD. Anyway, using brew cask is very easy:

    brew cask install emacs

nothing more.

## Using brew to install and setup emacs
To install emacs HEAD on macOS I use this commands:

    brew install emacs --with-cocoa --HEAD
    brew services start emacs
    brew linkapps emacs

That's all, happy coding with `emacs`.