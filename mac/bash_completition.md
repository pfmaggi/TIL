# Bash Completion on OS X With Brew

Frequently, installing an application with brew, you get a message that: 

    "Completion file is available in /usr/locat/etc/bash_completion.d/<package>"
    
## Sound like a good idea...
So, I can call these file from my `~/.bash_profile` configuration to have a nice
command line completion for the commands I'm more interested... **nice!**

After looking a bit around, I've seen that brew includes a bash_completion package
with additional packages and the note to add this to the `~/.bash_profile` file to
have them enabled in the shell:

```bash
if [ -f $(brew --prefix)/etc/bash_completion ]; then
. $(brew --prefix)/etc/bash_completion
fi
```

[source](http://davidalger.com/development/bash-completion-on-os-x-with-brew/)
