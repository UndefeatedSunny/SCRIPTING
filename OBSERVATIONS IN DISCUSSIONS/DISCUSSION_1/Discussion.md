## 1.) $SHELL

    $SHELL contains the absolute path of the binary of your current shell.

    Each and every command or shell in linux has a binary (the file containing executable code) associated with it.

    The binaries are not created/modified or saved when you run the commands.

    These binaries are always present in your linux system. Whenever you type any command on the shell, 
    it invokes the binary of that command and executes it.

    To know where the binary of a specific command is present, we can use which command.

    For example:
    which echo
    which cat

## 2.) When is used sudo /bin/bash then my user name changes to root but when I typed ls it is showing same file I have on my Home directory.

    The sudo command allows you to run programs as another user, by default the root user with administrative privileges

    sudo command is password protected.

    So this makes your username changes to root but the files remains the same.
    
## 3.) bunny@bunny-VirtualBox:~/Desktop$ echo -e "Hello\
##     > \nGuys\n\
##     > How are you ?"
##       Hello
##       Guys
##       How are you ?

    In bash,
    \ is used to continue writing the command in the next line.

    For example:
    echo "This is an example \
    > of multiple line command"

    This will come in handy when you will start writing scripts containing long commands to make it look more organized and understandable.
