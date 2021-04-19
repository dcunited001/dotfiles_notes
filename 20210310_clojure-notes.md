# Clojure

## Install & Config

- installed clojure/lein via `pacman`
- found [An Animated Intro to
  Clojure](https://ourcodestories.com/markm208/Playlist/4) on Our Code Stories
  (written in Clojure, afaik)

## Clojure deps.edn

- see [this guide](https://tomekw.com/clojure-deps-edn-a-basic-guide/)


### Practicalli `clojure-deps-edn`

`git clone git@github.com:dcunited001/clojure-deps-edn $HOME/.config/.clojure`

(from readme) How to run common tasks for Clojure development.
* Built-in tasks require no additional configuration.
* User aliases should be added to `~/.clojure/deps.edn`.
* Project aliases should be added to the individual project deps.edn file (or may be part of a template).
* User/Project alias can be defined in both user and project deps.edn files (typically added to project deps.edn for external running such as Continuous Integration)

#### Create project (clojure exec)  `clojure -X:project/new :template app :name practicalli/my-app` User alias

#### Run REPL (rebel readline) `clojure -M:repl/rebel` User alias

#### Run REPL (rebel and nrepl) `clojure -M:repl/rebel-nrepl` User alias

#### Run REPL (rebel and reveal data visualization)  `clojure -M:repl/rebel-reveal` User alias

#### Download dependencies  `clojure -Spath` or `clojure -P`  *plus optional aliases* Built-in

#### Find libraries (mvn & git)  `clojure -M:project/find-deps library-name` User alias

#### Generate image of project dependency graph   `clojure -X:project/graph-deps` User alias

#### Check for new dependency versions  `clojure -M:project/outdated` User alias

#### Run tests  `clojure -M:test/runner` User/Project alias

#### Run the project   `clojure -M -m domain.main-namespace` Built-in

#### [Run the project](https://youtu.be/u5VoFpsntXc?t=2166) `clojure -X:project/run` Project alias

#### Package library `clojure -X:project/jar` User/Project alias

#### Deploy library locally `clojure -X:deps mvn-install` Built-in

#### Package application `clojure -X:project/uberjar` User/Project alias

### System

- bash/fish?
- clojurescript?

### Doom/Emacs

- [setup LSP and clojure-mode](https://www.ianjones.us/clojure-development-in-emacs)
  - configuring LSP requires `pamac install clojure-lsp-bin`


### VSCode

- Calva (runs on CIDER)

# Clojurescript


### [Shadow CLJS](https://github.com/thheller/shadow-cljs)

good examples/demos of app stacks & boilerplate (below in "web/examples")

  - [condiuit Demo](https://jacekschae.github.io/conduit-re-frame-demo/
  - [conduit Demo with re-frame-10x](https://jacekschae.github.io/conduit-re-frame-10x-demo/
  - [Kareoke Demo](https://karaoke-player.netlify.app/songs/Rolling%20Stones-all%20over%20now%20rolling%20stones.html)


### React & Reagent

- react dev tools (firefox)


see [reagent-template](https://github.com/reagent-project/reagent-template) for
info on creating projects from the template:

```
lein new reagent <name> +spec +cider
```


## Todo App:

#### Initial Setup

- `npx create-reagent-app todo` which creates the reagent app
- `cd todo && npm install`
- `npm install --save-dev todomvc-app-css` 
- then ` cp node_modules/todomvc-app-css/index.css public/css/style.css`

#### Follow git commits for further tasks

## CLJS Karaoke App

clone, install requirements (above) and run with `npx shadow-cljs watch app`

the `app` target is defined in `./shadow-cljs.edn`
 


# Git Clones

with: 
