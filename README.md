edify
=====

This script stores and displays custom cli arguments with respective short descriptions, useful for OS X sysadmins.

For a long time, whenever I've come across an interesting command or a specific argument to which I would routinely return, I'd open up [nvAlt](http://brettterpstra.com/projects/nvalt/) and store the command there, along with a short description to remind my failing brain later what it was that I found so very interesting in the first place.

However, this started to prove inefficient. I'd be in Terminal, and would need to switch over to nvAlt, search for the command, read through my sloppy notes, find the specific invocation, attempt to copy it to the clipboard, switch back to Terminal, paste, and then get annoyed that the trailing return was also added to the clipboard.

Inspired by apps such as [Dash](http://kapeli.com/dash) and a [twittering](https://twitter.com/zoocoup/status/547061584728981505) by Jason Broccardo, I thought it might be nice to make something that would allow me to organize and search my commands, and which could be shared and/or appended by anyone.

Requirements
------------

+ python 2.7.x
+ I've only tested on 10.10.x.

Usage
-----

    usage: edify [-h] [-a] [-l] [-g GREP]

    optional arguments:
      -h, --help            show this help message and exit
      -a, --add             Add entry to local plist
      -l, --list            List all entries
      -g GREP, --grep GREP  Search entries for string

Installation
------------

Clone the repo and run the install script. The edify script is installed into `/usr/local/bin/` while the plist is installed into `/usr/local/share/edify/`, creating the enclosing directory if needed.

    git clone https://github.com/chilcote/edify.git && cd edify
    sudo ./install

Listing and Searching items
---------------------------

Generate a list of all commands in both the cached and local plists with the `-l` or `--list` argument:

    edify -l

Search for a case-insensitive string by invoking the `-g` or `--grep` argument:

    edify -g 'foo'


Adding commands locally
-----------------------

To add commands that you want to keep local, either because it contains site-specific information, or because you're a crumudgeon, you can do so with the `-a` or `--add` argument. The information will be stored at `~/Library/Application Support/edify/com.github.edify.plist`.

    edify -a

You will be prompted for two items: The command syntax and a short description.

    Enter the command:
    Enter description:

Enter the appropriate information and it will be added to your local plist.


Contributing
------------

To contribute to the master plist, change directory to your fork, create a branch, and use the hidden `-e` or `--edit` argument:

    ./edify -e

You will be prompted for two items: The command syntax and a short description.

    Enter the command:
    Enter description:

Enter the appropriate information and it will be added to the master plist. Pull requests are welcome.


License
-------

    Copyright 2014 Joseph Chilcote

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
