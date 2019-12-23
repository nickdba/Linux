# Tips

Tips for making your linux experience more enjoyable.

## Bash auto-complete case insensitive

Create .inputrc file that icludes /etc/inputrc and sets completion-ignore-case On.

```bash
if [ ! -a ~/.inputrc ]; then echo '$include /etc/inputrc' > ~/.inputrc; fi
echo 'set completion-ignore-case On' >> ~/.inputrc
```

## Cowsay fortune

Install few programs

```bash
sudo -i
apt install fortune cowsay boxes
vi /etc/bash.bashrc
```

Add the following at the end of /etc/bash.bashrc (or ~/.bashrc for current user)

```bash
# cowsay magic
if [ -x /usr/games/cowsay -a -x /usr/games/fortune -a -x /usr/bin/boxes ]; then
    fortune | cowthink -f `ls /usr/share/cowsay/cows/ | shuf -n1` -n | boxes -d columns
fi
```
