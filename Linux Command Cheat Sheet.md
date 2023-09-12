# Linux Commands Cheat Sheet by [Rahul G](https://github.com/Rahulgj3)

A collection of commonly used Linux commands to enhance your productivity.

### Basics

- `sudo`: Run the given command as the root user.
- `ls`: List the contents of a directory.
- `cd`: Change directory.
- `cat`: Concatenate files together and print them to the screen (`stdout`).
- `touch`: Create a file.
- `w`: Print what other users are running.
- `man`: Manual page viewer.
- `apropos`: Manual page searcher, Same as `man -k cmd`.
- `history`: Print the command history to the terminal.
- `echo`: Print text to the terminal.
- `env`: Print the current environment variables.
- `whoami`: Display the user running the commands.
- `lastlog`: Shows the last time any user on the system has logged in.
- `df`: Shows the size of all the filesystems.

### Text

- `wc`: Text count.
- `grep`: Text searcher.
- `nano`, `vim`, `emacs`: Text editors.
- `less`, `more`: Text viewers.
- `awk`, `sed`: Text manipulators.
- `head`, `tail`: Text readers.

### Shell Redirection Operators

- `cmd > file`: Send the output of the command to a file.
- `cmd >> file`: Append the output of the command to a file.
- `cmd 2> file`: Send Standard Error (`stderr`) to a file.
- `cmd 2> /dev/null`: Send `stderr` to null (discard all error output).
- `cmd < file`: Use the contents of `file` as input to `cmd`.
- `cmd <<EOF`: Provide input to `cmd` until `EOF` is encountered.
- `cmd1 | cmd2`: Send the output of `cmd1` to `cmd2`.
- `cmd1 ; cmd2`: Run `cmd1`, then `cmd2`.
- `cmd1 && cmd2`: Run `cmd2` if `cmd1` is successful.
- `cmd1 || cmd2`: Run `cmd2` if `cmd1` is not successful.


### Keyboard Shortcuts

- `[up arrow]`: Move up in the command history.
- `[down arrow]`: Move down in the command history.
- `[left arrow]`: Move the cursor left.
- `[right arrow]`: Move the cursor right.
- `[TAB]`: Autocompletion.
- `[SPACE] cmd`: In some shells, will not save the command to the history file.
- `Ctrl+a`: Move the cursor to the front of a command.
- `Ctrl+e`: Move to the cursor to the end of a command.
- `Ctrl+r`: Reverse search history.
- `Ctrl+c`: Terminate the current running command or clear the terminal of the command about to run.
- `Ctrl+Shift+c`: Copy the selected text out of the terminal window.
- `Ctrl+Shift+v`: Paste into the terminal window.
- `Ctrl+q`: Send the current command to the queue for one command before it repopulates the terminal.
- `Ctrl+l`: Clear the terminal.

### Processes

- `top`: Output top running processes.
- `kill`: Send signals to a process or stop a process.
  
 ### Jobs

- `cmd &`: Run the command in the background as a job.
- `jobs`: List all running jobs.
- `Ctrl+z`: Send the current running process to the background and suspend it.
- `bg %n`: Background job ID `n`.
- `fg %n`: Foreground job ID `n`.
- `kill %n`: Kill job ID `n`.
- `kill -SIGNAL %n`: Send a given SIGNAL to job ID `n`.
- `disown %n`: Disown the job ID `n` so it will run even if the terminal exits.



### Bang (!) Commands

- `!!`: Re-run the previous command.
- `sudo !!`: Very helpful for running the previous command with root privileges.
- `!n`: Re-run a specific command from the history using its number.
- `!$`: Last argument from the previous command.
- `!foo`: Re-run the last command starting with 'foo'.
- `!foo:p`: Print the previous command starting with 'foo'.

### Networking

- `ifconfig`: Lists the current networking interfaces and information about them, like the assigned IP addresses.
- `ip addr`: Like `ifconfig`, lists the current interfaces and associated IP addresses.
- `ss`: Lists active networking sockets.
- `nc`: Opens a network socket.

### Remote Network Connections

- `ssh`: Use the Secure Shell application to log into a remote host.
- `ftp`: Use the File Transfer Protocol to download/upload files to a remote host.
- `telnet`: Interact with network sockets.

### Web Builtins

- `curl`: Interact with files, webpages, and API endpoints.
- `wget`: Download files over the network.
  <br><br>
  
****
> Note: For more detailed information about each command, including available options, syntax, and usage examples, consult the respective manual pages using the `man` command. For example, to view the manual page for a command, you can type `man command_name` in your terminal.
