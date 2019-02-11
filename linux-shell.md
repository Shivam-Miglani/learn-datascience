### Concepts
* **Shell**: is a command interpreter for Linux kernel.

#### Redirection and Pipelining
* `>` redirects the standard output to a file. The existent contents of the file are overwritten.
` ls /home>testdir/testfile`
* `>>` redirects the standard output to a file. The existent contents of the file are kept, and the new information is appended at the end of the file.
`ls /home >> testdir/testfile`
* `|` is used to redirect the output of the command as input to another command.
`head -110 digits_all.fileids | tail -40` selects last 40 lines of the first 100 lines, i.e., lines 70 to 110.


#### Help commands
* `man command_name` or `command_name -h` or `command_name --help`
* `--verbose`

#### list
* `ls -l`: longer listing format including owners, permissions, size and date modified.
* `ls -a`: hidden files
* `ls -al`
* `ls -h`: file sizes in human readable format instead of bytes.

#### Remove
* `rm -rf`: recursively and forcefully. **Last resort method**

#### Nano
* `nano`
* Ctrl+o to save file. Enter name or press Enter.
* Ctrl+x to exit nano.

#### mkdir
* `mkdir -p /path/newfolder/newfolder2`

#### ps
* `ps`: List processes
* `ps aux`: List all processes in detail running on the system

#### kill
* `kill PID`: Get PID from `ps aux` and kill the offending process. If it refuses to die, `kill -9 PID` terminates the process by any means.
* `killall program`: It kills *by name* all instances of said program. E.g., `killall firefox` kills all sessions of the firefox.
* `xkill`: GUI way of killing things. Shows a skull and bones icon and next window clicked would be killed.

#### tee
* `tee`: sends output to both a file and the terminal. It is used in conjunction with `|` in order to take th command output and send it  elsewhere. Example: `dmesg| tee boot.txt` would run the command `dmesg` which shows the initial boot info and  `|` sends the output of `dmesg` to `tee`, which then sends it to terminal and to the log file `boot.txt`.

#### Disk space
* `df -h`: quick checkup
* `du -cksh target_name`: calculate size of a file or folder quickly.

#### History
`history`: history of commands.
`history -c`: clear the history.

#### File Execution

* Need to execute a GUI program from the terminal?  Simply type the `program_name` (case sensitive!) and it will launch.  **This will render the current terminal unusable**.  Closing the terminal while the program is open will kill the program.  A better way is to background the program, using `program_name &` and then typing the word exit at the terminal to close it and keep the process running.
 
* Need to run a GUI program with root rights from the terminal?  Prefix it with `gksudo` or `gksu` and not `sudo`.  Using `sudo` to launch GUI applications is a bad habit and should be avoided.

#### Sources Used
1. https://community.linuxmint.com/tutorial/view/100
2. 

