# Lab 2


## Permissions
### chmod 123 file_name
- here 123 are in octal and have individual personality
 - the numbers are in octal 
 
#### chmod abc
- a is for owner(u)
- b is for group(g)
- c is for others(o)

### chmod u+x file
- means add execute permission to user(owner)
### chmod u-x file
- means remove execute from owner

## Change owner,etc
#### Using sudo (super do)'
##### Change Owner
- sudo chown "username" file3.txt

    Output:

    [sudo] password for User: "Need password to do these tasks with sudo
##### Change Group
- Change chown to chgrp

## File Searching
Find files and dir. using various criterions(name,size,location etc)
- ## -name
    - find -name "file1.txt"
        - .Desktop/folder1/file1.txt
        - Case Sensitive
    
    - find -iname "file1.txt"
        - Not Case Sensitive
    - #### Using Directory
        -find ~/Desktop -iname "filename.txt"
- ## With file extension
    -find -name "*.txt"
        - Gives every file with txt extension
- ## Search by type
    - We can search with type like file or folder
        
        - find -type f  
            - f means file
        - find -type d
            - d means Dir
        - find -type l
            - l means link
- ## Search by size
    - We can search according to size
        - find -size <+/-> N <c,k,M,G >
            - here
            - "+"means greater than N size
            - "-"means less than N size
            - c means byte
            - k means kb
            - M means mb
            - G means gb
- ## by modification time
    - We can search by modification time (days)
        - find -mtime 0
- ## search for specific patterns within files
    - is case sensitive 
    - also can find words merged with other worlds 
        - eg: can find hello from "abc<b>hello</b>abc"
    - search with keyword in a file
        - grep "keyword" filename
        - Output:
            - It will print all the lines with keyword and highlight them 
    - search in dir
        - grep -r "keyword" ~/path
        - Output
            - it will print all the line wiht keywords(highlighted) and show path of file in whic they are
    - search with line numbers
        - grep -n "keyword" /path
        - Output
            - it print print all the lines and all with line numbers against them
- ## We can club these find methods
## Archiving and Compressing
- ### tar : archive files and dir into a single file
    - tar -cvf "myfiles.tar" file1 file2 file3
        - c means compress
        - v means checking on which files was the operation made
        - try -czvf will make files.tar.gz
    - tar -xvf "myfiles.tar"
        - x means extract
        - since we used we we saw whats inside the tar ie on which files was operation made
        - try -xzvf it will use files.tar.gz
- ### zip : compresing the files
    - zip "filename.zip" file1 file2
    - unzip "filename.zip" 
- ### gzip :compress file more efficient
    - instead if making a new zip file containing the file it make the files ."txt".gz
    - gzip file1.txt
    - gunzip file.txt.gz
    - it will remove the compressed file
    - for stop this
    - use -k it will make .txt.gz and keep .txt in that also
## Creating links for files
- ### Hard Link
    - Removing the files doesnt not delete actual data untill all the hard_link fiels are deleted 
    - ln file1.txt "file1_hardLink.txt"
    - Any change done to normal file is updated in this link
    - If we delete normal file hardlink file will have no issues
    - We cant make hard link for dir.
- ### Symbolic Link
    - Removing the files break the link b/w them  <b>(Broken/ Dangling link)</b>
    - ln -s file1.txt "file1_symLink.txt"
    - Any change done to normal file is updated in this link
    - If we delete normal fil softlink will not work
    - We can make soft link for dir.

    

        








## Adding new user
- sudo adduser abcdcdcd





# HW 
- How to create diiferent users in one VM
- Try gzip