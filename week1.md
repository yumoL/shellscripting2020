Yumo Luo 014810383

### Directory setup (1)
``` mkdir -p ShellScripting2020/Week1```

### Identify shift (2)
```la```, which is from ```alias la='ls -a'```

```alias cman='man --html=lynx'```

### (NON)-logins (3)
- login shell:
First ssh to the melkki.cs.helsinki.fi server: ```ssh melkki.cs.helsinki.fi```.
Then running ```ls```. The printed directories and files are with colors.
<img src="https://github.com/yumoL/shellscripting2020/blob/main/3_color.png"/>

- non-login shell:
Running ```ls``` over ssh remotely: ``` ssh melkki.cs.helsinki.fi 'ls'```. The printed directories and files are without color.

Reason: In the case of login shell, login shell executes /etc/profile. In etc/profiles, the script 
```
if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
fi
``` 
asks the shell to execute /etc/bash.bashrc, which has command aliases: ```alias ls='ls --color=auto'```.

In the case of non-login script, the shell tries to execute $HOME/.bashrc. Since there is no .bashrc file under the home directory, the shell executes the 
default ```ls``` command, which has no alias that define colors. 
