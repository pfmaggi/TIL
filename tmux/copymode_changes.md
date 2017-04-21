# tmux v2.4 introduce a new copymode option... that broke my previous setup

This was introduced in [this commit](https://github.com/tmux/tmux/commit/76d6d3641f271be1756e41494960d96714e7ee58) with the note:

## Fundamental change to how copy mode key bindings work:
The vi-copy and emacs-copy mode key tables are gone, and instead copy
mode commands are bound in one of two normal key tables ("copy-mode" or
"copy-mode-vi"). Keys are bound to "send-keys -X copy-mode-command". So:

    bind -temacs-copy C-Up scroll-up
    bind -temacs-copy -R5 WheelUpPane scroll-up

Becomes:

    bind -Tcopy-mode C-Up send -X scroll-up
    bind -Tcopy-mode WheelUpPane send -N5 -X scroll-up

This allows the full command parser and command set to be used - for
example, we can use the normal command prompt for searching, jumping,
and so on instead of a custom one:

    bind -Tcopy-mode C-r command-prompt -p'search up' "send -X search-backward '%%'"

command-prompt also gets a -1 option to only require on key press, which
is needed for jumping.

The plan is to get rid of mode keys entirely, so more to come eventually.

## what changes in my tmux
My previous configuration for copy mode was:

    bind-key -t vi-copy v begin-selection
    bind-key -t vi-copy y copy-pipe "reattach-to-user-namespace pbcopy"

This now becames:

    bind-key -Tcopy-mode-vi 'v' send -X begin-selection
    bind-key -Tcopy-mode-vi 'y' send -X copy-pipe "reattach-to-user-namespace pbcopy"

### Bonus
on MacOS Sierra you can drop reattach-to-user-namespace, but make sure you have the `Applications in terminal may access clipboard` option set when using iTerm2.

    bind-key -Tcopy-mode-vi 'v' send -X begin-selection
    bind-key -Tcopy-mode-vi 'y' send -X copy-selection
