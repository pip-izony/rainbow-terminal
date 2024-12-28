# rainbow-terminal
Make each terminal tab colorful for easier identification and a more vibrant workspace.

## To-Do List with examples
Develop it as a plugin.

### .bashrc
``` shell
function check_directory() {
    if [[ "$PWD" == "/root/work" ]]; then
        # Change background color
        echo -e "\033]11;#1e90ff\007"

        # Change prompt
        PS1="\[\033[32m\]\u@\h:\w\$ \[\033[0m\]"
    else
        # Restore default background and prompt
        echo -e "\033]11;#000000\007"
        PS1="\[\033[37m\]\u@\h:\w\$ \[\033[0m\]"
    fi
}

# Set the hook for every command prompt refresh
PROMPT_COMMAND=check_directory
```

### .zshrc
``` shell
chpwd() {
    if [[ "$PWD" == "/root/work" ]]; then
        # Change background color
        echo -e "\033]11;#1e90ff\007"

        # Change prompt
        export PS1="%{$(tput setaf 2)%}%n@%m:%~%#%{$(tput sgr0)%} "
    else
        # Restore default background and prompt
        echo -e "\033]11;#000000\007"
        export PS1="%{$(tput setaf 7)%}%n@%m:%~%#%{$(tput sgr0)%} "
    fi
}
```
