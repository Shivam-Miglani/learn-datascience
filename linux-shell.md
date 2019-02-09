### Concepts
* **Shell**: is a command interpreter for Linux kernel.

#### Redirection and Pipelining
* `>` redirects the standard output to a file. The existent contents of the file are overwritten.
` ls /home>testdir/testfile`
* `>>` redirects the standard output to a file. The existent contents of the file are kept, and the new information is appended at the end of the file.
`ls /home >> testdir/testfile`
* `|` is used to redirect the output of the command as input to another command.
`head -110 digits_all.fileids | tail -40` selects last 40 lines of the first 100 lines, i.e., lines 70 to 110.

