## Chapter 6
<small>Philipp Moritzer - 21170004</small>
<hr/>

### Anatomy of a Command
```bash
$ Command [options] [arguments] //Unix command structure
- $ ls -sCF /usr/bin
- $ ls -s -C -F /etc

$ man ls //manual

$ apropos ls //finds all related files

$ whereis echo //shows where all echo related files are

$ which echo //only shows executable

```

### Meta Characters

```bash
$ Wildcard
 - ? : matches one character
 - * : matches one or more characters
 - [] : matches one of the characters in [...]
$ ls *.txt
$ ls hi?.txt
$ ls hi[12357].txt
```

### Redirection

```bash
$ ls > ls.txt

$ sort < /etc/group //sorts a textfile alphabetically
$ sort < /etc/group > sort.txt

$ find / -name 'hi.txt' 2> /dev/null // find a file by name. Permssion denied messages will be omitted.

$ find /export/home -name 'hi.txt' > out.txt 2>&1
$ find /export/home -name 'hi.txt' 2> out.txt 1>&2
```

### Pipes

The Output of the first process is the input of the second process.

```bash
$ cho | wc // word count who command
$ cat /etc/passwd | grep unix30 // shows only lines that contain unix30
$ echo $PATH // shell variable path
$ ${PATH}${TERM} //shell variable value
$ echo today is `date`
$ \$PATH Escape the dollar sign
```