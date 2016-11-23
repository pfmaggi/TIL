#  Sometimes brew decides that you have an old xcode version...

Setting up a new machine I've installed brew, before installing xcode.  No big deal, brew downloaded something and was able to correctly install the packages I needed.

Then I manually installed other apps, included the latest version of xcode... and brew started to complain that I had an old xcode version installed and I needed to upgrade it through the mac appstore...

At the end, I had to use the command line utility `xcode-select` to select the correct xcode (the one I had download from the appstore) to convince brew that I had the latest version.

At least now I know!