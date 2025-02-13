# Bash

## Bashrc

Edit the `.bashrc` file from home folder.

Customizing promt

```bash
PS1='\[\e[01;36m\][\u@\h \W]\$\[\e[m\] '
```

Paths for autocompletion

```bash
export CDPATH=.:~:<path1>:<path2>:<path3>
```

Add history search

```bash
bind '"\e[A":history-search-backward' # history with arrow up key
bind '"\e[B":history-search-forward' # history with arrow down key
```

Neofetch is also an option here

```bash
neofetch --ascii_distro Arch
```

Lastly I preffer to keep the aliases separated in a `.bash_aliases` file. This is the default configuration in Ubuntu and derivated distros.

```bash
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```


## Bash aliases

Edit the `.bash_aliases` file from home folder or create a new file if it doesn't exists.

```bash
# Custom aliases

## Apps shortcuts
alias ls='ls --color=auto'
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