## Chapter 5 - Customizing Working Environment
<small>Philipp Moritzer - 21170004</small>
<hr/>

### System Variables

```bash
$PS1 - Shell apperance
$PS1 = '$ '
```
Output:

![](../../images/2021-03-30-10-15-40.png)

```bash
$PATH - executables
```

### Local/environment Variable

Local variable: affects current shell only

Environment variable: affects sub-shell as well
```bash
$ a = 3 #local variable
$ export a # exposes variable
```

Example:
```bash
$ a=3; b=5
$ echo $a $b # 3, 5
$ export b
$ sh // start sub-shell
$ echo $a #no result
$ echo $b #5
$ exit #return to parent shell
```

### Variable Commands

```bash
$ set # see all variables and its values
$ set | grep PATH # shows the value of the PATH variable
$ env # lists exported variables
$ echo $variable # shows variable value
$ export # makes a variable an env variable
$ unset # delete variable
```

### Absolute/Relative Path

- Absolute Path
  - Starts with the root path (/)
  - Example: /usr/bin/ls
- Relative Path:
  - does not start with /
  - references to the current directory
  - Example ../dir/hi.txt

. : Current directory
.. : Parent directory
~ : User's home directory

### Shell Types
- Bourne Shell (sh)
  - Original Unix shell
- C Shell (csh)
  - Syntax as the C programing language
- Korn Shell (ksh)
  - Combines sh and csh and has some additional functions
- Bourne Again Shell (bash)
  - same as sh but has additional functions


### Shell initialization files

/etc/profile: global configratuion file

Sh: ~/.profile

Ksh: ~./profile, ~/.kshrc

Bash: ~/.bashrc_profile

### Alias

```bash

$ alias ls='ls -l' # Substituting one term to another
$ unalias ls
```
