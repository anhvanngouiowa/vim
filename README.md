Python google style

~/.vim/indent/python.vim

Load Solarized: by using terminal.app preferences
Solarized Terminal w/Monaco 13pt

Solarized Dark - Monaco 13.terminal is my customized version of the OS X solarized terminal files by Tomislav Filipčić. The only change is that the font size has been set to 13pt from 11pt because I have a huge monitor and don't want to squint when I work in the terminal.


- Mac OS:
   brew install bash-completion
   add following code to the end of ~/.bash_profile:
   _fab_completion() {
	       COMPREPLY=()

	       # Fab in the path?
	       #/usr/bin/which -s fab || return 0
	       #/usr/bin/which fab 2> /dev/null || return 0

	       # Fabfile in this folder?
	       #[[ -e fabfile.py ]] || return 0

	       local cur="${COMP_WORDS[COMP_CWORD]}"

	       local tasks=$(fab --shortlist 2>/dev/null)
	       COMPREPLY=( $(compgen -W "${tasks}" -- ${cur}) )
	       }

    if [ -f /usr/local/etc/bash_completion ] && ! shopt -oq posix; then
        . /usr/local/etc/bash_completion
        complete -o nospace -F _fab_completion fab
        #complete -F _fab_completion fab
    fi

    complete -F _fab_completion fab

    $. ~/.bash_profile

