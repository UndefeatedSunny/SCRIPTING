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
    
## 4.) We already know that everything in our system is located in Root directory. So, Can we change our user/owner name like we can do in Windows ?

    You can change the username like this:-

    usermod -l new_name old_name

    usermod does not require any permission as you're just changing the login-name for your system.

## Can we also change the machine name too?
    
    Yes but for that, you will need sudo permissions and we generally avoid to do it as it may break your system.
    
    There are files:
    /etc/hostname

    And 
    /etc/hosts

    Where we need to change the hostname.
    
## 5.) What is the difference between $ and :/home$ and :~$     

    $ is a special character used to extract values from the variables.

    In the command prompt, $ represents the bash shell and hence,

    :/home$ means current working directory is /home and current shell is bash.

    AND

    :~$ means current working directory is home and the shell is bash shell.
    
## 6.) What is the difference between echo and cat?

    echo is used to print the string on the terminal but cat prints the contents of the file which we give it as argument.
    
## 7.) Why do we limit the default file creation permissions on 666?
    
    There are 2 reasons behind this:

    1) we can't let any arbitrary file have the execute permissions by default as it can put the security of the system at risk.
    Since a virus or malware-related file can get executed by mistake and result in system-corruption.

    2) most files don't need to be executable and hence, we can selectively choose what files we need to make executable.
    
## 8.) Want to make a folder named "pine 1" but when i use mkdir pine 1 it takes pine and 1 as different arguments

    Space isn't allowed as a valid character while naming files/dirs.
    
    The reason allowed is in bold is because it's not advisable to do so but we can do it.

    You can try:
    mkdir "pine 1"

    Or

    mkdir pine\ 1
    
    But you may notice while accessing the directory you don't need to start with '.  LIKE THAT -->> 'pine 1'

    As a general practice, please avoid using spaces while naming files/dirs. (PLEASE NOTE THAT POINT)
## REASON (why not prefer)
bash: cd: too many arguments
## SOLUTION
    cd pine\ 1     
    
    
    
    
    
    

    
