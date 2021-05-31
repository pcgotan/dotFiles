# Setup ZSH

## Install ZSH
```
#first install the basic utilities

sudo apt-get install curl wget git
sudo apt-get install zsh
```

## Zsh Plugins
```
# zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions

zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting

# Add this tine is .zshrc
plugins=(git zsh-autosuggestions zsh-syntax-highlighting extract)

```

## Install Oh-My-Zsh
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
# or
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

## Install powerlevel10k Theme
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc.

# Update the ~/.oh-my-zsh/oh-my-zsh.sh file at the end (If needed)

# Load the theme
if [ ! "$ZSH_THEME" = ""  ]; then
  if [ -f "$ZSH_CUSTOM/$ZSH_THEME.zsh-theme" ]; then
    source "$ZSH_CUSTOM/$ZSH_THEME.zsh-theme"
  elif [ -f "$ZSH_CUSTOM/themes/$ZSH_THEME.zsh-theme" ]; then
    source "$ZSH_CUSTOM/themes/$ZSH_THEME.zsh-theme"
  elif [ -f "$ZSH_CUSTOM/themes/$ZSH_THEME/$ZSH_THEME.zsh-theme" ]; then
    source "$ZSH_CUSTOM/themes/$ZSH_THEME/$ZSH_THEME.zsh-theme"
  else
    source "$ZSH/themes/$ZSH_THEME.zsh-theme"
  fi
fi

# To configure the powerlevel10k theme
p10k configure

# If any issue arises, try rebooting the device
```
