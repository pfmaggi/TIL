# Playing with dotNet core (on OSX) with a docker container

The basic idea is to play a bit with dotNET core without having to install anything on my own machine. You can get an idea of what I mean watching [this video](https://channel9.msdn.com/Blogs/dotnet/Create-a-Simple-NET-Application-in-Docker).

Microsoft publish a docker image with all the tools to start playing with dotNet core, so, it's simple to just start with that:

    docker run -tiv /<host_folder>:/root/src microsoft/dotnet

in my case this became:

    docker run -tiv /Users/pfmaggi/source/C#/dotNET_core/sample:/root/src microsoft/dotnet

The first time you run this command, docker downloads the image (currently less than 2GB) and then you find yourself in the container image prompt.

Time to go to the folder you created, linked to your host, and start to play:

    cd ~/src
    dotnet new console -o HelloWorld
    cd HelloWorld
    dotnet run

as you can expect you're going to compile and execute the simple console program that is going to print the infamous `Hello World!`.

Next, you can start to edit the project from your host machine, with the preferred editor:

    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello World!");
            }
        }
    }

Modify the command in your editor (as an example, change the string to `"Hello Docker!"`), save, and recompile it from inside the container:

    dotnet run
    $Hello Docker!