# Disable Middle Button on Linux
On my linux distribution, middle click will paste whatever is in the clipboard. 
This is fine, except middle click usually means clicking the mouse wheel, and people often use
the mouse wheel to scroll in docs. 
If someone scrolls too enthusiastically, they will unintentionally paste some content wherever
the cursor happens to be in the doc - usually not realizing that they did so.

## How to disable the middle-button
I was able to disable the middle-click by adding a custom xorg.conf file.
This file needs to reside in the `/etc/X11/xorg.conf.d` folder. I it does not exist on your linux
machine, you've to create it:

     sudo mkdir /etc/X11/xorg.conf.d

Then create a file with your configuration:

    echo '#Disable Middle Click
    Section "InputClass"
        Identifier   "USB Pointer"
        MatchIsPointer "true"
        Option         "ButtonMapping" "1 0 3 4 5 6 7"
    EndSection
    Section "InputClass"
        Identifier   "TouchPad Pointer"
        MatchIsTouchpad "true"
        Option         "ButtonMapping" "1 0 3 4 5 6 7"
    EndSection' | sudo tee /etc/X11/xorg.conf.d/disable-middle-click.conf

Then you need to restart your X session.

## Troubleshooting
If setting the second button to 0 doesn't properly affect your input, you can do some testing with
`xinput` to see which button to zero out:

    sudo apt install xinput

From my Lenovo X1

    $ xinput
    ⎡ Virtual core pointer                          id=2    [master pointer  (3)]
    ⎜   ↳ Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
    ⎜   ↳ TPPS/2 Elan TrackPoint                    id=13   [slave  pointer  (2)]
    ⎜   ↳ Synaptics TM3289-002                      id=12   [slave  pointer  (2)]
    ⎣ Virtual core keyboard                         id=3    [master keyboard (2)]
        ↳ Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
        ↳ Power Button                              id=6    [slave  keyboard (3)]
        ↳ Video Bus                                 id=7    [slave  keyboard (3)]
        ↳ Sleep Button                              id=8    [slave  keyboard (3)]
        ↳ Integrated Camera: Integrated C           id=9    [slave  keyboard (3)]
        ↳ AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
        ↳ ThinkPad Extra Buttons                    id=11   [slave  keyboard (3)]

You can then check the configuration of one of the item:
    $ xinput get-button-map "TPPS/2 Elan TrackPoint"
    1 0 3 4 5 6 7

The 0 represents turning off the middle button for me.