tslime.vim
==========

This is a simple vim script to send portions of text from a vim buffer to a
running tmux session.

It is based on
[slime.vim](http://technotales.wordpress.com/2007/10/03/like-slime-for-vim/),
but uses tmux instead of screen. However, unlike tmux, screen doesn't have
a notion of panes. This script has been adapted to take panes into account.

**Note:** If you use a version of tmux earlier than 1.3, you should use the
stable branch. The version available in that branch isn't aware of panes so it
will paste to pane 0 of the window.

Settings
--------

You can tell tslime.vim to use the current session and current window; this
let's you avoid specifying this on every upstart of vim.

```vim
let g:tslime_always_current_session = 1
let g:tslime_always_current_window = 1
```

These are disabled by default, meaning you will have the ability to choose from
every session/window/pane combination.


With some interpreters it is often necessary to input an empty line at the end
of a code block in order to trigger code execution. Such is the case for
instance with the Python interpreter.
You can specify language specific settings with autocommands

```vim
au FileType python let g:tslime_ensure_trailing_newlines = 2
```


Setting Keybindings
-------------------

You can modify default keybindings by setting:

``` vim
" To grab the current method that a cursor is in normal mode
let g:tslime_normal_mapping = '<c-c><c-c>'
" Or a single line at a time
let g:tslime_normal_next    = '<a-enter>'

" To send a selection in visual mode to tmux
let g:tslime_visual_mapping = '<c-c><c-c>'

" To send any text object or motion to tmux from normal mode
let g:tslime_operator       = '<c-c>o'

" Use the following to reset the session, window, and pane info
let g:tslime_vars_mapping   = '<c-c>v'
```
