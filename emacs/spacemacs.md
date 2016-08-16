# SpaceMacs 

## What is SpaceMacs?
[SpaceMacs](http://spacemacs.org/) is an emacs opinionated distribution that provides a `vi` friendly experience.

## So what?
I'm a long time emacs used that tried over time to learn `vi` key-bindings, but emacs muscle memory is too strong!

I've read over and over again about the great SpaceMacs distribution and I finally decided to give it a go.

## Some configuration
The install instructions available on the github project are quite easy to follow and allows to setup quickly the system.
The only issue I got was on OSX El Capitan where SpaceMacs was hanging on startup, this seems to be linked to helm and trampoline. I've applied the [suggested workaround](https://github.com/syl20bnr/spacemacs/blob/develop/doc/FAQ.org#why-is-spacemacs-hanging-on-startup), and it worked for me.

Another configuration I've done was to enable the right `option key` to be able to insert special character, this was found in the [OSX layer documentation](http://spacemacs.org/layers/osx/README.html) and was easy as adding:

    (setq-default mac-right-option-modifier nil)

to the configuration.  
Another change was to be able to use `aspell` in place of `ispell`.  
why? I don't really know even seems that `hunspell` is better supporting more dictionary, but I've always used `aspell` and it works.  
Again, another small configuration to instruct emacs on the filename to use (you need to have aspell installed, `brew install aspell` is your friend).

    (setq ispell-program-name "aspell")
 

# Some sparse links/references

  - [github project](https://github.com/syl20bnr/spacemacs/)
  - [Main doc website](http://spacemacs.org/doc/DOCUMENTATION.html)
  - [Layers](http://spacemacs.org/layers/LAYERS.html)
  - [OS X Layer](http://spacemacs.org/layers/osx/README.html)
