# mydebian

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
