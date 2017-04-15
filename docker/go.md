# Docker container for GoLang programming

With docker we can even have a container devoted to a new programming language, with the environment always updated!

I'm using in this case [mbrt/golang-vim-dev](https://hub.docker.com/r/mbrt/golang-vim-dev/) that includes not only GoLang environment but a full vim setup with plugins to support the development.

# how to use it

  - First, you need to have docker available - easy
  - download the docker image:

        docker pull mbrt/golang-vim-dev

  - move to the folder where you've your go project
  - launch the docker image, passing the current folder as the working one:

        docker run --rm -tiv `pwd`:/go mbrt/golang-vim-dev