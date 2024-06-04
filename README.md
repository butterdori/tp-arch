# tp-arch  
Arch Linux installation and configuration for Thinkpad T14s AMD Gen 3  
Specs:  
Processor : AMD Ryzen™ 7 PRO 6850U Processor (2.70 GHz up to 4.70 GHz)  
Graphic Card : Integrated AMD Radeon™ 680M  
Memory : 16 GB LPDDR5-6400MHz (Soldered)  
Display : 14" WUXGA (1920 x 1200)  

Installation of Arch Linux on the T14s is quite painless, especially if using the archinstall script. Follow the Arch wiki to install without archinstall, which sometimes has issues. The following tweaks are not strictly necessary, but are quality of life improvements for my personal use.


## Installation  
Process  
Desktop  
gnome  
mirrors  
Preinstall packages list: firefox zsh vim gnome-terminal onlyoffice thunderbird mc  

## After installation  
### Keyboard  
**keyd**

https://github.com/rvaiya/keyd
```
git clone https://github.com/rvaiya/keyd
cd keyd
make && sudo make install
sudo systemctl enable keyd && sudo systemctl start keyd
```
Install and start keyd `sudo systemctl enable keyd`

Config file in `/etc/keyd/default.conf`

```
[ids]
#Exception for NINJA keyboard
-258a:004c
*
[main]
#Escape when presesd, control when held
capslock = overload(control, esc)
#Remap esc to capslock
esc = capslock
#Map pageup and pagedown keys on the keyboard to browser forward/backwards keys, like older models of ThinkPads.
pagedown = macro(leftalt+right)
pageup = macro(leftalt+left)
rightcontrol=layer(fn)
[fn]
pageup = macro(pageup)
pagedown = macro(pagedown)
```

### Gnome keyboard shortcut customization
**Navigation**  
Switch applications: Alt+Tab  
Switch windows: Super+Tab
Switch windows of an app directly: Super+\`    
Switch windows of an application: Alt+\`  

**Screenshots**  
Take a screenshot: Super+S
Take a screenshot interactively: Print  

**Windows**  
Toggle maximization state: Super+Up

### Gnome Shell Extensions
AppIndicator and KStatuesNotifierItemSupport  
Blur my Shell  
Clipboard History  
Dash to Dock
ddterm  
GSConnect
Just Perfection  
Panel Date Format
Vitals  

## Themes

### Gnome Theme

### GDM Settings
https://github.com/gdm-settings/gdm-settings?tab=readme-ov-file  
Greeter theme

### Terminal color scheme
One Half for gnome-terminal https://github.com/sonph/onehalf

## Work

### VSCode

### R

### LaTeX

### STATA
Linux version of STATA18 is installable without much tweaks. However, the installation contains a install script that can sometimes interfere with pacman updates (endless loop of press y to continue). It is safe to delete the installation script after installation.

### Other applications
P3X OneNote  
MS-365-Electron  
tlp tlpui  
Obsidian  
Joplin  
Krita  
dconf editor  
Main Menu  
Variety  
MPV  

## App configurations
## MPV
Skin: https://github.com/cyl0/ModernX
Script to autoadd other videos in the same folder to the playlist:

### OneDrive
https://github.com/abraunegg/onedrive  
Config file at ~/.config/onedrive/config

```
# Configuration for OneDrive Linux Client
# This file contains the list of supported configuration fields
# with their default values.
# All values need to be enclosed in quotes
# When changing a config option below, remove the '#' from the start of the line
# For explanations of all config options below see docs/USAGE.md or the man page.
#
sync_dir = "~/OneDriveGT"
# skip_file = "~*|.~*|*.tmp"
# monitor_interval = "300"
skip_dir = "World Bank"
# log_dir = "/var/log/onedrive/"
# drive_id = ""
# upload_only = "false"
# check_nomount = "false"
# check_nosync = "false"
# download_only = "false"
# disable_notifications = "false"
# disable_upload_validation = "false"
# enable_logging = "false"
# force_http_11 = "false"
# local_first = "false"
# no_remote_delete = "false"
# skip_symlinks = "false"
# debug_https = "false"
# skip_dotfiles = "false"
# skip_size = "1000"
# dry_run = "false"
# min_notify_changes = "5"
# monitor_log_frequency = "6"
# monitor_fullscan_frequency = "12"
# sync_root_files = "false"
# classify_as_big_delete = "1000"
# user_agent = ""
# remove_source_files = "false"
# skip_dir_strict_match = "false"
# application_id = ""
# resync = "false"
# resync_auth = "false"
# bypass_data_preservation = "false"
# azure_ad_endpoint = ""
# azure_tenant_id = "common"
# sync_business_shared_folders = "false"
# sync_dir_permissions = "700"
# sync_file_permissions = "600"
# rate_limit = "131072"
# webhook_enabled = "false"
# webhook_public_url = ""
# webhook_listening_host = ""
# webhook_listening_port = "8888"
# webhook_expiration_interval = "86400"
# webhook_renewal_interval = "43200"
# space_reservation = "50"
# display_running_config = "false"
# read_only_auth_scope = "false"
# cleanup_local_files = "false"
# operation_timeout = "3600"
# dns_timeout = "60"
# connect_timeout = "10"
# data_timeout = "600"
# ip_protocol_version = "0"
```

### oh-my-zsh
https://ohmyz.sh/
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Powerline theme for oh-my-zsh

### .zshrc
```
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="powerlevel10k/powerlevel10k"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

#typeset -g POWERLEVEL9K_INSTANT_PROMPT=quiet

#TexLive PATH
#PATH=/usr/local/texlive/2023/bin/x86_64-linux; export PATH
#MANPATH=/usr/local/texlive/2023/texmf-dist/doc/man;$MANPATH; export manpath
#INFOPATH=/usr/local/texlive/2023/texmf-dist/doc/info;$INFOPATH; export infopath
export PATH="/usr/local/texlive/2023/bin/x86_64-linux:$PATH"
export MANPATH="/usr/local/texlive/2023/texmf-dist/doc/man:$MANPATH"
export INFOPATH="/usr/local/texlive/2023/texmf-dist/doc/info:$INFOPATH"
export PATH="/home/dk/.local/bin/:$PATH"
export PATH="/usr/local/stata18/:$PATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"
alias ls='ls -lh --group-directories-first --color=auto'

source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

# Created by `pipx` on 2024-02-15 19:42:42
export PATH="$PATH:/home/dk/.local/bin"
```

### Powerline fonts
Caskaydia

### Battery charge thresholds
For battery management, charge thresholds can be used. Stops battery from charging before reaching 80%. Start recharging when battery falls to 75%.  
Install TLP  
```
START_CHARGE_THRESH_BAT0 75
STOP_CHARGE_THRESH_BAT0 80
```
## System management
### Home folder backup
Backup script (home_backup.sh) that will make a backup every month, keep the last 3 month and last 1 year's backup. It excludes the Downloads folder, cache, log, and temporary files. Bear in mind that not all custom settings live within the home folder. As such, restoring from the backup may not restore all your previous settings.  

```
#!/bin/bash

# Configuration
SOURCE_DIR="$HOME"
DEST_DIR="/path/to/your/debian/server/backup" # Replace with your actual backup directory
EXCLUDE="--exclude=Downloads --exclude=.cache --exclude=tmp --exclude=temp --exclude='*.tmp' --exclude='*.log'" --exclude=.var/app/com.valvesoftware.Steam" # Adjust as necessary
SERVER_USER="your_username" # Replace with your actual server username
SERVER_ADDRESS="your.server.address" # Replace with your actual server address

# Get current date
CURRENT_DATE=$(date +"%Y-%m-%d")
CURRENT_YEAR=$(date +"%Y")
CURRENT_MONTH=$(date +"%m")

# Define backup directories
MONTHLY_BACKUP="${DEST_DIR}/monthly/${CURRENT_DATE}"
YEARLY_BACKUP="${DEST_DIR}/yearly/${CURRENT_YEAR}"

# Create directories if they don't exist
ssh ${SERVER_USER}@${SERVER_ADDRESS} "mkdir -p ${MONTHLY_BACKUP}"
ssh ${SERVER_USER}@${SERVER_ADDRESS} "mkdir -p ${YEARLY_BACKUP}"

# Perform rsync backup
rsync -avz --delete ${EXCLUDE} ${SOURCE_DIR}/ ${SERVER_USER}@${SERVER_ADDRESS}:${MONTHLY_BACKUP}/

# Create yearly backup if it's January
if [ "${CURRENT_MONTH}" == "01" ]; then
    ssh ${SERVER_USER}@${SERVER_ADDRESS} "cp -al ${MONTHLY_BACKUP} ${YEARLY_BACKUP}"
fi

# Rotate monthly backups, keeping only the last 3
ssh ${SERVER_USER}@${SERVER_ADDRESS} << EOF
cd ${DEST_DIR}/monthly
ls -1tr | head -n -3 | xargs -d '\n' rm -rf --
EOF

# Print completion message
echo "Backup completed successfully!"
```
You can use cron or systemd/timer to schedule. For the above, I will be using systemd.

## Other resources
Arch Linux Wiki https://wiki.archlinux.org/title/Lenovo_ThinkPad_T14s_(AMD)_Gen_3  
No particular tweaks are necessary but it could nevertheles be helpful
