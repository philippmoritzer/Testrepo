## Chapter 7 - Vi Editor
<small>Philipp Moritzer - 21170004</small>
<hr/>

### Vi Modes

```bash
$ vi # Opens Vi Editor
$ vi filename # Opens Vi Editor with file 'filename'
```

![](../../images/2021-04-08-14-18-37.png)

### Moving within a file
- h,j,k,l (left, down, up, right)
  ![](../../images/2021-04-08-14-19-43.png)

- 0,^(left most), $(right most)
- [Enter] Next line
- Ctrl + F : One Page Forward
- Ctrl + B : One Page Backwards
- Ctrl + U : Half Page Up
- Ctrl + D : Half Page Down
- :0, :1 - First Line
- :\$ - Last Line
- :100 - 100th Line
- Ctrl + % ( {<--->}) Move in between brackets
- :set nu - displays line numbers

### Searching

- /string  
    search string(forwards)
- n  
    Go to next string
- N  
    Go to previous string
- ?string  
    Search backwards

### Exit / save

- :q - quit 
- :w - write to the file
- :wq - write and quit
- q! - exit without saving
- :wq! - overwrite and exit
- ZZ - save and exit
- :x - exit
- :w filename - write to file filename
- :r filename - read and insert file filename

### Insert Mode

- i - insert
- a - append
- o - insert from next line
- [esc] - go to command mode

### Delete 

- x - Delete 1 Character
- 5x - Delete 5 Characters
- dd - Delete 1 line
- 3dd - Delete 3 lines
- D - delete remaining line of this line from the cursor
- J - join current line and next line
- i[enter][esc] - separate line

### Change

- r - replace 1 character  
  - ra - 1 character is changed to 'a'
- 3r - replace 3 characters
  - 3ra[esc] - 3 Characters are changed to 'aaa'
- cw - change 1 word
  - cwabc[esc] - word is changed to 'abc'
  - cwab cd 12[esc] - word is changed to 'ab cd 12'
- 3cw: change 3 words
  - 3cwabc[esc] - 3 words are changed to 'abc'
  - 3cwab cd 12[esc] - 3 words are changed to 'ab cd 12'

### Undo / Redo

- u - Undo (Cancel Change)
  - uu - Cancel undo

- . - redo
  - /abc //search 'abc'
  - cwABCD[esc] //change to 'ABCD'
  - n. //search next and change to 'ABCD'
  
### Copy and move
```bash
$ Copy a line
- yy -> [move] -> p

$ Copy several lines
- 3yy -> [move] ->p

$ Move a line
- dd -> [move] -> p

$ Move several lines
- 3dd -> [move] -> p
```

### Running commands
- :%s/abc/ABCD/g
  - change all 'abc' to 'ABCD' in file
- :10,$ s/abc/ABCD/g
  - change all 'abc' to 'ABCD' from line 10 to end of file
- :0,$ s/[Ctrl + V][CTRL+M]//g
  - delete all ^M character in file
- :100,200 w! filename
  - save line 100 to 200 to file filename 

### Miscellaneous
- :set nu - show line number
- :set nonu - hide line number
- :sh - go to sh temporary
  - return to vi by $exit
- :!pwd run a command in vi
  - press enter to edit continously
- Ctrl + l - reset screen