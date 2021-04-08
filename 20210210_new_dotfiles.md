# dc.files 2.0

- ideas for configuration from [20210305_garuda-fresh.md]() contained here
- needs to follow the [XDG specs](https://www.freedesktop.org/wiki/Software/)
  (while anticipating the trajectory of XDG Sessions).
  - the XDG software page contains many references to user/gui-level projects,
    providing a partial cover of the underlying space to survey (i.e. links to
    many projects whose configuration conventions would be useful to survey)
  - XDG Sessions in Wayland will allow various window managers to, for KDE
    Activities or XMonad topicspaces, automate config or persist/regenerate the
    state of applications.

## Overview

### Requirements

- integrates nicely with XDG
- templates? meh... i guess?
  - how easy are these to modify? nothing beats `cp a.sh b.sh`
  
#### Gitsubmodules

i would like to have modules for:

- dc.files.kbd
- KDE `$HOME.config` folders
  - other window manager config folders?

### Dotfiles Tools

- Dotter: rust, handlebars templates
- RCM: bash, thoughtbot (templates?)
- chezmoi (no gitmodules)
- Dotdrop: python3, jinja2


## Dotfiles Setup

clone to `$HOME/.dotfiles` or `$HOME/dc.files`?

### integrate a new XDG folder

what would this be like?

### Keyboard


## Desktop & Window Manager Configs


#### 

- `.desktop` files can launch applications from the terminal (with `gtk-launch` or `dex`)

###


