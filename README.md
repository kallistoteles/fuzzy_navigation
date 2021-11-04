## Fuzzy Navigation
This is not something I uniquely created (what is?) or some crazy new stuff, but it changed how I fundamently move around in the terminal.
And I use it extensively, so I hope you can take it, expand on it and make it your own.
If you haven't already, check out all the cool [examples in the fzf wiki.](https://github.com/junegunn/fzf/wiki/examples)
## Concept
Instead of tabbing your way to a file, catalog or program - find it super quick as a part of your command execution.

## Setup
Add the following to your `.zshrc`
```
# find directory
alias -g fd='$(find ~/ -not -path ".*\/\.*" -type d | fzf)'
# find file
alias -g ff='~/$(cd ~/ && fzf)'
# find content
alias -g fc='$(grep --line-buffered -r --include=\*.{md,py,txt,sh,scad,yml,json} "" * 2> /dev/null | fzf | sed "s/:.*//g")'
```
and as an extra, if you are a pacman user, this one from the [arch wiki](https://wiki.archlinux.org/title/fzf) has also helped me a lot.
```
# find package
alias -g fp='$(pacman -Slq | fzf --multi --preview "pacman -Si {1}")'
```

## Usage examples
`cd fd` change to any sub-directory under your homedir

`less ff` read any file under your homedir tree

`vi fc` search for any content and edit that specific file under current directory

`sudo pacman -S fp` if someone could expand this to include the AUR - I would be greatful! :)

## Dependencies
fzf

zsh, or something that can work similarly as global alias in zsh

