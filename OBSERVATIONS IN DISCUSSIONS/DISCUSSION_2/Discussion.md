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
