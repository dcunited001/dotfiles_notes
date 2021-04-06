# Clojure

```
sudo pacman -Syu clojure leiningen
```

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

```shell
### node/npm
pacman -Syu nodejs npm

### configure for npm
npm config set prefix $HOME/.npm-packages

### shadow-cljs (file watch, tasks, builds, updates to repl/browser)
npm install -g shadow-cljs

### react tooling
npm install -g react-cli

### to install dependencies for headless testing
npm install -g karma-cli
npm install karma karma-cljs-test karma-chrome-launcher --save-dev

### for node-sass
pacman -Syu python2
npm install -g node-sass

### to run tests
lein doo chrome-headless test once
```

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

```shell
cat README.md | grep -e "- CLONE: " | sed "s/^- CLONE: //g" | xargs -n2 git clone`
```


### Finance Examples

- CLONE: https://github.com/daveduthie/mortgage-calc finance/mortgage-reagent2
- CLONE: https://github.com/Romacoding/Mortgage-Calculator finance/mortgage-reagent
- CLONE: https://github.com/yangaxnkohla/mortgage-calculator finance/mortgage-calculator
- CLONE: https://github.com/clojure-finance/clojure-backtesting finance/clojure-backtesting

### Statistics

- CLONE: https://github.com/ptaoussanis/tukey dsci/tukey
- CLONE: https://github.com/bfollek/baseball dsci/baseball
- CLONE: https://github.com/uncomplicate/bayadera dsci/bayadera

### Science

- CLONE: https://github.com/intermine/bluegenes dsci/bluegenes
- CLONE: https://github.com/saidone75/wa-tor dsci/wa-tor-population-sim

### Libraries

- CLONE: https://github.com/pbaille/question-mark lib/question-mark
- CLONE: https://github.com/defold/defold lib/defold

### Clojure

- CLONE: https://github.com/clojure/clojure tools/clojure

### Tools

- CLONE: https://github.com/technomancy tools/leiningen
- CLONE: https://github.com/BetterThanTomorrow/calva tools/calva
- CLONE: https://github.com/clojure-emacs/orchard tools/orchard
- CLONE: https://github.com/seancorfield/dot-clojure tools/dot-clojure
- CLONE: https://github.com/practicalli/clojure-deps-edn tools/clojure-deps-edn
- CLONE: https://github.com/thheller/shadow-cljs tools/shadow-cljs

### Learning

- CLONE: https://github.com/exercism learn/exercise-clojure
- CLONE: https://github.com/functional-koans/clojure-koans learn/clojure-koans

### Luminus

- CLONE: https://github.com/luminus-framework/luminus-template web/luminus-template
- CLONE: https://github.com/luminus-framework/guestbook web/luminus-guestbook
- CLONE: https://github.com/luminus-framework/examples web/luminus-examples
- CLONE: https://github.com/magnars/confair web/confair

### Web Examples


#### `shadow-cljs` examples

- CLONE: https://github.com/shadow-cljs/quickstart-browser web/examples/quickstart-browser
- CLONE: https://github.com/mhuebert/shadow-re-frame web/examples/shadow-re-frame
- CLONE: https://github.com/Day8/re-frame web/examples/re-frame
- CLONE: https://github.com/Day8/re-frame-trace web/examples/re-frame-trace
- CLONE: https://github.com/jacekschae/shadow-reagent web/examples/shadow-reagent
- CLONE: https://github.com/jacekschae/shadow-firebase web/examples/shadow-firebase
- CLONE: https://github.com/ahonn/shadow-electorn-starter web/examples/shadow-electorn-starter
- CLONE: (https://github.com/jacekschae/conduit web/examples/conduit
- CLONE: https://github.com/quangv/shadow-re-frame-simple-example web/examples/shadow-re-frame-simple-example
- CLONE: https://github.com/teawaterwire/cryptotwittos web/examples/cryptotwittos
- CLONE: https://github.com/loganpowell/shadow-proto-starter web/examples/shadow-proto-starter
- CLONE: https://github.com/manuel-uberti/boodle web/examples/boodle
- CLONE: https://github.com/iku000888/shadow-cljs-kitchen-async-puppeteer web/examples/shadow-cljs-kitchen-async-puppeteer
- CLONE: https://github.com/baskeboler/cljs-karaoke-client web/examples/cljs-karaoke-client
- CLONE: https://github.com/flexsurfer/ClojureRNProject web/examples/ClojureRNProject
- CLONE: https://github.com/jacekschae/shadow-cljs-devcards web/examples/shadow-cljs-devcards
- CLONE: https://github.com/jacekschae/shadow-cljs-tailwindcss web/examples/shadow-cljs-tailwindcss

#### Reagent

- CLONE: https://github.com/reagent-project/reagent-utils reagent/reagent-utils
- CLONE: https://github.com/reagent-project/reagent-forms reagent/reagent-forms
- CLONE: https://github.com/reagent-project/reagent-cookbook reagent/reagent-cookbook
- CLONE: https://github.com/reagent-project/reagent-template reagent/reagent-template
- CLONE: https://github.com/reagent-project/reagent reagent/reagent
- CLONE: https://github.com/reagent-project/reagent-frontend-template reagent/reagent-frontend-template

#### React-vis Examples

- CLONE: https://github.com/chrismurrph/fulcro-react-vis web/examples/fulcro-react-vis
- CLONE: https://github.com/mooreryan/cljs_reagent_react_vis_blog_materials templates/cljs-react-vis

#### Bioinformatics

- CLONE: https://github.com/mooreryan/clj-parse-fasta bio/clj-parse-fasta
- CLONE: https://github.com/mooreryan/derep bio/derep

