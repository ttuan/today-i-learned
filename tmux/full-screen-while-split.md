# Interactive window selector fullscreen while split

**tl;dr:** Zoom the pane with `<prefix>z` or `resize-pane -Z`.

----

The default function for `<prefix>w` is `choose-tree -w` (version 2.6+; in older versions it was `choose-window`).  These are displayed in the `pane`, so zoom the pane to fill the window temporarily.

Combining the two operations on a single keybind should be fairly straightforward.  This can go in your `.tmux.conf` or into a running session (`<prefix>:`):

    # replace default window-chooser: zoom first
    bind-key -T prefix w resize-pane -Z \; choose-tree -w

See [`man tmux`](http://man.openbsd.org/OpenBSD-current/man1/tmux.1#choose-tree):

    choose-tree [-GNsw] [-F format] [-f filter]
                [-O sort-order] [-t target-pane] [template]
        Put a pane into tree mode, where a session, window or pane may
        be chosen interactively from a list. -s starts with sessions
        collapsed and -w with windows collapsed. [...]

Ref: https://unix.stackexchange.com/questions/417853/tmux-interactive-window-selector-fullscreen-while-in-split/417884#417884
