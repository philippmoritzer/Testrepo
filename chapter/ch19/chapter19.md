## Chapter 19 - Installing Software from Source Code

<small>Philipp Moritzer - 21170004</small>
<hr/>


### Open source Licensing
- BSD License
  - Source code can be modified
  - Modification can not be redistributed
  - Adverteised so that it's clear that BSD code is used
  - Can be used as proprietary or commercial software
- GNU Public License (GPL)
  - "Copyright license"
  - Modified Software can be distributed under the same license

### Install Lynx Software
Lynx is a Text Browser

- Downloaded from lynx.isc.org
- unzip
```bash
$ PATH=$PATH:/usr/sfw/bin:/usr/ccs/bin:.
$ export PATH
$ ./configure
$ make
$ make install
```

Run Lynx

### Compile C Program
```bash
$ gcc hello.c # complies hello.c file
$ gcc -o hello hello.c # compiles hello.c and names the output file hello
$ gcc -c main.c sub1.c sub2.c # compiles 3 files in one command
$ gcc -o maketest main.o sub1.o sub2.o
$ make -f make.my # executes makefile
```

### makefile/Makefile
Schema:  
\<default target>: dependency list  
\<tab>command  
\<target>: depencdency list  
\<tab>: dependency list  
...  
\<label>:  
\<tab>: command

Example:  
```makefile
maketest: main.o sub.o sub2.o
    gcc -o maketest main.o sub1.o sub2.o
main.o : main.c my.h
    gcc -c main.c
sub1.o : sub1.c my.h
    gcc -c sub1.c
sub2.o : sub2.c my.h
    gcc -c sub2.c
clean :
    rm -f *.o maketest
```

