# run for every zsh

typeset -U path PATH
path=(~/.local/bin $path)
export PATH

skip_global_compinit=1

export XDG_CONFIG_HOME="$HOME/.config"
export XDG_DATA_HOME="$HOME/.local/share"
export XDG_STATE_HOME="$HOME/.local/state"
export XDG_CACHE_HOME="$HOME/.cache/"

## let gnome-keyring-daemon handle unlocking of (password protected) ssh keys
export SSH_AUTH_SOCK=$XDG_RUNTIME_DIR/keyring/ssh

## enable mangohud for all vulkan games
export MANGOHUD=1

function _source {
  for file in "$@"; do
    [ -r $file ] && source $file
  done
}

# Be more restrictive with permissions; no one has any business reading things
# that don't belong to them.
if (( EUID != 0 )); then
  umask 027
else
  # Be even less permissive if root.
  umask 077
fi
