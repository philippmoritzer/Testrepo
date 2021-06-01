## Chapter 18 - Backup Tools

<small>Philipp Moritzer - 21170004</small>
<hr/>

### Backup Media Types

- Magnetic Tapes
- CD/DVD-Rom
- Zip drives
- Hard drive/network backup
- USB


### Backup Types

- Full backup
  - entire system is backed up
- Differential Backup
  - Only backups that has changed since last full backup
- Incremental Backup
  - Backup on what has changed since the completion of any type of backup

### tar
- Tape Archive
- Options:
  - c - create
  - t - show contents
  - x - extract
  - v - verbose
  - f - set filename
```bash
Options:

$ tar cvf mydir.tar mydir # all contents under mydir directory will be bundled to mydir.tar
$ tar tvf mydir.tar # shows content of bundled file
$ tar xvf mydir.tar # extracts tar file
```

### compress
Compress a file to a smaller file
```bash
$ compress mydir.tar # compress mydir.tar file -> mydir.tar.Z
$ uncompress mydir.tar.Z # uncrompresses mydir.tar
$ gzip mydir.tar # -> mydir.tar.gz
$ gzip -d mydir.tar.gz # extract file
$ gunzip mydir.tar.gz # extract file
```

### Example
```bash
$ tar cvf mydir.tar mydir
$ compress mydir.tar
$ ftp 10.10.54.75
ftp> bi
ftp> put mydir.tar.Z
ftp>quit
$ telnet 10.10.54.75
$ uncompress mydir.tar.Z
$ tar xvf mydir.tar
```