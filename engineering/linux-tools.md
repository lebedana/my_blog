# Linux tools

* [Ranger](http://macappstore.org/ranger/)
* vimx 
* [Iterm2](%20https://www.iterm2.com/features.html)
* \*\*\*\*[**ZSH**](https://www.freecodecamp.org/news/how-to-configure-your-macos-terminal-with-zsh-like-a-pro-c0ab3f3c1156/) ****
  * [Setup guide for likes ](https://medium.com/@elviocavalcante/5-steps-to-improve-your-terminal-appearance-on-mac-osx-f58b20058c84)
* fzf - [fuzzy search ](https://github.com/junegunn/fzf)

```text
fzf                             # Fuzzy file lister
fzf --preview="head -$LINES {}" # Fuzzy file lister with file preview
vim $(fzf)                      # Launch Vim editor on fuzzy found file
history | fzf                   # Fuzzy find a command from history
cat /usr/share/dict/words | fzf # Fuzzy search a dictionary word
```

