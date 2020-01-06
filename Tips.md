# Tips

Tips for making your linux experience more enjoyable.

## Bash auto-complete case insensitive

Create .inputrc file that icludes /etc/inputrc and sets completion-ignore-case On.

```bash
if [ ! -a ~/.inputrc ]; then echo '$include /etc/inputrc' > ~/.inputrc; fi
echo 'set completion-ignore-case On' >> ~/.inputrc
```

## Longer sudo time

Add a line to /etc/sudoers with the new number in minutes.

```bash
sudo visudo     # Edits /etc/sudoers
```

Modify this line:
```Defaults        env_reset```  
With this line:
```Defaults        env_reset,timestamp_timeout=30```
