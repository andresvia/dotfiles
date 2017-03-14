#!/bin/bash
# added because SC2148
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

add_to_path() {
  some_path="${1}"
  found=no
  IFS=:
  for path in $PATH; do
    if [[ "${path}" == "${some_path}"  ]]; then
      found=yes
      break
    fi
  done
  unset IFS
  if  [[ "${found}" == "no" ]]; then
    PATH="${some_path}:${PATH}"
  fi
}

clean_path() {
  paths=(${PATH//:/ })
  clean_path="${paths[0]}"
  IFS=:
  for path in $PATH; do
    found=no
    for cleaned_path in $clean_path; do
      if [[ "${path}" == "${cleaned_path}"  ]]; then
        found=yes
        break
      fi
    done
    if  [[ "${found}" == "no" ]]; then
      clean_path="${clean_path}:${path}"
    fi
  done
  unset IFS
  PATH="${clean_path}"
  export PATH
}

# last wins
add_to_path "$HOME/bin"
add_to_path "$HOME/.rbenv/bin"
add_to_path "$HOME/.pyenv/bin"
add_to_path "$HOME/.local/bin"

export PATH

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi
