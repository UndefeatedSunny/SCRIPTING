      In UNIX, each file/directory is stored on the memory alongwith some meta-data.

      Typically the size allocated to small files and directories is 4 blocks and if files/dirs exceed this size, 
      then they are allocated 8 blocks and so on.

      So in the SS, the number 4 is the number of blocks allocated to the succeeding files and total 16 is the number of blocks hence, 
      allocated to the directory m2.

      You can also see the manual of ls command.
      
      -s is used to display the size allocated in blocks.
      
