[LINUX] Learn linux CLI
==========

# $ ls
1. $ ls -a
  - lists all contents, including hidden files and directories
2. $ ls -l
  - lists all contents of a directory in long format
3. $ ls -t
  - order files and directories by the time they were last modified.

4. $ ls -l

        $ ls -l
        drwxr-xr-x 5  cc  eng  4096 Jun 24 16:51  action
        drwxr-xr-x 4  cc  eng  4096 Jun 24 16:51  comedy
        drwxr-xr-x 6  cc  eng  4096 Jun 24 16:51  drama
        -rw-r--r-- 1  cc  eng     0 Jun 24 16:51  genres.txt

    The -l option lists files and directories as a table. Here there are four rows, with seven columns separated by spaces. Here's what each column means:

    Access rights. These are actions that are permitted on a file or directory.
    Number of hard links. This number counts the number of child directories and files. This number includes the parent directory link (..) and current directory link (.).
    The username of the file's owner. Here the username is cc.
    The name of the group that owns the file. Here the group name is eng.
    The size of the file in bytes.
    The date & time that the file was last modified.
    The name of the file or directory.

5. $ ls -alt

- In addition to using each option separately, like ls -a or ls -l, multiple options can be used together, like ls -alt.

- Here, ls -alt lists all contents, including hidden files and directories, in long format, ordered by the date and time they were last modified.