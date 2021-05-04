## Chapter 8 - Advanced Tools
<small>Philipp Moritzer - 21170004</small>
<hr/>

### Regular Expression

- Pattern that represents texts or strings

- Representing a varying array of characters

- Often include Metacharacters  
Metacharacters: Characters that represent another set or group of characters or commands
  - . : a character
  - [] : any one inside of it
  - \* : zero or more characters
  - [^.*]: Do NOT match any inside of it
  - ^.* : Match at the beginning
  - ^.\*[.*]: Match at the beginning and match inside in it
  - $ : Match at the end of line
  - \\ : Escape special character
  - ? : Zero or one Character
  - [a-z]: Match all occurences of any single letter 

### FTP (file transfer protocol)

```bash
$ ftp 21170004@comunix.seoultech.ac.kr # connect to Comunix server using FTP
$ sftp -p 21170004@comunix.seoultech.ac.kr #connect to Comunix server using FTP while specifying the port with -P
$ !dir # shows content of your current local directory
$ pwd # displays current working directory remotely
$ lcd .. # change local directory
$ put <filename> # upload file to server using current local directory as source and current remote directory as destination
$ get <filename> # download file using the directories
$ quit # exit (s)ftp session
```
### grep

Prints lines that has the string:
```bash
$ grep unix30 /etc/passwd # prints lines that contain unix30 in /etc/passwd file
$ cat /etc/passwd | grep unix30 # same as above but with using the pipe operator
$ grep -v # opposite (not matching the expression)
$ grep -i # ignores the case
```

### find

Finds files in the directory structure  

```bash
$ find / -name core # finds files with the name core
$ find /export -user unix300 # finds files specifiyng the user name
$ find /export -size +2000k # finds files specifiyng the file size
$ find / -perm -4000 # finds files specifiyng the persmission
$ find / -name core 2> /dev/null # omits the error messages
```

### sort

```bash
$ sort -t: +1 /etc/group #sorts the /etc/group file using the second column divided by the ':'
$ head /etc/passwd | sort -r > pass.txt # sorts the /etc/passwd file and sorts it in reverse order and puts the output in the pass.txt file
$ -f # ignore case
$ -r # reversed order
$ -t # set delimiter
$ -o # set output file
```

### Tee/script

Tee: Split output (Screen and file)  
```bash
$ ps -ef | tee ps.txt #prints current process status to the console and saves it to ps.txt
$ telnet 10.10.54.75 | tee telnet.txt # saves the whole telnet session to file telnet.txt
```

Script: Record interactive login session  
```bash
$ script -a filename # saves session to filename
$ exit # end script
```

### Unix utilites

```bash
$ wc # word count (lines/words/characters)
$ cut # extract character or words
$ cut -c1-5 /etc/passwd # extract characters 1-5 from /etc/passwd file
$ cut -d: -f 1,3 /etc/passwd # cuts by delimiter
$ paste file1 file2 # merges file1 and file2
$ tr abcd ABCD < filename # translate characters abcd to ABCD by using input filename
$ split -5 /etc/passwd # splites /etc/passwd into separate files of 5 lines
$ uniq filename # file comparison - reports or filters out repeated lines in a file
$ cmp filename # file comparison - no output if the files are the same, if they differ the comparison will be displayed by byte and line numbers where the first difference occured
$ comm file1 file2 # file comparison - output in 3 columns: lines only in file 1, lines only in file 2, lines in both files
$ diff file1 file2 # file comparison - No output if the files are same. The output will be a minimal list of diffrences between the files

```