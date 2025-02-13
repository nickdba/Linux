# Bash

Edit the `.bashrc` file from home folder.

Paths for autocompletion

```bash
export CDPATH=.:~:<path1>:<path2>:<path3>
```

Add history search

```bash
bind '"\e[A":history-search-backward' # history with arrow up key
bind '"\e[B":history-search-forward' # history with arrow down key
```

Lastly preffer to keep the aliases separated in a `.bash_aliases` file. This is the default configuration in Ubuntu and derivated distros.

```bash
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```


## Bash aliases

```bash
# Custom aliases

## Apps shortcuts
alias ll='ls -lah --color=auto'
alias vi='vim'
alias svi='sudo vim'
alias grep='grep --color=auto'
alias egrep='egrep --color=auto'
alias mkdir='mkdir -pv'
alias h='history'
alias j='jobs -l'
alias df='df -H'
alias du='du -ch'
alias top='htop'

## Go To Places
alias ggit='cd <path to git>'
alias ..='cd ..'
alias ...='cd ../..'
```