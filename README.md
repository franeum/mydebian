# mydebian

## add user to sudoers

```bash
su
sudo adduser <user> sudo
```

N.B. perhaps `useradd` instead `adduser`

## for debian 12 on laptop

edit `/etc/default/grub`:  
substitute:  
`GRUB_CMDLINE_LINUX_DEFAULT="quiet"`  
with  
`GRUB_CMDLINE_LINUX_DEFAULT="intel_idle.max_cstate=1"`  

run  
`sudo update-grub`  

## bashrc

add these lines to .bashrc file:

```bash
alias ll='ls -la'
alias cl='clear'
alias cd..='cd ..'
alias aggiorna='sudo apt update && sudo apt -y upgrade'
alias spegni='systemctl poweroff'
alias riavvia='systemctl reboot'
alias batt='upower -i $(upower -e | grep BAT) | grep --color=never -E "state|to\ full|to\ empty|percentage"'
```

If `bash` terminal doesn't open at home dir, install `policycoreutils` and execute these commands as root:

```bash
restorecon -r -v /home
```

## on mx-linux

`bashrc` file:

```bash
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

## if /home is empty

Install xdg-user-dirs and then:

```bash
LC_ALL=C.UTF-8 xdg-user-dirs-update --force
```


## DWA-181 wireless dongle install

follow these instructions:

https://github.com/morrownr/88x2bu-20210702

## stampante EPSON EPL-6200L

[link](https://forum.ubuntu-it.org/viewtopic.php?t=426071)

### wget gpg

```bash
sudo apt-get install wget gpg
```

### vscode

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg
```

```bash
sudo apt install apt-transport-https
sudo apt update
sudo apt install code
```

### node 16 (+ npm)

```bash
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt install nodejs
```

## neovim

### installation

```bash
sudo apt install snapd
sudo apt install nvim
```

In `.bashrc`, add `/snap/bin` to PATH:

```bash
export PATH=$PATH:/snap/bin
```

### install vim-plug

```bash
curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

In file `init.lua` you insert reference to a plugin. After this, you can call from `nvim` this command
```bash
:PlugInstall
```
