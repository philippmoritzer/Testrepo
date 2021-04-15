## Chapter 6 - Unix Commands In-Depth
<small>Philipp Moritzer - 21170004</small>
<hr/>

### Anatomy of a Command
```bash
$ Command [options] [arguments] # Unix command structure

Examples: 
- $ ls -sCF /usr/bin
- $ ls -s -C -F /etc

$ man ls # command manual

$ apropos ls # shows all related file to this command (ls)

$ whereis echo # shows where all echo related files are located

$ which echo # only shows executable

```

### Meta Characters

```bash
$ Wildcard
 - ? # matches one character
 - * # matches one or more characters
 - [] # matches one of the characters in [...]
$ ls *.txt
$ ls hi?.txt
$ ls hi[12357].txt
```

### Redirection

```bash
$ ls > ls.txt # writes the output of ls command to ls.txt file

$ sort < /etc/group # sorts a textfile alphabetically
$ sort < /etc/group > sort.txt # same as above but puts output into sort.txt

$ find / -name 'hi.txt' 2> /dev/null # find a file by name. Permssion denied messages will be omitted.

$ find /export/home -name 'hi.txt' > out.txt 2>&1 #Puts error and output into out.txt file, errors first
$ find /export/home -name 'hi.txt' 2> out.txt 1>&2 # same as above but content first, then errors
```

### Pipes

The Output of the first process is the input of the second process.

```bash
$ who | wc # word count who command
$ cat /etc/passwd | grep unix30 # shows only lines that contain unix30
$ echo $PATH # shell variable path
$ ${PATH}${TERM} # shell variable value
$ echo today is `date` # prints current date
$ \$PATH # Escape the dollar sign
```

### Quotas

The amount of disk space for each user is allocated

```bash
$ /etc/vfstab #enable quotas option

$ quotacheck -acug /export/home # scan filesystem for disk usage, create, check and repair quota files
```