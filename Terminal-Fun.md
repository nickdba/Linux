# Terminal fun

## Fortune

Random funny and phrases.

```bash
~> fortune
```

## Boxes

Box your content.

```bash
~> echo "   Hello Wonderful World!" | boxes -d mouse
```

## Cowsay

Make the cow say mu or whatever else.

```bash
~> fortune | cowsay -f koala
```

## Neofetch

Display computer info with a nice logo design.

```bash
~> neofetch
```

## Cmatrix

You are in the matrix.

```bash
~> cmatrix
```

## Figlet

Fun way to write stuff.

```bash
~> echo Hello World! | figlet
```

## Next Level

Add the following at the end of /etc/bash.bashrc (or ~/.bashrc for current user)

```bash
# cowsay magic
if [ -x /usr/games/cowsay -a -x /usr/games/fortune -a -x /usr/bin/boxes ]; then
    fortune | cowthink -f `ls /usr/share/cowsay/cows/ | shuf -n1` -n | boxes -d columns
fi
```
