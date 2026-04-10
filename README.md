Following are installation steps.

<u>Step 1</u> : 
Install Oh My Zsh non-interactively.
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" " --unattended"
```

<u>Step 2</u> :
Install fzf. fzf is a general-purpose, interactive command-line fuzzy finder
Prerequisite for zsh's fzf-tab plugin:
```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install
```

<u>Step 3</u> : 
Clone personal dotfiles and apply zsh/tmux configs via GNU Stow.
Remove any existing ~/.zshrc created by the Oh My Zsh installer so stow can place its own.
```bash
rm -f ~/.zshrc && \
    git clone https://github.com/Bai-YunHan/Dotfiles.git ~/dotfiles && \
    cd ~/dotfiles && \
    stow zsh && \
    stow tmux
```

<u>Step 4</u> : 
Set zsh as root's default login shell, so tmux spawns zsh in new panes/windows
```bash
chsh -s /bin/zsh
```