# `rust` and embedded

I wanted to play a bit with rust on the stm32 blue pill kind of board

## Starting point
I started from [this docker image](https://dev.to/dalimay28/using-docker-for-embedded-systems-development-b16), it does not includes rust, but it has the needed toolchain.

The changes I'd to adopt to run it on macOS is to avoid access to USB. I'll use the image just to generate the binaries, then using the stlink utility in macOS to write the binary blob to the device's FLASH:

    $ docker run -it --name docker-arm -p 4444:4444 -v "$(pwd)/app":/usr/src/app docker-arm /bin/bash

At this point I can work on the host machine in the ./app folder.

[To test the toolchain I used a small C program (the classic blink)](https://github.com/trebisky/stm32f103/tree/master/blink1)

Ok, it works.

Time to install rust and test it!

## Installing rust in the docker image
First, install curl in the image:

    sudo apt-get install curl

The install rustup

    curl https://sh.rustup.rs -sSf | sh
    source $HOME/.cargo/env

Then we proceed installing the rust "stuff"

    cargo install xargo

we then need some other libraries using apt-get:

    sudo apt-get install libssl-dev (* maybe not necessary)
    sudo apt-get install libssh-dev (* maybe not necessary)
    sudo apt-get install libgit2-dev (* maybe not necessary)
    sudo apt-get install cmake

Then we install cargo-clone

    cargo install cargo-clone

The we can clone the project

    cargo clone cortex-m-quickstart

So far so good? not really. I managed to compile a sample project just to discover that the built artifact is empty.  
I need to review these instructions as I think there's some better way to build a crosscompile at this stage, without the need of `xargo`.