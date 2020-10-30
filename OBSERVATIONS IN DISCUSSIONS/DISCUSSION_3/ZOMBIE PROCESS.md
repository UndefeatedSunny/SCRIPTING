
##      rm -r ../d3 command to remove the d3 directory while I was already in d3 directory, but when the command executed successfully, In next command then too I was in d3 directory, why this is happening..?

      The shell process has d3 as its CWD which keeps its inodes on the disk allocated as long as the shell is using that directory.

      Since this directory is deleted, it becomes a zombie process that only waits for all of its handlers (utilities using that process) 
      to be closed.
      That's why, after the command 
      rm -r ../d3,

      If you try to create a file inside the CWD, it will fail since this directory is no longer physically present on the disk rather 
      it exists only as a zombie process as long as the current shell has it as CWD.
