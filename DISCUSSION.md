 ##                                       DAY 3

## 1.) Built-in command don't have any binary file associated with them but Non-Built-in does?

    built-in commands are shell-specific i.e., they have their definition inside the binary of the shell itself and hence, 
    don't need a separate executable code/binaries.
    
## 2.) What is the role of -exec switch, Can we use it anywhere else like we use it in removing files having same pattern ?

    So, -exec switch in find command is used to execute some command on the file/dir found by the find command.

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
    
    Placeholders will just get replaced by the filenames being processed by the find command one by one.

    So, in first iteration, the find command will give "./file" to the rm command hence, the command will be:

    rm ./file

    For the second time, "./file1" will be returned and hence, the command will be:

    rm ./file1

    And similarly, 3rd time, the command will be:

    rm ./file2

    \;
    Is just a command separator (like we use on the shell to execute multiple commands one after the other)
    
##  Why have we used command separator in the end if we are writing find command and then rm command

    The -exec switch will assume everything written before \; as an argument to the command and hence, it's important to notify the end of this command using this separator \;
    
##  IN CASE OF PIPE OPERATOR :-
    
    Similar to that but the pipe operator takes the complete stdout to the next command as an stdin.

    Here, if you use pipe operator, the next command will receive
    ./file
    ./file1
    ./file2
    As stdin.

    And as we can see, it is a list of files and to operate on this list, we may have to use xargs command (should be covered in class).

    As an overview, xargs basically takes a list and passes the arguments as an stdin.
   
##  parantheses to group the ranges

    find . \( -size +1c -a -size -3c \) -o \( -size +4c -a -size -200c \)
    
## 3.) wildcard in tar command ?

    *,?,[]
    
    In linux, there are only these 3 main wild cards.
    Further, you will study some more meta-characters that are used for pattern matching when regular expressions will be covered.
    
## 4.) Facts on rm -R command

    -R switch is just for deleting the dirs and their contents recursively.
    
    When a write-protected file is deleted, a prompt appears for the confirmation irrespective of the -R switch.

    In other cases, the file will he deleted without seeking any confirmation from the user.
    
    If you want to force delete these files, you may use -f switch to ignore the prompt for write-protected files
    
## 5.) Join Command Problem -_- : 

    f1:	f2: 
    A 1	A 1 1
    b 2	B 2 2
    C 3	C 3 3

    then on executing the command -> join f1 f2 
    the output should be merging only till the place where the contents are same, ie till the 1st row as told in the class.
    But I'm getting the output with the 1st row and 3rd row contents, i.e,
    o/p:-
    A 1 1 1
    C 3 3 3
    
    SOLUTION :-
    
    join - join lines of two files on a common field

    And in the description, you may find:
    For each pair of input lines with identical join fields, write a line to stdout. The default join field is the first....

    Hence, as you can see in your files,
    The first field in the second lines don't match and hence, that line us ignored OR it skips the unmatched field.

    The output is produced only for the lines having identical join fields (first field by default)

##  NEW PROBLEM ARISES 
    
    f1:	f2: 
    a 1	A 1
    b 4	B 2
    c 3	C 3
    
    join -1 2 -2 2 f1 f2
    
    1 a A
    join: File1:3: is not sorted: c 3
    
    EXPLANATION :-
    
    For Join Command field must be sorted but here 4 is coming before 3,So,It is only goes to 1  and then field is not sorted so it is printing error.
    
    If you see the manual of the join command, there's an important note mentioned over there:

    FILE1 and FILE2 must be sorted on the join fields......
    In this case you are using 2nd field from both file1 and file2 but in file1, the join fields are not in sorted order and 
    hence, a warning is printed when 3 is encountered after 4.
