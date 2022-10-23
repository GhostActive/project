# project

*project* is an utility script to create project folder - based on template folders.

## Installation and Deinstallation

**Installation**

Clone GitHub repository
```sh
git clone https://github.com/GhostActive/project.git
```

Install `project` to local file system 
```sh
cd project && chmod +x project && sudo cp project /usr/local/bin/project
```

**Deinstallation**

```sh
sudo rm /usr/local/bin/project
```

## Configuration

The configuration of used path is handled within the script itself. To change the current configuration just open the script and modify the values as you need.

```
# Hint: Use $HOME instead of '~'. Folder names are quoted before used to allow
#       spaces in folder names. Therefore '~' will not be replaced to current
#       user's home directory.

# The varibale SRC_FOLDER contains the root path for template folders. At
# runtime files and sub folders can be copied from a specified template folder
# to the current project folder. The default template folder is defined by
# DEFAULT_TEMPLATE. If the path for SRC_FOLDER doesn't exist, then copying items
# from template folder is skipped. To disable the use of templates in general,
# then set SRC_FOLDER to "" (empty string).
SRC_FOLDER="$HOME/Templates"

# Default name of used template folder. If a sub folder in $SRC_FOLDER with
# this name exists, it's content is copied automatically to new project folders.
# If the folder does't exist, then it's ignored and no template is used.
DEFAULT_TEMPLATE="default"

# Root folder in which new project folders will be created. At runtime in the
# DST_FOLDER a new sub folder with given name from user input is created. If the
# DST_FOLDER doesn't exist, it's created automatically.
DST_FOLDER="$HOME/Projects"

# The most recently created project folder can be refrenced by a link. The
# variable LINK_NAME contains the full path of where the link should be created,
# e.g. in DST_FOLDER with the name 'current'. To disable the creattion of a
# link, set the value to "" (empty string).
LINK_NAME="$DST_FOLDER/current"
```

## Usage

```
$ project
project - creates new project folder

Usage: project [OPTION]... [STRING] ...

All non alphanumeric characters in the given name are replaced by '-' (dash).
Multiple dashes in the name are reduced to single one, e.g '--' or '---' gets
to '-'. Dashes at the begin and the end of a name are removed, too.

Options
    -h      Print this help message.

    -t FOLDER
            Used template FOLDER to copy content when creating new project
            folder instead of the default one.

    -v      Show version number.

Examples
    # Create new project folder
    project samplecustomer sampleproject

    # Create new project folder with current date as prefix
    project $(date +'%F') samplecustomer sampleproject
```
