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

### python 3.10.4
```bash
sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev libbz2-dev
wget https://www.python.org/ftp/python/3.10.4/Python-3.10.4.tgz
tar -xf Python-3.10.4 && cd $_
./configure --enable-optimizations
make -j 4
sudo make altinstall (sudo make install if you want replace default binary python)
```
