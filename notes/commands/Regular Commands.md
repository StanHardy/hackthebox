### Post \ Pre Exploitation

- ls
- Grep 
- AWK
- Tar
- Find


#### ls
```bash
# list files
ls

# list hidden files
ls -la

# list files with human readable size
la -sh
```

#### Grep
```bash
# search for the files that contains the phrase password in it
grep -ir password

# exclude multiple strings
grep -Ev 'exclude1 | exclude 2' filename.txt

# obtain only lines starting with small letters
grep -v '[A-Z]' users.txt
```


#### AWK
```bash
# simple grab based on spaces, damnedsec cyberwr3nch hackthebox
awk '{print $1}' # output damnedsec

# multiple field seperator, obtain things only with in the delimeter
# contents of the file-> user: cyberwr3nch: damnedsec;123
awk -F: '{print $3}' users.txt # output damnedsec;123

# contents of users.txt -> user:[BLACKFIELD764430] rid:[0x451], 
awk -F"[][]" '{print $2}' users.txt # output: BLACKFIELD764430

# obtain contents from a specific line
# where x is the line number	
awk 'NR==x {print $1}'

```


#### Tar
```bash
# unzip a *.tar.gz file
tar -xzvf html.tar.gz
```

#### Find
```bash
# find with file names
find . -name user.txt 

# find and execute
find . -name '*.txt' -exec cat "{}" \;

# {} is used as the place holder and tells the follwing to as an argument
# find directories with the specified name and execute the command
find . -type d -name uploads -exec rm -rf "{}" ';'
# find and copy files 
find -name 'file.ext' -exec cp "{}" <copy_path>  \;
```

#### Monitor
```bash
# ls -la every 1 sec on a dir
watch -n 1 'ls -la'
```