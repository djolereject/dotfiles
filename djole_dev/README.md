Djole Dev Ansible Role
=========

My ansible role designed for fast setup of development computer which is usualy MBP with MacOS, but sometimes can be Ubuntu. MacOS tends to also be my main computer so mac role installs some software unrelated to development.

This is my personal role so it might not suit somebody with different needs, but it's still good starting point in building simple dev environment. Look into list of software installed with apt or homebrew and tweak that list acording to your needs. In the same manner skip copying of .emacs.d from my repository if you have preferred setup for Emacs. In case you don't need Emacs at all, along with removing it from the software list be sure to remove all tasks related to it.

Role Variables
--------------

This is a simple role so all variables are defined in [defaults](./defaults/main.yml).

- **dotfiles** and **shell**
  Directory path where all dotfiles are stored and subdirectory for shell-related files.
- **zshrc**
  **path** is destination of actual file and **link** is symlink on it from user root. Template for zshrc is in [zshrc](./templates/zshrc.j2).
- **oh_my_zsh**
  **src** is url from which oh-my-zsh is pulled and **path** is destination which has to be recreated in zshrc file.
- **aliases**
  Path to separate file sourced in .zshrc with template at [aliases](./templates/aliases.j2).
- **env**
  Same as aliases, but for environment variables [env](./templates/env.j2).
- **emacs**
  **src** is my personal repository url from which .emacs.d is pulled, **path** is dotfiles directory where it's stored and **link** is symlink on it from user root. You can change or remove all paths but Emacs will look for "~/.emacs.d" and create it if it's not there.
- **software**
  Programs installed are separated by package manager, so we have lists of **apt** installed software for Ubuntu and **brew** and **cask** for MacOS. Feel free to curate this list as needed.

Dependencies
------------
There are no external dependencies, all modules are standard ones from [modules](https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html).

Example Playbook
----------------

Both operating systems can be created from [tests](./tests/) directory with command:

`vagrant up`

This creates two boxes with Ubuntu 18 and MacOS 10.14.

License
-------
GNU GPLv3

Author Information
------------------

Djordje Knezevic

email: djolereject@gmail.com
