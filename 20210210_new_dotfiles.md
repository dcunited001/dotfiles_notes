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




## Ideas for KDE

- [KDE Archwiki](https://wiki.archlinux.org/index.php/KDE)

### Surveying the potential endpoints for automation

- find references to key paths like `/etc/*`, `/var/*` and similar by searching
  files like `/var/log/pacman.log`
- the absolute basics of configuration management for specific apps/packages
  should be found in `PKGBUILD` repos  
- gather info from `.desktop` entries (sometimes; useful for chrome shortcuts or
  browser configs). details found on [Desktop Entries](https://wiki.archlinux.org/index.php/Desktop_entries) archwiki
  - `gendesk` can reflect on these `PKGBUILD` files
  - `lsdesktopf` can list/search `.desktop` files
  - icons can be downloaded from [open icon
library](http://openiconlibrary.sourceforge.net/)

### Session/Window Management

#### [KWin/Wayland](https://community.kde.org/KWin/Wayland#Start_a_Plasma_session_on_Wayland)


- [status of Wayland in 2021](https://shibumi.dev/posts/wayland-in-2021/)
- [Developing KWin Wayland](https://www.proli.net/2020/04/03/developing-kwin-wayland/)
- [Wayland 2021 sprint](https://community.kde.org/Sprints/Wayland/2021Virtual)

#### [XDG Autostart](https://wiki.archlinux.org/index.php/XDG_Autostart) can be used
to load `.desktop` definitions (which are apparently brittle). the archwiki
mentions

- application launch scripts can be gradually built up from `.desktop` scripts and other available config entities (hashes merged on top of these can function as launch profiles specific to a `virtual-desktop` or a Plasma `activity`

### [Wayland's `xdg-session-management` gradually replaces `XSMP`]

- [The Mysteryof KDE Activities](https://www.datamation.com/open-source/the-mystery-of-kde-activities/), a 2012 blog referencing the below 2011 blog before interest was lost in activities.........

#### [Beyond Activities: Cross-Device Sessions](https://chani.wordpress.com/2011/08/01/beyond-activities-cross-device-sessions/#more-706): 

2011 Blog: XSMP, KDE Activities, Cross-Device Sessions and the gradual move to [what became] Wayland's XDG Session Manager


### Idempotent approach to KDE activity state (via xmonad-like hooks)

an implementation of the idea would be like an advanced `xmonad` config where: 

- the `managehooks` and other hooks effectively create an **idempotent monad** that can assess the window/process state in an activity (or xmonad topicspace)
- and re/create it from nothing move **or** move it towards an ideal intended state (i.e. x,y,z programs opened with d,f,g args to run a,b,c selenium-style UI interactions to arrive at the targeted topicspace state requirements)


#### requires capabilities of [XMonad with Mutable State](https://wiki.haskell.org/Xmonad/Mutable_state_in_contrib_modules_or_xmonad.hs)
