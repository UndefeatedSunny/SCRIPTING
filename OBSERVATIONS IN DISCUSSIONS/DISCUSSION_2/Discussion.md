## 1) Why ls -s and stat commands show different size in blocks and what is IO block in stat command

## 2) What is Birth in the output of stat command

EXPLANATION :-

    1) firstly we need to understand the difference between the two commands:

    ls command prints the details as per the linux operating system whereas stat prints the details according to file system 
    being used (there are many different file systems (NFS,   ZFS, etc.) but we don't need to go deep into that for now.

    Hence,
    ls -s command gives the file size in blocks of 1024 bytes (1KB) whereas stat command considers blocks of 512 bytes 
    (based on the file system) that's why you'll always see stat command printing the blocks twice the number being displayed by 
    ls -s command.

    Next, the IO Block in the stat command shows the fundamental block size (memory) to be read or written at once (as per the
    file system). Currently, the default file system in linux is ext2/ext3 which allocates 4096 bytes (4KB) as the IO Block size.

    2) Birth in the stat command ideally shows the file creation time but it's not applicable in linux that's why we see 
    a hyphen '-' in that section.
    
## 3) How can we display file/directory creation time and is it different from any of time stamps i.e. access time, modification time or change time ?

    In linux, the creation time isn't stored.
    But linux only allows keeping traces of modification, access and change time.
    This may also depend on the file system being used.
    Some file systems allow to keep a trace of file creation time while others don't.

    "is it different from any of the time stamps": yes it is as the name suggests it's the time your file is created.

## 4) Regarding Visibility of Files

    All files starting with '.' are considered as hidden for both the shell and the GUI.
    
    The backup files (typically created by the editors like gedit and vi) ending with '~' are considered as hidden in the GUI 
    but not in the shell.
    
    Shell and GUI are different.
    For shell, only files starting with '.' are hidden and hence you can only see them -a switch.
    
## 5) when we create a soft link for a file and then we change its permissions using chmod command suppose to 555 even then the permissions of the soft link remain as 777.

    SOFT LINK -->>
    The soft link just adds an indirection to the file path.
    Hence, if you try to run a command over a soft link like:

    chmod 555 soft_link_to_f1

    The shell will interpret it as:

    chmod 555 /path/to/f1

    Since, soft link contains nothing but the path of the original file and that's why the permissions of the file would be modified 
    and not those of the soft link itself.
    
    HARD LINK -->>
    A hard link is like an actual copy of the file except for the fact that it has the same inode number,
    (implying it points to the same memory location).

    We can say a hard link is just another name for the same file.

    Hence, if you try to modify permissions of the hard link, you are actually modifying the permissions of that memory location and now, 
    these changes will be reflected in all other hard links as well as the original file.
    
    
    
    
