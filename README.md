# setup-mac

This is a playbook to set up an OS X computer the way I like.

It installs and configures most of the software I use on my macs for work and play. 

It can be run multiple times on the same machine safely. It installs, upgrades, or skips packages based on what is already installed on the machine.

You could easily clone or fork this repo and change stuff to the way you like. 


## Requirements

Tested on:

* OS X Yosemite (~10.10.4)
* macOS Mojave (~10.14.5)


## Installation

### Fast Install

If you'd like to start with my default list of tools and apps (see Included Apps/Config below), then simply install with:

    sh -c "$(curl -fsSL https://raw.githubusercontent.com/nille/setup-mac/master/install.sh)"


You can always customize the install after-the-fact (see below), and re-run the playbook. It will skip over any installed apps.

### Custom Install

If you want to add/remove to the list of apps/utils installed, its pretty straightforward.

As above, download and bootstrap the script. But stop it before it starts ansible, and edit the playbook as desired, before re-running ansible.

1. Grab and start the bootstrap script. Let it install the prereqs and clone the full `nille/setup-mac` repo locally...

      sh -c "$(curl -fsSL https://raw.githubusercontent.com/nille/setup-mac/master/install.sh)"


1. Stop the script (Ctrl+C) when ansible asks for the a 'sudo' password. 

        ```
        Changing to setup-mac repo dir ...

        Running ansible playbook ...
        SUDO password:  ^c

        ```

1. Change into the cloned repo dir

        cd setup-mac

1. Edit playbook.yml and add/remove the apps/utils you want. 

        vi playbook.yml

1. Kick off ansible manually

        ansible-playbook playbook.yml -i hosts --ask-sudo-pass -vvvv 

You can do this as many times as you like and re-run the `ansible-playbook` command. Ansible is smart enough to skip installed apps, so subsequent runs are super fast.


## Included Applications / Configuration

### Applications

Apps installed with Homebrew Cask:

  - 1password
  - alfred # | http://www.alfredapp.com 
  - apptrap # remove associated prefs when uninstalling
  - appzapper # uninstaller
  - bettertouchtool # window snapping. (maybe Moom is more lightweight?)
  - carbon-copy-cloner # backups | https://bombich.com/download
  - cheatsheet # know your shortcuts
  - cyberduck # ftp, s3, openstack
  - dash # totally sick API browser
  - diffmerge # free visual diq
  - disk-inventory-x # reclaim space on your expensive-ass Apple SSD | http://www.derlien.com/
  - dropbox # a worse Mega Sync
  - firefox 
  - flux # get more sleep
  - google-chrome
  - imageoptim # optimize images
  - istumbler # network discovery GUI
  - jumpcut # awesome clipboard
  - karabiner # Keyboard customization
  - licecap # GIFs !
  - little-snitch # awesome outbound firewall
  - megasync # a better Dropbox  
  - monolingual # remove unneeded osx lang files
  - nvalt # fast note taking
  - qlcolorcode # quick look syntax highlighting
  - qlimagesize # quick look image dimensions
  - qlmarkdown # quick look .md files
  - qlstephen # quick look extension-less text files
  - rowanj-gitx # Awesome gitx fork.
  - sequel-pro # FREE SQL GUI!
  - shortcat # kill your mouse
  - shuttle # ssh management
  - skype # 
  - sublime-text3 # (experimental cask) | http://www.sublimetext.com/
  - thunderbird # email
  - tomighty # pomodoro
  - torbrowser # be the noise
  - transmission # torrents
  - tunnelblick # VPN
  - vagrant # | https://www.vagrantup.com/downloads.html
  - vagrant-manager # 
  - virtualbox # | https://www.virtualbox.org/
  - vlc 

There are several more common cask apps listed in the playbook.yml - simply uncomment them to include them in your install. 


### Packages/Utilities 
 
Things installed with Homebrew:

  - autoconf
  - autojump # quickly navigate from cmd line
  - bash # Bash 4
  - boot2docker # for running docker on osx
  - brew-cask
  - coreutils # Install GNU core utilities (those that come with OS X are outdated)
  - cowsay # amazing
  - docker # | https://docs.docker.com/installation/mac/
  - findutils  # Install GNU `find`, `locate`, `updatedb`, and `xargs`, g-prefixed
  - git
  - go
  - gpg
  - hub # github
  - keybase # in alpha at time of writing.
  - mtr # better traceroute
  - node
  - npm
  - openssl
  - packer
  - postgresql # yes and nosql
  - python
  - rbenv # ruby. Just installs binaries - assumes you bring in the dotfiles.
  - readline
  - redis
  - rename # rename multiple files
  - rsync
  - ruby-build
  - sqlite # production rails DB
  - the_silver_searcher # fast ack-grep
  - tmux
  - vim
  - wget
  - zsh

There are several more utils listed in the playbook.yml - simply uncomment them to include them in your install. 


### System Settings

It also installs a few useful system preferences/settings/tweaks with a toned-down verson of Matt Mueller's [OSX-for Hackers script](https://gist.github.com/MatthewMueller/e22d9840f9ea2fee4716). 

It does some reasonably gnarly stuff e.g.

  - hide spotlight icon
  - disable app Gate Keeper
  - change stand-by delay from 1hr to 12hrs. 
  - Set trackpad tracking rate.
  - Set mouse tracking rate.
  - and lots more...

so you need read it very carefully first. (see scripts/system_settings.sh)

TODO: moar sick settings with https://github.com/ryanmaclean/OSX-Post-Install-Script


### MacStore Apps (WIP)

These apps only available via the App Store. (sigh)

TODO: Port bork : https://github.com/mattly/bork/blob/master/types/macstore.sh and do this automagically!

  - Monosnap
  - Pages
  - Keynote
  - Numbers
  - etc



### Application Settings (WIP)

Keep your application settings in sync.

TODO: Add Mackup task


### Other 

- install fonts like a boss : http://lapwinglabs.com/blog/hacker-guide-to-setting-up-your-mac

- TODO: Install [Sublime Package Manager](http://sublime.wbond.net/installation).
- ZSH tab/auto completion
- Powerline in tmux
- zsh-autosuggestions plugin
- zsh-history-substring-search plugin
- zsh-notify plugin


## Author

[Nille af Ekenstam](https://nille.dev), 2019. 


## Credits

This project is based off the work of the following folks;

* Eduardo de Oliveira Hernandes' [ansible-macbook](https://github.com/eduardodeoh/ansible-macbook])
* Jeff Geerlings' [Mac Dev Ansible Playbook](https://github.com/geerlingguy/mac-dev-playbook)
* [Thoughtbot/laptop](https://github.com/thoughtbot/laptop) (boostrapping, dev tools)
* [OSX for Hackers](https://gist.github.com/MatthewMueller/e22d9840f9ea2fee4716) (awesome osx tweaks)
* [Mackup](https://github.com/lra/mackup)  (backup/restore App settings)
* [siyelo/laptop](https://github.com/siyelo/laptop)
