# Doom Emacs

- see "config examples" section below for ideas
- [Doom cheatsheet](https://gist.github.com/hjertnes/9e14416e8962ff5f03c6b9871945b165)
- [Ethan Anderson's guide is a great intro to workflows.... . . . .](https://ethanaa.com/blog/switching-to-doom-emacs/)

## Usage to condition:

- Definitely, definitely use Treemacs (or whatever) 
  - Docs at [Treemacs Github](https://github.com/Alexander-Miller/treemacs) are useful

#### RIGHT CLICK IN `TREEMACS` FOR ALL THE THINGS

- `F9` +treemacs/toggle

#### Keys to Learn

- `C-h v` counsel-describe-variable
- `C-c o p` treemacs/toggle
- `C-(left)` previous-buffer 
- `C-(right)` next-buffer
- `C-x o` ace-window-switch
- TODO: set `(ace-window-display-mode)` (minor mode) on all modes

#### Finding mapped-keys

- `C-h b b` counsel-descbinds
- `C-h b k` which-key-show-keymap
- `C-h b t` which-key-show-top-level

#### ... Looking things up

- `C-c c` +lookup/*
- `C-c c k`+lookup/documentation

#### Undo/Redo

- `C-_` undo 
- `M-_` redo 

`(C/M)-s-space` for me

#### Arrow Keys

- `C-(up/down)` back/forward-paragraph
- `C-M-(up/down)` up/down-list
- `M-(up/down)` drag-stuff-up/down

- `C-(left/right)` left/right-word
- `C-M-(left/right)` backward/forward-sexp
- `M-(left/right)` drag-stuff-left/right
- `C-x (left/right)` previous/next-buffer
- `C-x C-(left/right)` previous/next-buffer 

- `C-c left/right` markdown-promote

##### Unmapped 

- `C-s-(up/down)` 
- `C-s-(left/right)` 

#### Page Up/Down

- `M-(prior/next)` page up/down
- `C-(prior/next)` scroll right/left

#### Home/End

- `C-(home/end)` beginning/end-of-buffer
- `C-M-(home/end)` beginning/end-of-defun
- `M-(home/end)` beginning/end-of-buffer-other-window

#### Mouse Functions

- `C-down-mouse-1` mouse-buffer-menu
- `C-M-down-mouse-1` mouse-drag-region-secondary
- `M-down-mouse-1` mouse-drag-secondary
- `S-down-mouse-1` mouse-appearance-menu


## TODO: Configs

- TODO: map `undo-redo` => `C-?`
- TODO: reuse function keys? (most modkeys are unused)
- TODO: configure a hyper key 
  - but with my current `xkb` config KDE considers this as a Super, even as Mod5)
  - another option is to remap Esc (currently F13) as hyper within emacs

#### [Docker](https://github.com/hlissner/doom-emacs/blob/develop/modules/tools/docker/README.org)

- [Executing Org Blocks with a Docker Container](https://www.reddit.com/r/emacs/comments/c3bz6e/executing_org_blocks_with_a_docker_container/)

#### Python

## Jupyter

- [emacs-jupyter](https://github.com/burakbayramli/emacs-jupyter)

#### Org-Babel

- list of Doom Emacs org modules [HERE](https://github.com/hlissner/doom-emacs/tree/develop/modules/lang/org)


#### Julia

- [ijulia/workflow jupyter via emacs-jupyter](https://discourse.julialang.org/t/jupyter-integration-with-emacs/21496/5)

## Workflow 

- info on this can be found in doom help under [./modules/ui/workspaces](https://github.com/hlissner/doom-emacs/tree/5b3f52f5fb98cc3af653b043d809254cebe04e6a/modules/ui/workspaces)

### Projectile

- Create a `.projectile` folder if the project root doesn't have a `.git` repo.
- This file uses the `.gitignore` format
- create new frame with `make-frame` M-N

Projectile docs:

- [Projects](https://docs.projectile.mx/projectile/projects.html) ... Probably
  something helpful to link to from the Doom Emacs github...
- [Extensions](https://docs.projectile.mx/projectile/extensions.html)
- [Config](https://docs.projectile.mx/projectile/configuration.html) (indexing, etc)  
- [Doom Emacs Workflow](https://noelwelsh.com/posts/2019-01-10-doom-emacs.html)

### Perspective

- manage perspective workspaces with `treemacs-edit-workspaces`

### Sessions

- save with `save-session` C-c w s
- load with `load-session`


## Misc


- Alhassy [Emacs docs](https://github.com/alhassy/emacs.d)

### Dired

- TODO: Show hidden files by default... `C-x M-o` to toggle with `dired-omit-mode` for now



## Config examples:

- Reference [DistroTube's](https://gitlab.com/dwt1/dotfiles) config in `.doom.d`
- Article on [Literate doom-emacs config](https://dotdoom.rgoswami.me/config.html)
- Another article on doom-emacs from [tecosaur](https://tecosaur.github.io/emacs-config/config.html)
- Sacha Chua has a ton of great Emacs links on [her blog](https://sachachua.com/blog/about)
- DFeich [Emacs Course](https://github.com/dfeich/emacs-course)
- DFeich Emacs Course Config [dfeich/emacs-course-and-config](https://github.com/dfeich/emacs-course-and-config/blob/master/init.el)

- [Vianney Lebouteiller](http://irfu.cea.fr/Pisp/vianney.lebouteiller/)'s config: [everything with emacs](http://irfu.cea.fr/Pisp/vianney.lebouteiller/emacs.html)
- [bzg/dotemacs](https://github.com/bzg/dotemacs/blob/master/emacs.org)

#### [Tecosaur](https://tecosaur.github.io)

[Doom Emacs config](https://tecosaur.github.io/emacs-config/config.html)

#### [Guang Tao](https://www.gtrun.org/) 

- Guang Tao's [doom emacs config](https://www.gtrun.org/custom/config.html)
- also has uploaded [xah-fly-keys](http://ergoemacs.org/misc/ergoemacs_vi_mode.html) config
- [Learning List and Agenda](https://www.gtrun.org/custom/), with a list of
  links for [NSM (Network & Security Manager)](https://www.gtrun.org/custom/nsmorg)
