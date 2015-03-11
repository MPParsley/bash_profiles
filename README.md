[![Author](https://img.shields.io/badge/author-%40sgrame-blue.svg?style=flat-square)](https://twitter.com/sgrame)
[![License - MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](http://opensource.org/licenses/MIT)


# .bash_profiles

This folder contains scripts and settings that will be loaded when you open a terminal.

The scripts and settings were created for use within an OSX environment.


## Installation
[Download](https://github.com/zero2one/bash_profiles/archive/develop.zip), unpack and move the folder to `/Users/<your username>` rename the folder to `.bash_profiles` so it becomes a hidden folder.

Or [clone](https://github.com/zero2one/bash_profiles) this repository within your home folder (`/Users/<your username>`).

```
$ git clone https://github.com/zero2one/bash_profiles.git ~/.bash_profiles
```

Make sure that the `bash_profile.sh` script is executable:

```
$ chmod +x ~/.bash_profiles/bash_profile.sh
```

Replace the `.bash_profile` file within your home folder (`/Users/<your username>/.bash_profile`) by removing the original file and replace it with a symlink to the `bash_profile.sh` script in the `.bash_profiles` folder.

```
$ mv ~/.bash_profile ~/.bash_profile.BAK
$ ln -s ~/.bash_profiles/bash_profile.sh ~/.bash_profile
```

Close and reopen the terminal window or reload the `.bash_profile` by running the following command:

```
$ source ~/.bash_profile
```


## Enable scripts

This package has a set of predefined scripts. They are not defined by default.
You can enable them by creating a symlink from the `.bash_profiles/enabled/` folder to the script in the `.bash_profiles/available/` folder:

```
$ cd ~/.bash_profiles/enabled
$ ln -s ../available/<script name>.sh 
```

You need to reload the .bash_profile folder (or close and reopen the terminal) to get the changes applied:

```
$ source ~/.bash_profile
```

The `.bash_profile` script will be loaded and will scan the enabled folder to load all `*.sh` files.


## Add aliases

The `.bash_profile` script will also load automatically all scripts in the `.bash_profiles/aliases` folder.

This folder is meant to hold scripts that define aliases, but you can put here whatever script you like to be loaded in the command line interface.

Make sure that each script starts with a shebang line (`#!/bin/bash`)


## Script included in the package

The `.bash_profiles/available`folder contains a set of predefined scripts.
See [Enable scripts](#enable-scripts) how to enable them.

This is an overview of all available scripts:

### bash_history.sh
Override the default `history` command settings for keeping and showing the bash history.

It will keep the last 100 000 commands you run trough CLI.

### composer.sh
Add the composer bin directory to the $PATH variable so packages installed globally by composer can be run without using the full path (e.g. phpunit, …).

### git.sh
**Support for latest git version.**

X-Code comes with an outdated version of GIT.
Replace it with a manual updated version.

1. Download the latest version from http://git-scm.com/download/mac
2. Run the installer.

This script will adds the manual installed GIT bin path to the $PATH variable.

**Cleaner Git log output**

Alias to have a nicer log output from GIT.
See [https://coderwall.com/p/euwpig/a-better-git-log](https://coderwall.com/p/euwpig/a-better-git-log)

Use following command to see the nicer output:

```
$ git lg
```


### homebrew.sh
Brew autocomplete (including support for git).

You need to have following installation done:

1. Install [homebrew](http://brew.sh/).
2. Install autocomplete support for the `brew` and `git` commands:
   
   ```
   $ brew install git bash-completion
   ```
   
   (Note: If this install fails with a 404 error, and you already have git installed, just remove the git part of this brew install).
   
   ```
   $ brew install bash-completion
   ```


### java.sh
Force starting java jar files from cli in the background (e.g. Tomcat, Solr, Tika).

### mongodb.sh
Adds the MongoDB bin directory to the $PATH variable.

### mysql.sh
Add the bin directory, of the manually installed [MySQL server](http://dev.mysql.com/downloads/mysql/), to the $PATH variable.

### php_debug.sh
Enable/Disable debugging of PHP scripts when they are run in command line.
Use an IDE (like PhpStorm) that support PHP debugging.

Enable debugger by running:

```
$ php-debug-on
```

Disable debugger by running:

```
$ php-debug-off
```

### prompt.sh
Pimp the command prompt by:

* Add colors to it.
* Add extra info to it like current user, hostname & full path
* Put the prompt on 2 lines: 1 with the info, 2dn to enter command.
* Show the current GIT branch name (if any).

![bash_prompt](https://cloud.githubusercontent.com/assets/133124/6603845/d083629e-c824-11e4-8bce-0a74b086555f.png)

### tar.sh
Exclude OSX hidden files, created due to the extended attributes, from tarballs.

### terminal_window.sh
Add the current path to the terminal window & tab.

This will lookup the current path, create a shorter version out of it and add it as title to the terminal window & tab.

![terminal_window](https://cloud.githubusercontent.com/assets/133124/6603897/1d661336-c825-11e4-8420-ae845fcaf11f.png)

### zend_framework.sh
Add alias for the Zend Framework 1 command line tool.
It uses the zend_framework that is installed together with Zend Server.

```
$ zf
```

### zend_server.sh
Adds the bin directory, created during the instalation of Zend Server, to the $PATH variable.
