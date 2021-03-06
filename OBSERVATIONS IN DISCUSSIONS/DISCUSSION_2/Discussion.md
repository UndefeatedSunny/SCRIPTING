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
   
## 6) we know soft link contain path.....if we create a soft link of a file....then create another soft link of that soft link...and make 2-3 soft link....sir if we delete any soft link in between will it show the path to file???
    
    Let's say we have a file f1.

    We create a soft link to this file f1_soft

    Then, we create another soft link to this f1_soft as f1_soft_soft.

    Now the hierarchy will be: (as will be the output of ls -l)
    f1_soft -> f1
    f1_soft_soft -> f1_soft

    Now if we delete f1_soft, the link f1_soft_soft -> f1_soft will become broken (will be highlighted by red colour in ls -l)   
    CONCLUSION -->>
    Hierarchy will get break...
    
## 7) Why are hard links not allowed for directories?

https://askubuntu.com/questions/210741/why-are-hard-links-not-allowed-for-directories#:~:text=The%20reason%20hard-linking%20directories,ln%20-s%20target%20link%20

## 8) Extension not matters, Linux automatically Recognized it.
    In linux,
    There's no such thing as extensions of a file.

    For example:
    touch f1 and touch f1.txt
    Will create regular files and "f1" and "f1.txt" are  names of those files.

## 9) We make soft link using ln -s command in case of directory While using cp -s working fine for file but not working in case of directory.

    Possible reason:

    When cp operates on a directory, -r switch is required to perform copy operation recursively i.e., 
    copy each and everything from source dir to destination dir.
    Now, if we try to creat soft links alongwith using -r, it would mean we are creating soft links recursively. 
    (for each sub dir as well as file inside the source dir) as well which shouldn't be allowed.
    
    As an example:

    Directory source has contents:

    files: f1, f2
    Dirs: d1, d2

    Now if we try to do the same (use -r and -s together):

    cp -rs source source_link

    What it will represent:
    Create a soft link source_link for the directory source recursively i.e., create soft links for f1, f2, d1 and d2 inside source_link 
    (not possible because source_link is a soft link and not a directory which can actually contain something)

    Hence, in this case, source_link will be created as a directory which will be copy of the directory source.

## 10) MAN & HELP 

    Man: displays the manual of a command in an interactive way. You can search for keywords inside the manual page and when done, 
    exit the manual page using q.
    Also, it shows the general information regarding a command like name, synopsis, description, author, documentation links, etc. 
    (Basically like a reference manual)

    Help: prints the related information about the command on the shell itself. i.e., prints everything at once 
    and gives the control of the terminal back. You can't search for a keyword or interact in this case.
    Help gives a brief info about the command and it's switches.

    Also, help is a bash command (limited to bash shell) and manual is a linux command.

## 11) FACT on soft link 

    They aren't loyal to the original file.

    For example:

    Say I have a file f1 in CWD, and i create a soft link like:

    ln -s f1 f1_soft,

    And now, if I try to move this soft link to some other directory,

    2 things can happen:

    1) if the new directory doesn't have a file named f1, this link will be broken

    2) if there's a file f1 in the new directory, this soft link will start pointing to that file since it only has the path "f1" inside it.

    That's why it's advisable to use absolute paths while creating soft links
    
## 12) ANSI-C Quoting

https://www.gnu.org/software/bash/manual/html_node/ANSI_002dC-Quoting.html

