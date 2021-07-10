# Tips

Tips for making your linux experience more enjoyable.

## Bash auto-complete case insensitive

If you have root permissions and want to change this for all users

```bash
vim /etc/inputrc
set completion-ignore-case On # Add this line at the end of the file
```

Otherwise you will change this only for the current user.

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
```Defaults        env_reset,timestamp_timeout=60```

## Set the default text editor

```bash
sudo update-alternatives --config editor
```

## Pulse audio remove flat volume

```bash
sudo vi /etc/pulse/daemon.conf
 # set flat-volumes = no by removing the comment in front `;`
```
