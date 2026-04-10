Following are installation steps.

# Install Oh My Zsh (non-interactively)
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" " --unattended"

# Install fzf: general-purpose, interactive command-line fuzzy finder
# Prerequisite for zsh's fzf-tab plugin
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install

# Clone personal dotfiles and apply zsh/tmux configs via GNU Stow.
# Remove any existing ~/.zshrc created by the Oh My Zsh installer so stow can place its own.
rm -f ~/.zshrc && \
    git clone https://github.com/Bai-YunHan/Dotfiles.git ~/dotfiles && \
    cd ~/dotfiles && \
    stow zsh && \
    stow tmux

# Set zsh as root's default login shell so tmux spawns zsh in new panes/windows
chsh -s /bin/zsh