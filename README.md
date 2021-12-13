# This is my personal config repository for archlinux.
The following document gives a high level overview of my linux config.  
This particular config has been tested on ArchLinux only (last update on 11/14/21).  
Thus, only `pacman` and `yay` have been used and tested as arch and AUR packages managers respectively.  
The reader is highly adviced to search the internet and in particular the [ArchWiki][archlinux], **EVEN in NON arch-based systems!!**

First, an overview of the repo is given with the project architecture and a brief explaination of all the files involved in [section 1](#1-overview-and-architecture-toc).  
The documentation is presented and linked in [section 2](#2-documentation-toc).  
Finally, ways to contribute to this project are put forward in [section 3](#3-contribute-toc) for who is interested and a gallery of photos is presented in [section 4](#4-gallery-toc), 
to give an idea of the final rendering of the config.  

If you want a quick brief of what dotfiles really are, I recommend [this video][fireship-dotfiles] of *FireShip*.

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
## Table Of Content.
- **1** [**Overview and architecture.**](#1-overview-and-architecture-toc)
- **2** [**Documentation.**](#2-documentation-toc)
- **3** [**Contribute.**](#3-contribute-toc)
- **4** [**Gallery.**](#4-gallery-toc)

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
## 1. Overview and architecture. [[toc](#table-of-content)]
Below is a snapshot of the architecture of the config project.  
This repo has been created using a `bare` repository, i.e. initialization has been done with `git init --bare $HOME/.dotfiles` instead of the
usual `git init`.  This command creates a *bare* repository, meaning that there is no working directory inside it, only git files.
This is normal as *bare* repositories are not meant to host working files, but only track outside files.  
This makes the process of tracking *dotfiles* much easier! There is no need anymore to copy files into the *dotfiles* repository, track them
and put them back where they should be using symlinks! A simple `alias` of the form `cfg='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'`
is enough.

Hence, the architecture below is a perfect mirror, regarding tracked files only, of my system!  

Notes:
- simply replace $HOME with whatever your personal space is called. One can issue `echo $HOME` in a terminal to check this.
- flags are given right before file names -> **[d]** indicates a directory, **[l]** a symbolic link and **[-]** a file.

If you want more information about *bare* `git` repositories, you can check one of the following resources:
- a [blog post][bare-repo-blog] about *bare* repositories.
- a [video from dt][bare-repo-dt] if you want to see the creation of such a repository step by step.
```
$HOME
|-- [d]  .config                                     -- main config directory
|   |-- [d]  alacritty                                 --  the alacritty terminal emulator.
|   |   `-- [-]  alacritty.yml
|   |-- [d]  bspwm
|   |   `-- [-]  bspwmrc
|   |-- [d]  dmscripts
|   |   `-- [-]  config
|   |-- [d]  htop                                      -- my process monitor.
|   |   `-- [-]  htoprc
|   |-- [d]  mpd                                       -- music server deamon.
|   |   `-- [-]  mpd.conf                                 crashes for some reason...
|   |-- [d]  ncmpcpp                                   -- music client.
|   |   `-- [-]  config
|   |-- [d]  neofetch                                  -- a logo printer.
|   |   |-- [d]  ascii                                   -- all used arts.
|   |   |   |-- [-]  christmas.art
|   |   |   |-- [-]  fall-leaf.art
|   |   |   |-- [-]  halloween.art
|   |   |   |-- [-]  lolo.art
|   |   |   |-- [-]  spring-flower.art
|   |   |   |-- [-]  summer-sun.art
|   |   |   `-- [-]  winter-snow.art
|   |   |-- [-]  neofetchrc                              -- lauches the right art based on date.
|   |   `-- [-]  config.conf                             -- the actual config for basic use.
|   |-- [d]  nitrogen                                  -- a wallpaper manager.
|   |   `-- [-]  nitrogen.cfg
|   |-- [d]  spectrwm                                  -- the spectrWM tilling window manager.
|   |   |-- [-]  spectrwm.conf
|   |   |-- [-]  spectrwm_fr.conf
|   |   `-- [-]  spectrwm_us.conf
|   |-- [d]  sxhkd
|   |   `-- [-]  sxhkdrc
|   `-- [d]  vifm                                      -- the file manager.
|       |-- [d]  colors
|       |   `-- [-]  molokai.vifm
|       `-- [-]  vifmrc
|-- [d]  .pkgslists                                  -- packages.
|   |-- [-]  allpkglist.txt                            -- the list of all installed packages.
|   |-- [-]  foreignpkglist.txt                        -- the list of AUR packages.
|   |-- [-]  optdeplist.txt                            -- the list of optional packages.
|   `-- [-]  pkglist.txt                               -- the list of arch packages.
|-- [d]  scripts                                     -- my scripts.
|   |-- [-]  _countdown.sh                             -- a countdown with alarm (deprecated).
|   |-- [-]  _parse_git_info.sh                        -- parses the repo information if available.
|   |-- [-]  _shortwd.sh                               -- gives a short directory name for prompt.
|   |-- [-]  _stopwatch.sh                             -- a stopwatch (deprecated)
|   |-- [-]  prompt.sh                                 -- a binary prompt that executes commands.
|   |-- [-]  screenshot.sh                             -- takes screeshots with scrot.
|   |-- [-]  spectrWM-baraction.sh                     -- controls the spectrWM bar.
|   |-- [-]  togkb.sh                                  -- toggles the keyboard layout.
|   |-- [-]  tr2md.sh                                  -- transforms a directory into a tree for .md files.
|   |-- [-]  upl.sh                                    -- updates the list of installed packages.
|   |-- [-]  wvenv.sh                                  -- shows current python environment.
|   |-- [-]  xtcl.sh                                   -- disables my broken caps lock key.
|   `-- [-]  ytdl.sh
|-- [-]  .bash_aliases                               -- all my command aliases.
|-- [-]  .bash_logout                                -- what bash should do on logout.
|-- [-]  .bash_profile                               -- runs bash and starts the WM on startup.
|-- [-]  .bashrc                                     -- runs config stuff to make the experience what it is.
|-- [-]  .gitconfig                                  -- all my git config.
|-- [-]  .profile                                    -- profile script.
|-- [-]  .tmux.conf                                  -- my tmux config file.
|-- [-]  .vimrc                                      -- all needed configuration for a pretty vim.
|-- [-]  .xinitrc                                    -- what to do when x starts.
|-- [-]  .xscreensaver                               -- my config when the machine is idle or manually locked.
|-- [-]  LICENSE
`-- [-]  README.md
```


<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
## 2. Documentation. [[toc](#table-of-content)]
The doc of my dotfiles can be found on my [personal website][mysite] under the [`config/doc/`][mydoc] domain.  
In this section, some general ideas are given and the lists of the programs, scripts and other stuff I use are put forward.

#### Installation.
For now, the only way to install my config is to manually:
- backup your config files.
- copy mine in replacement.

For instance, let us say that you want to replace your `vim` config with mine, you can either go to the section below
or directly:
- clone the repo with `git clone https://github.com/a2n-s/dotfiles.git` or `git clone git@github.com:a2n-s/dotfiles.git`.
- place your version of the `.vimrc` file inside a backup directory or archive.
- copy my `.vimrc` file in replacement of yours.
- follow additional instructions in the dedicated section ([here][mydoc-vim]).
- enjoy your new `vim` experience!

I will try, in the future, to provide an `install.sh` script to (1) select what part of the config to install,
(2) backup the choosen files of the user inside a safe place and (3) install my config files in replacement.  
I.doc/programs/vim/ also plan to develop an `uninstall.sh` script that does the exact inverse to restore the config of the user
just as it was before the installation.

#### Dependencies.
In this config, some part, i.e. commands and programs like window managers or text editors, requires some dependencies.  
To install dependencies, one has two options:
- install them by hand, individually -> use `pacman -F <command>` or `yay -F <command>` to find the name of the package
containing the command. Then issue `pacman -S <package>` or `yay -S <package>` to install them.
- install all the packages I have on my system by using the lists in [`pkgslists`] and `pacman` or `yay` to install them.

(\*) comes from another repo.  
(\*\*) the associated documentation page.

#### List of programs:
- [x] [`alacritty`]    ([\*\*][mydoc-alacritty])
- [x] [`bspwm`]        ([\*\*][mydoc-bspwm])
- [x] [`bash`]         ([\*\*][mydoc-bash])
- [x] [`git`]          ([\*\*][mydoc-git])
- [x] [`htop`]         ([\*\*][mydoc-htop])
- [ ] [`mpd`]          ([\*\*][mydoc-mpd])
- [ ] [`ncmcpp`]       ([\*\*][mydoc-ncmcpp])
- [ ] [`neofetch`]     ([\*\*][mydoc-neofetch])
- [ ] [`nitrogen`]     ([\*\*][mydoc-nitrogen])
- [ ] [`spectrWM`]     ([\*\*][mydoc-spectrWM])
- [x] [`sxhkd`]        ([\*\*][mydoc-sxhkd])
- [ ] [`tmux`]         ([\*\*][mydoc-tmux])
- [x] [`vifm`]         ([\*\*][mydoc-vifm])
- [x] [`vim`]          ([\*\*][mydoc-vim])
- [x] [`x`]            ([\*\*][mydoc-x])
- [x] [`xscreensaver`] ([\*\*][mydoc-xscreensaver])

#### List of scripts:
- [ ] [`_countdown.sh`]         ([\*\*][mydoc-countdown.sh])
- [x] [`_parse_git_info.sh`]    ([\*\*][mydoc-parse_git_info.sh])
- [x] [`_shortwd.sh`]           ([\*\*][mydoc-shortwd.sh])
- [ ] [`_stopwatch.sh`]         ([\*\*][mydoc-stopwatch.sh])
- [x] [`prompt.sh`]             ([\*\*][mydoc-prompt.sh])
- [x] [`screenshot.sh`]         ([\*\*][mydoc-screenshot.sh])
- [x] [`spectrWM-baraction.sh`] ([\*\*][mydoc-spectrWM-baraction.sh])
- [x] [`togkb.sh`]              ([\*\*][mydoc-togkb.sh])
- [x] [`tr2md.sh`]              ([\*\*][mydoc-tr2md.sh])
- [x] [`upl.sh`]                ([\*\*][mydoc-upl.sh])
- [x] [`wvenv.sh`]              ([\*\*][mydoc-wvenv.sh])
- [x] [`xtcl.sh`]               ([\*\*][mydoc-xtcl.sh])

#### Other programs and stuff I use:
- [x] virtualenvwrapper: tutorials [in english][virtualenvs-en] and [in french][virtualenvs-fr].
- [x] some [wallpapers][my-wallpapers]                          (\*) ([\*\*][mydoc-wallpapers])
- [x] [my fork][my-dmenu] of [suckless dmenu][dmenu]            (\*) ([\*\*][mydoc-dmenu])
- [x] [my fork][my-dmscripts] of [dt's dmscripts][dmscripts-dt] (\*) ([\*\*][mydoc-dmscripts])
- [x] [my fork][my-polybar-themes] of [polybar-themes]          (\*) ([\*\*][mydoc-polybar-themes])
- [x] [my fork][my-surf] of [suckless surf][surf]               (\*) ([\*\*][mydoc-surf])

(\*) comes from another repo.  
(\*\*) the associated documentation page.


<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
## 3. Contribute. [[toc](#table-of-content)]
YOU can contribute to this project in the wonderfull world of linux, arch and configuration!
- if you like the overview, try to install the config and see what it looks like!
- if you like the config, please share it to whoever could be interested.
- if you stumble upon bugs, ideas, new amazing color palettes or alternatives,
do not hesitate to contact me, either via email, github issues or pull requests!

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
## 4. Gallery. [[toc](#table-of-content)]
| ![My wallpaper.][mygallery-nitrogen] |
|:--:|
| *My wallpaper.* |

| ![My bar.][mygallery-bar] |
|:--:|
| *My bar.* |

| ![SpectrWM in a dual monitor setup: left monitor selected.][mygallery-spectwm1] |
|:--:|
| *SpectrWM in a dual monitor setup: left monitor selected.* |

| ![SpectrWM in a dual monitor setup: right monitor selected.][mygallery-spectrwm2] |
|:--:|
| *SpectrWM in a dual monitor setup: right monitor selected.* |

| ![A screenshot of seing all processes.][mygallery-htop] |
|:--:|
| *A screenshot of seing all processes.* |

| ![A screenshot of being in a git repository.][mygallery-git] |
|:--:|
| *A screenshot of being in a git repository.* |

| ![A screenshot of being in vim.][mygallery-vim] |
|:--:|
| *A screenshot of being in vim.* |


<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
<!-- my files -->
[`pkgslists`]:             .pkgslists
[`alacritty`]:             .config/alacritty
[`bspwm`]:                 .config/bspwm
[`bash`]:                  .bashrc
[`git`]:                   .gitconfig
[`htop`]:                  .config/htop
[`mpd`]:                   .config/mpd
[`ncmcpp`]:                .config/ncmcpp
[`neofetch`]:              .config/neofetch
[`nitrogen`]:              .config/nitrogen
[`spectrWM`]:              .config/spectrwm
[`sxhkd`]:                 .config/sxhkd
[`tmux`]:                  .tmux.conf
[`vifm`]:                  .config/vifm
[`vim`]:                   .vimrc
[`x`]:                     .xinitrc
[`xscreensaver`]:          .xscreensaver
[`_countdown.sh`]:         scripts/_countdown.sh
[`_parse_git_info.sh`]:    scripts/_parse_git_info.sh
[`_shortwd.sh`]:           scripts/_shortwd.sh
[`_stopwatch.sh`]:         scripts/_stopwatch.sh
[`prompt.sh`]:             scripts/prompt.sh
[`screenshot.sh`]:         scripts/screenshot.sh
[`spectrWM-baraction.sh`]: scripts/spectrWM-baraction.sh
[`togkb.sh`]:              scripts/togkb.sh
[`tr2md.sh`]:              scripts/tr2md.sh
[`upl.sh`]:                scripts/upl.sh
[`wvenv.sh`]:              scripts/wvenv.sh
[`xtcl.sh`]:               scripts/xtcl.sh

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
<!-- my links -->
[archlinux]:                   https://archlinux.org/
[fireship-dotfiles]:           https://www.youtube.com/watch?v=r_MpUP6aKiQ
[bare-repo-blog]:              https://www.atlassian.com/git/tutorials/dotfiles
[bare-repo-dt]:                https://www.youtube.com/watch?v=tBoLDpTWVOM&t=879s
[mysite]:                      https://a2n-s.github.io/public
[mydoc]:                       https://a2n-s.github.io/public/doc/config

<!-- programs -->
[mydoc-alacritty]:             https://a2n-s.github.io/public/doc/config/dotfiles/alacritty
[mydoc-bspwm]:                 https://a2n-s.github.io/public/doc/config/dotfiles/bspwm
[mydoc-bash]:                  https://a2n-s.github.io/public/doc/config/dotfiles/bash
[mydoc-git]:                   https://a2n-s.github.io/public/doc/config/dotfiles/git
[mydoc-htop]:                  https://a2n-s.github.io/public/doc/config/dotfiles/htop
[mydoc-mpd]:                   https://a2n-s.github.io/public/doc/config/dotfiles/mpd
[mydoc-ncmcpp]:                https://a2n-s.github.io/public/doc/config/dotfiles/ncmcpp
[mydoc-neofetch]:              https://a2n-s.github.io/public/doc/config/dotfiles/neofetch
[mydoc-nitrogen]:              https://a2n-s.github.io/public/doc/config/dotfiles/nitrogen
[mydoc-spectrwm]:              https://a2n-s.github.io/public/doc/config/dotfiles/spectrwm
[mydoc-sxhkd]:                 https://a2n-s.github.io/public/doc/config/dotfiles/sxhkd
[mydoc-tmux]:                  https://a2n-s.github.io/public/doc/config/dotfiles/tmux
[mydoc-vifm]:                  https://a2n-s.github.io/public/doc/config/dotfiles/vifm
[mydoc-vim]:                   https://a2n-s.github.io/public/doc/config/dotfiles/vim
[mydoc-x]:                     https://a2n-s.github.io/public/doc/config/dotfiles/x
[mydoc-xscreensaver]:          https://a2n-s.github.io/public/doc/config/dotfiles/xscreensaver

<!-- scripts: -->
[mydoc-countdown.sh]:          https://a2n-s.github.io/public/doc/config/scripts/_countdown.sh
[mydoc-parse_git_info.sh]:     https://a2n-s.github.io/public/doc/config/scripts/_parse_git_info.sh
[mydoc-shortwd.sh]:            https://a2n-s.github.io/public/doc/config/scripts/_shortwd.sh
[mydoc-stopwatch.sh]:          https://a2n-s.github.io/public/doc/config/scripts/_stopwatch.sh
[mydoc-prompt.sh]:             https://a2n-s.github.io/public/doc/config/scripts/prompt.sh
[mydoc-screenshot.sh]:         https://a2n-s.github.io/public/doc/config/scripts/screenshot.sh
[mydoc-spectrWM-baraction.sh]: https://a2n-s.github.io/public/doc/config/scripts/spectrWM-baraction.sh
[mydoc-togkb.sh]:              https://a2n-s.github.io/public/doc/config/scripts/togkb.sh
[mydoc-tr2md.sh]:              https://a2n-s.github.io/public/doc/config/scripts/tr2md.sh
[mydoc-upl.sh]:                https://a2n-s.github.io/public/doc/config/scripts/upl.sh
[mydoc-wvenv.sh]:              https://a2n-s.github.io/public/doc/config/scripts/wvenv.sh
[mydoc-xtcl.sh]:               https://a2n-s.github.io/public/doc/config/scripts/xtcl.sh

<!-- other stuff -->
[virtualenvs-en]:              https://virtualenvwrapper.readthedocs.io/en/latest/
[virtualenvs-fr]:              https://python-guide-pt-br.readthedocs.io/fr/latest/dev/virtualenvs.html
[dmenu]:                       https://git.suckless.org/dmenu/
[dmscripts-dt]:                https://gitlab.com/dwt1/dmscripts.git
[polybar-themes]:              https://github.com/adi1090x/polybar-themes
[surf]:                        https://git.suckless.org/surf/
[my-wallpapers]:               https://github.com/a2n-s/wallpapers
[my-dmenu]:                    https://github.com/a2n-s/dmenu
[my-dmscripts]:                https://github.com/a2n-s/dmscripts
[my-polybar-themes]:           https://github.com/a2n-s/polybar-themes
[my-surf]:                     https://github.com/a2n-s/surf
[mydoc-wallpapers]:            https://a2n-s.github.io/public/doc/config/wallpapers
[mydoc-dmenu]:                 https://a2n-s.github.io/public/doc/config/dmenu
[mydoc-dmscripts]:             https://a2n-s.github.io/public/doc/config/dmscripts
[mydoc-polybar-themes]:        https://a2n-s.github.io/public/doc/config/polybar
[mydoc-surf]:                  https://a2n-s.github.io/public/doc/config/surf

<!-- gallery -->
[mygallery-nitrogen]:          https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-nitrogen.png
[mygallery-bar]:               https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-bar.png
[mygallery-spectrwm1]:         https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-spectrwm1.png
[mygallery-spectrwm2]:         https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-spectrwm2.png
[mygallery-htop]:              https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-htop.png
[mygallery-git]:               https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-git.png
[mygallery-vim]:               https://a2n-s.github.io/public/res/doc/config/dotfiles/gallery-vim.png
