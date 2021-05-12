

## Links: 

#### Systems

- [AUR](https://wiki.archlinux.org/index.php/Arch_User_Repository)
- [ABS](https://wiki.archlinux.org/index.php/Arch_Build_System#Preserve_modified_packages)

#### Tools

- [makepkg](https://wiki.archlinux.org/index.php/Makepkg)
  - [A Brief Tour of the Makepkg Process](https://gist.github.com/Earnestly/bebad057f40a662b5cc3)
- [pacman](https://wiki.archlinux.org/index.php/pacman#Configuration)

#### Processes

- [building in a clean chroot](https://wiki.archlinux.org/index.php/DeveloperWiki:Building_in_a_clean_chroot)
- [pacman tips & tricks](https://wiki.archlinux.org/index.php/Pacman/Tips_and_tricks)
- [PKGBUILD](https://wiki.archlinux.org/index.php/PKGBUILD#validpgpkeys)
- [.SRCINFO](https://wiki.archlinux.org/index.php/.SRCINFO)

#### Configs

- [makepkg.conf](https://jlk.fjfi.cvut.cz/arch/manpages/man/makepkg.conf.5)
- [pacman.conf](https://jlk.fjfi.cvut.cz/arch/manpages/man/pacman.conf.5)

#### Blogs

- [configuring the AUR with Aurutils](https://gpgpu.io/2019/11/21/configuring-the-aur-with-aurutils/)
- [two PGP Keyrings for Package Management in Arch Linux](http://allanmcrae.com/2015/01/two-pgp-keyrings-for-package-management-in-arch-linux/)

## Process for a New Custom Repo

#### Vars & Locations

```bash
export aurhome="/home/aur-repos"
export repo="reponame"
export repo_install="/usr/local/$repo"
export repo_home="$aurhome/$repo"
export repo_log="$repo_home/pacman.$repo.log"
export repo_conf="$repo_home/pacman.$repo.conf"
export repo_makepkg="$repo_home/makepkg.$repo.conf"
```

#### Global Setup (run once)

- setup repo bins container: `sudo install -d /usr/local/repos`

#### Permissions after a repo setup

- run after setup: `sudo chown root:repo -R /usr/local/repos`

#### Tasks

- bash script: render to and chmod u+x `$repo_home/_pac-$repo.sh`

```bash
#!/bin/bash
pacman --config {{ repo.home }}/pacman.{{ repo.name }}.conf "$@"
```

- dir for bins: `sudo install -d /usr/local/$repo`
- path: `echo "export PATH=$repo_install/usr/bin:$PATH" >> ~/.zshrc`
- repo home: `mkdir $repo_home`
- pacman db: `install -d $repo_home/db`
- config file: `touch $repo_home/pacman.$repo.conf`
- makepkg conf: `touch $repo_home/makepkg.$repo.conf`
- makepkg logs: `install -d $repo_home/log`
- repo log: `touch $repo_home/log/pacman.$repo.log`
- make repo: `repo-add $repo_home/$repo.db.tar.gz`
- make pacman cache: `sudo install -d /var/cache/pacman/$repo`
- mount: `sudo mount --bind $repo_home /var/cache/pacman/$repo`
- mount options: `sudo mount -o remount,bind,ro $repo_home /var/cache/pacman/$repo`
- sync pacman: `sudo pacman --config $repo-home/pacman.$repo.conf -Syu`
- or sync with `sudo _pac-docker -Syu`
- clone the makepkg config: `sudo cp /etc/makepkg.conf $repo_home`

udpate fstab with:

```bash
export add_to_fstab=`cat /etc/mtab | grep -e $repo`

# check fstab (careful...)
echo $add_to_fstab
```

#### Pacman Config File

```jinja2
[options]
RootDir = /home/aur-repos/{{ repo.name }}
DBPath = /home/aur-repos/{{ repo.name }}/db
CacheDir = /var/cache/pacman/{{ repo.name }}
CleanMethod = KeepCurrent
LogFile = {{ repo.home }}/pacman.{{ repo.name }}.log
Architecture = auto

SigLevel    = Required TrustedOnly DatabaseOptional
LocalFileSigLevel = Optional
#RemoteFileSigLevel = Required

# Defaults
#GPGDir = /etc/pacman.d/gnupg/
#HookDir = /etc/pacman.d/hooks/
#HoldPkg = ...
#XferCommand = /usr/bin/curl -L -C - -f -o %o %u
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u

# Per-Repo
#IgnorePkg   = go
#IgnoreGroup =
#NoUpgrade   =
#NoExtract   =

[{{ repo.name }}]
SigLevel = PackageRequired TrustedOnly
Include = /etc/pacman.d/mirrorlist
Server = file://{{ repo.home }}
```

#### Makepkg Config File

```jinja2
PKGDEST="{{ repo.install }}"
MAKEFLAGS="-j4"
LOGDEST="{{ repo.home }}/makepkglogs"

# sometimes, a package will need to be signed to be trusted by Pacman
# BUILDENV=(!distcc color !ccache check sign)
```


## Building emacs with `makepkg` 

specifically, to get debugging of native codA

- this requires having a copy of the source code, so the 
*.c files can be accessed. this needs to be the same SHA
what was built (ideally.... to match the *.map files, 
if they are source maps?)

#### pamac didn't work no matter what i tried.

- pamac uses spawnv (not spawnve) to spawn makepkg AFAIK.
  - so it doesn't pass env vars to `makepkg`
- There are several invocations to makepkg 
  - in alpm tools, database.vala and transaction.vala
  - It builds packages with `makepkg -cCi`
- strangely, there are no references to `pacman` in `pamac`...?
  - is that correct?
- anyways, even when changing `SRCDEST` in /etc/makepkg.conf,
  - that shit didn't work for pamac
  - it runs as a service with elevated priviledges and can't 
    write to /usr/src
  - pamac also fails when writing to /home/dc/local/src

#### building with makepkg

download [emacs-native-comp-git](https://aur.archlinux.org/emacs-native-comp-git.git) to
/data/dev/abs/emacs-native-comp-git. 

print .SRCINFO with `makepkg --printsrcinfo`. this is what 
pamac digests (with pipes?) and it's likely that other 
cmdline & gui tools do this as well.

build with `makepkg -cCfLi`:

- -L logs
- -i installs the completed package
- -f overwrites existing built package
- -cC clean for fresh builds in case of failure

#### getting makepkg to build optimized binaries

## OBS Repo

#### To search for all `jack-git` dependencies and install (if on AUR)

```bash
aur depends -a jack-git | xargs aur sync --config=/home/aur-repos/obs/pacman.obs.conf --makepkg-conf=/home/aur-repos/obs/makepkg.obs.conf
```

otherwise, will need to use `provides` or `provides-with` options in
`pacman` when installing, after buildling/installing those packages in
that repo.

## Docker Repo

after configuring as above

- in pacman.conf: `IgnorePkg: go go-md2man kubectl`

#### Build and install Go

```bash
echo "GO111MODULE: $GO111MODULE" >> /home/aur-repos/docker/makepkglogs/docker-man.log
echo "GOPATH: $GOPATH" >> /home/aur-repos/docker/makepkglogs/docker-man.log
echo `which go-md2man` >> /home/aur-repos/docker/makepkglogs/docker-man.log
echo `go env` >> /home/aur-repos/docker/makepkglogs/docker-man.log
```

...

#### Install Go Tools 

- [An Overview of Go's Tooling](https://www.alexedwards.net/blog/an-overview-of-go-tooling#installing-tooling)

```bash
# standard go tools
go get golang.org/x/tools/cmd/{benchcmp,bundle,callgraph,compilebench,cover,digraph,eg,fiximports,go-contrib-init,godex,godoc,goimports,gomvpkg,gorename,gotype,goyacc,guru,html2article,present,ssadump,stringer,toolstash}

# kubernetes-bin

# cni-plugins-bin

# kubectl-grace-git

# kubeadm-bin

# kubelet-bin

# for minikube-bin
go get github.com/cpuguy83/go-md2man

# for kubectl-bin


```

#### Build AUR Repos

`aur sync --config $repo_conf --makepkg-conf $repo_makepkg -u docker-bin`


#### Sync with Pacman (to install)


## Pacman Examples

#### [Preserve modified packages](https://wiki.archlinux.org/index.php/Arch_Build_System#Preserve_modified_packages)

(From ABS Docs) Into the `PKGBUILD`, add the package to a group called modified `groups=('modified')`

Then in `/etc/pacman.conf`, add that group to `IgnoreGroup = modified`

## AUR Examples

(cobbled together from man pages and wikis, listed here for reference since i have yet to configure colors in man-pages)

### Arch User Repository

#### Run actions on the dependency tree of an AUR package:

```bash
echo foo | aur depends | while read -r pkg; do ... done
```

#### Build plasma-desktop-git and its dependencies with systemd-nspawn(1):

```bash
aur sync -c plasma-desktop-git
```

#### Update all AUR packages in a single local repository:

```bash
aur sync -u
```

#### Check foreign packages for AUR updates:

```bash
pacman -Qm | aur vercmp
```

#### Check the custom repository for AUR updates:

```bash
aur repo -d custom --list | aur vercmp
```

#### If pacman.conf only contains one local repository, the above may be shortened to:

```bash
aur repo --upgrades
```

### Arch User Repository - advanced usage

#### Print packages from the custom repository that are unavailable in the AUR:

```bash
grep -Fxvf <(aur pkglist) <(pacman -Slq custom)
```

#### As above, but for orphaned packages:

```bash
pacman -Slq custom | aur rpc -t info | jq -r '.[].results[] | select(.Maintainer == null)'
```

#### Update packages in the custom repository which are installed on the host:

```bash
grep -Fxf <(pacman -Qq) <(pacman -Slq custom) > installed.txt
xargs -a installed.txt aur sync --repo=custom
```

#### Search for AUR packages with both wm and git in the name:

```bash
aur pkglist -P '(?=.*wm)(?=.*git)' | xargs aur search -i
```

#### Select an AUR package with name matching pony, and build the result:

```bash
select a in $(aur pkglist -F pony); do aur sync "$a"; break; done
```

### Official repositories
   
#### Print Perl modules that are both in the AUR and official repositories:

```bash
aur pkglist -P '^perl-.+' > perl.txt
grep -Fxf <(aur repo-filter < perl.txt) perl.txt
```

#### Print packages both in AUR and [community] and compare their versions:

```bash
aur repo -d community --all
```

### Using PKGBUILDs

#### Build packages in the pkgbuilds github repository (generating required .SRCINFO files):

```bash
git clone https://www.github.com/Earnestly/pkgbuilds
cd pkgbuilds
find -name PKGBUILD -execdir sh -c 'makepkg --printsrcinfo > .SRCINFO' \;

aur graph */.SRCINFO | tsort | tac > queue # Remove unwanted targets
aur build -a queue
```

#### Build a package for a different architecture, here i686:

```bash
setarch i686 aur sync -c --repo=custom_i686 tclkit
```

### Using 3rd Party Helpers

Repository packages can be "made foreign" by temporarily removing the
repository from the pacman configuration.  This can be used with
programs that support the PACMAN environment variable and check
foreign packages for AUR updates.

```bash
#!/bin/sh
# create a bin in /usr/local/bin
pacman --config=/etc/pacman.$repo.conf "$@"
```

and point the PACMAN variable towards it:

```bash
export PACMAN=/usr/local/bin/mypacman
```
