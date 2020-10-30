    This is one of the special cases.

    To understand what's happening here, we will need to understand some basics:

    When we give 003, as per the umask rules, for file, the permissions will be derived by subtracting 003 from 666 which is equals 663 
    and corresponds to permissions:
    
    rw-rw--wx

    But, if you see closely, user and group don't have execute permissions but others do! Which shouldn't be allowed as ideally, 
    if the owner of the file as well as the group isn't allowed to execute, then others definitely shouldn't be allowed as well.

    Hence, these permissions won't be a valid combination and that is why umask gives the permissions corresponding to 002 (previous mask).

    => umask 003 and umask 002 will yield same permissions for a file




    You can also try 005 which ideally should yield 666-005 = 661. i.e., rw-rw---x
    But the permissions given will correspond to 004 i.e.,
    662: rw-rw--w-





