---
layout: post
title: "Lion reinstallation"
description: ""
category: 
tags: []
---
{% include JB/setup %}

## Reinstall Lion

1. Restart OS.  While start up, keep pressing the "option" key
2. Start system at Recovery HD
3. Use Disc utility and delete Machintosh HD
4. Reinstall Lion

## Install Firefox

## Install Xcode from App Store
* After installation, add "Command Line Tools" by 
   1. Start Xcode
   2. From menu, chose Xcode -> Preference
   3. Select Downloads -> Command Line Tools -> install

## Install Vim

1. Download from http://code.google.com/p/macvim/
2. Install Pathogen by following https://github.com/tpope/vim-pathogen
3. Install Vim-Latex
   * Follow http://vim-latex.sourceforge.net/index.php?subject=download&title=Download

## Resulting vimrc

      filetype plugin indent off
      call pathogen#runtime_append_all_bundles()
      syntax on
      filetype plugin indent on
      
      set nocompatible
      set number
      set expandtab
      set tabstop=2
      set shiftwidth=2
      set softtabstop=2
      set hlsearch
      set incsearch
      set ignorecase
      set smartcase
      
      " REQUIRED. This makes vim invoke Latex-Suite when you open a tex file.
      filetype plugin on
      "
      " " IMPORTANT: win32 users will need to have 'shellslash' set so that latex
      " " can be called correctly.
      set shellslash
      "
      " " IMPORTANT: grep will sometimes skip displaying the file name if you
      " " search in a singe file. This will confuse Latex-Suite. Set your grep
      " " program to always generate a file-name.
      set grepprg=grep\ -nH\ $*
      "
      " " OPTIONAL: This enables automatic indentation as you type.
      filetype indent on
      "
      " " OPTIONAL: Starting with Vim 7, the filetype of empty .tex files defaults
      " to
      " " 'plaintex' instead of 'tex', which results in vim-latex not being loaded.
      " " The following changes the default filetype back to 'tex':
      let g:tex_flavor='latex'
      "

## Resulting .gvimrc

      set guioptions-=T
      set transparency=30
      colorscheme murphy

## Homebrew installation

* Refer to http://mxcl.github.com/homebrew/
* Here is the log 
      
      $ /usr/bin/ruby -e "$(/usr/bin/curl -fksSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"
      ==> This script will install:
      /usr/local/bin/brew
      /usr/local/Library/Formula/...
      /usr/local/Library/Homebrew/...
      ==> The following directories will be made group writable:
      /usr/local/.
      /usr/local/bin
      ==> The following directories will have their group set to admin:
      /usr/local/.
      /usr/local/bin
      
      Press enter to continue
      ==> /usr/bin/sudo /bin/chmod g+rwx /usr/local/. /usr/local/bin
      Password:
      ==> /usr/bin/sudo /usr/bin/chgrp admin /usr/local/. /usr/local/bin
      ==> Downloading and Installing Homebrew...
      ==> Installation successful!
      You should run `brew doctor' *before* you install anything.
      Now type: brew help
      [4]-  Done                    mvim test.tex
      $ brew doctor
      
      Warning: Your Xcode is configured with an invalid path.
      You should change it to the correct path. Please note that there is no correct
      path at this time if you have *only* installed the Command Line Tools for Xcode.
      If your Xcode is pre-4.3 or you installed the whole of Xcode 4.3 then one of
      these is (probably) what you want:
      
          sudo xcode-select -switch /Developer
          sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
      
      DO NOT SET / OR EVERYTHING BREAKS!
      $ sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
      $ brew doctorYour system is raring to brew.
      

## Install tools

### ledit

      $ brew install ledit
      ==> Installing ledit dependency: objective-caml
      ==> Downloading https://downloads.sf.net/project/machomebrew/Bottles/objective-c
      ######################################################################## 100.0%
      ==> Pouring objective-caml-3.12.1.lion.bottle.tar.gz
      /usr/local/Library/Homebrew/download_strategy.rb:118: warning: conflicting chdir during another chdir block
      /usr/local/Cellar/objective-caml/3.12.1: 1310 files, 182M
      ==> Installing ledit dependency: camlp5
      ==> Downloading http://pauillac.inria.fr/~ddr/camlp5/distrib/src/camlp5-5.15.tgz
      ######################################################################## 100.0%
      ==> ./configure -prefix /usr/local/Cellar/camlp5/5.15 -mandir /usr/local/Cellar/
      ==> make world.opt
      ==> make install
      /usr/local/Cellar/camlp5/5.15: 193 files, 18M, built in 116 seconds
      ==> Installing ledit
      ==> Downloading http://pauillac.inria.fr/~ddr/ledit/distrib/src/ledit-2.01.tgz
      ######################################################################## 100.0%
      ==> make BINDIR=/usr/local/Cellar/ledit/2.01/bin LIBDIR=/usr/local/Cellar/ledit/
      ==> make install BINDIR=/usr/local/Cellar/ledit/2.01/bin LIBDIR=/usr/local/Cella
      /usr/bin/strip: the __LINKEDIT segment does not cover the end of the file (can't be processed) in: /usr/local/Cellar/ledit/2.01/bin/ledit
      /usr/local/Cellar/ledit/2.01: 6 files, 476K, built in 4 seconds

### Scala

      $ brew install scala
      ==> Downloading http://www.scala-lang.org/downloads/distrib/files/scala-2.9.2.tg
      ######################################################################## 100.0%
      ==> Downloading https://raw.github.com/scala/scala-dist/27bc0c25145a8/completion
      ######################################################################## 100.0%
      ==> Caveats
      Bash completion has been installed to:
        /usr/local/etc/bash_completion.d
      ==> Summary
      /usr/local/Cellar/scala/2.9.2: 38 files, 26M, built in 25 seconds

### SWI Prolog

* This was failed due to lack of javac
* JAVA installation was kicked out automatically
* Retry worked well

      $ brew install swi-prolog
      ==> Downloading http://www.swi-prolog.org/download/stable/src/pl-6.0.2.tar.gz
      Already downloaded: /Library/Caches/Homebrew/swi-prolog-6.0.2.tar.gz
      ==> ./configure --prefix=/usr/local/Cellar/swi-prolog/6.0.2 --mandir=/usr/local/
      ==> make
      ==> make install
      ==> Caveats
      By default, this formula installs the JPL bridge.
      On 10.6, this requires the "Java Developer Update" from Apple:
       * https://github.com/mxcl/homebrew/wiki/new-issue
      
      Use the "--without-jpl" switch to skip installing this component.
      ==> Summary
      /usr/local/Cellar/swi-prolog/6.0.2: 1813 files, 30M, built in 3.2 minutes

### Haskell

      $ brew install haskell-platform
      ==> Installing haskell-platform dependency: ghc
      Warning: Formula will not build with Clang, trying LLVM
      ==> Downloading http://www.haskell.org/ghc/dist/7.0.4/ghc-7.0.4-x86_64-apple-dar
      ######################################################################## 100.0%
      ==> ./configure --prefix=/usr/local/Cellar/ghc/7.0.4
      ==> make install
      ==> Caveats
      This brew is for GHC only; you might also be interested in haskell-platform.
      ==> Summary
      /usr/local/Cellar/ghc/7.0.4: 4955 files, 647M, built in 2.9 minutes
      ==> Installing haskell-platform
      ==> Downloading http://lambda.haskell.org/platform/download/2011.4.0.0/haskell-p
      ######################################################################## 100.0%
      ==> ./configure --prefix=/usr/local/Cellar/haskell-platform/2011.4.0.0 --enable-
      ==> EXTRA_CONFIGURE_OPTS="--libdir=/usr/local/Cellar/haskell-platform/2011.4.0.0
      ==> Caveats
      Run `cabal update` to initialize the package list.
      
      If you are replacing a previous version of haskell-platform, you may want
      to unregister packages belonging to the old version. You can find broken
      packages using:
        ghc-pkg check --simple-output
      You can uninstall them using:
        ghc-pkg check --simple-output | xargs -n 1 ghc-pkg unregister --force
      ==> Summary
      /usr/local/Cellar/haskell-platform/2011.4.0.0: 1967 files, 166M, built in 12.4 minutes

### Hakyll
    cabal update
    cabal install hakyll

## Set up ProjectLocker SSH keys

1. Generate key
    ssh-keygen
2. Copy the key to Locker's home page


## Install and Setup VirtualBox

## On VirtualBox, set up octopress

### Install RVM

* Refer to https://rvm.io//rvm/install/
* One command should do.

      user$ curl -L get.rvm.io | bash -s stable

### Install Ruby

* Have to install zlib-devel, openssl-devel and readline-devel first.

      su$ yum -y install zlib-devel
      su$ yum -y install openssl-devel
      su$ yum -y install readline-devel

* Then, follow http://octopress.org/docs/setup/

      user$ rvm install 1.9.2 && rvm use 1.9.2



