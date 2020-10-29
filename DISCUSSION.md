 ##                                       DAY 3

1.) WHILE Writting in Files 
     
    Please make sure you don't leave trailing spaces in the lines while editing a file. 
    It may cause confusion in the outputs of such commands like(Join).

2.) Built-in command don't have any binary file associated with them but Non-Built-in does ,what does it Signifies?

    built-in commands are shell-specific i.e., they have their definition inside the binary of the shell itself and hence, 
    don't need a separate executable code/binaries.
    
3.) What is the role of -exec switch, Can we use it anywhere else like we use it in removing files having same pattern ?

    So, -exec switch in find command is used to execute some command on thr file/dir found by the find command.

    As an example:

    Let's say I have following files in my CWD:
    file
    file1
    file2
    File
    File1
    File2

    Now, if I run the following find command:

    find . -type 'f' -name "file*"

    The find command will yield output:
    ./file
    ./file1
    ./file2

    Now, let's say I want to perform some operation on these files, e.g., remove them, I can do it using -exec switch like this:

    find . -type 'f' -name "file*" -exec rm {} \;

    Here, if you now see closely,
    We have written an "rm" command only.
    {}
    Will act like a placeholder for the files being returned by the find command.

    So, in first iteration, the find command will give "./file" to the rm command hence, the command will be:

    rm ./file

    For the second time, "./file1" will be returned and hence, the command will be:

    rm ./file1

    And similarly, 3rd time, the command will be:

    rm ./file2

    \;
    Is just a command separator (like we use on the shell to execute multiple commands one after the other)
