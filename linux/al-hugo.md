# Install Hugo on ArchLinux

I use the static website [hugo](http://gohugo.io/) to generate [my blog](http://pietromaggi.com). As I'm setting up my white rabbit (a late 2007 White MacBook) with ArchLinux to play a bit with some _embedded stuff_ I have planned to have it handy to add some note on my blog with my experiments.

## Installing hugo
`hugo` is not included in the pacman repository, but there's an actively developed [AUR package](https://aur.archlinux.org/packages/hugo/).

So, we follow the standard (but new for me) steps to install an AUR on my white rabbit:
- Download the package:

    git clone https://aur.archlinux.org/hugo.git

- build the package

    cd hello
    makepkg -s

- install it

    sudo pacman -U /path/to/pkg.tar.xz

## Testing hugo
At the end we can quickly check if everything is right moving to the root folder of the source of our static website and use `hugo`:

    cd <path-to-source>
    hugo server -Dw

then we can navigate to [localhost:1313](http://localhost:1313) to check if everything is working correctly.  In this way we are rendering all the pages, included the ones marked as draft and, if we modify one of the source pages, the website is regenerated and reloaded.

