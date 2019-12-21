# Tips

Tips for making your linux experience more enjoyable.

## Bash auto-complete case insensitive. 
Create .inputrc file that icludes /etc/inputrc and sets completion-ignore-case On.

```bash
if [ ! -a ~/.inputrc ]; then echo '$include /etc/inputrc' > ~/.inputrc; fi
echo 'set completion-ignore-case On' >> ~/.inputrc
```
