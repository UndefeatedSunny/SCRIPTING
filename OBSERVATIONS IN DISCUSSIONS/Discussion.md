Let's quickly take a look at the questions that came up in the last session:

1) Why ls -s and stat commands show different size in blocks and what is IO block in stat command

2) What is Birth in the output of stat command

So, here are the explanations for these questions:

1) firstly we need to understand the difference between the two commands:

ls command prints the details as per the linux operating system whereas stat prints the details according to file system being used (there are many different file systems (NFS, ZFS, etc.) but we don't need to go deep into that for now).

Hence,
ls -s command gives the file size in blocks of 1024 bytes (1KB) whereas stat command considers blocks of 512 bytes (based on the file system) that's why you'll always see stat command printing the blocks twice the number being displayed by ls -s command.

Next, the IO Block in the stat command shows the fundamental block size (memory) to be read or written at once (as per the file system).
Currently, the default file system in linux is NFS which allocates 4096 bytes (4KB) as the IO Block size.

2) Birth in the stat command ideally shows the file creation time but it's not applicable in linux that's why we see a hyphen '-' in that section.
