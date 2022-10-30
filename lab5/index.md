# Find
### find -type c

This opintion will return the file or folder with type `c`. `c` can be `f`, which means file, or `d`, which means directory. 

- d: directory
- c: font device file
- b: block device file
- p: named column
- f: general file
- l: symbolic link
- s: socket

Example:

    find -type d           
    .
    ./.git
    ./.git/info
    ./.git/hooks
    ./.git/branches
    ./.git/refs
    ./.git/refs/heads
    ./.git/refs/tags
    ./.git/refs/remotes       
    ./.git/refs/remotes/origin
    ./.git/objects
    ./.git/objects/pack       
    ./.git/objects/info       
    ./.git/logs
    ./.git/logs/refs
    ./.git/logs/refs/remotes       
    ./.git/logs/refs/remotes/origin
    ./.git/logs/refs/heads
    ./lib
    ./technical
    ./technical/911report
    ./technical/biomed
    ./technical/government
    ./technical/government/About_LSC
    ./technical/government/Alcohol_Problems  
    ./technical/government/Env_Prot_Agen     
    ./technical/government/Gen_Account_Office
    ./technical/government/Media
    ./technical/government/Post_Rate_Comm    
    ./technical/plos

### find -empty
Find the empty file. 

Example:

    find -empty
    ./.git/branches    
    ./.git/refs/tags   
    ./.git/objects/info

### find -path p
Find the file that maths path p.

Example: 

    find -path "./lib*"
    ./lib
    ./lib/hamcrest-core-1.3.jar
    ./lib/junit-4.13.2.jar

***

# grep

### grep -c
Show how many linens match the style we are searching for.

Example:

    grep -c 'IPF' ./technical/biomed/rr166.txt
    40

### grep -n
Show the number of line.

Example: 

    grep -n 'lower' ./technical/biomed/rr166.txt
    270:          2 ) and found a significantly lower
    314:        2 metabolites was lower in IPF
    437:        significantly lower prostacyclin:thromboxane ratio. We
    438:        hypothesize that the lower PGI

### grep -o
Only show the content that matchs.

Example:

    grep -o 'lower' ./technical/biomed/rr166.txt
    lower
    lower
    lower
    lower

***

#less

### less -e
When reaching the end of the file, exit the file automatically. 

Example:

    ...opps, no example for this one. 

### less -x n
Make the 'tab' as given n spaces.

Example:

    less test.txt
                one tab here
                    two tabs here
                            three tabs here
    test.txt (END)
    
    less -x 2 test.txt
      one tab here
        two tabs here
          three tabs here
    test.txt (END)

### less -N
Show the line number.

Example:

    less -N test.txt
          1         one tab here
          2                 two tabs here
          3                         three tabs here
    test.txt (END)





















