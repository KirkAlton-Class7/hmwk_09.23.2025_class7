
# Killer Coda Exercises
## <i>Linux: Lesson 1</i>

Home Directory
macOS: `/Users/<YOUR-USERNAME>/`

`mkdir` make directory
`rmdir` remove directory
`rm -rf <directory>
- `-r` is recursive. This continually applies the command on all folders within the directory.
- `-f` is force. This forces execution of the operation, regardless of system behavior that may interfere or ask for confirmation. **Use with caution, and only if you know what you're doing.**
`touch` create a file
`rm` remove a file

`mv` move file
```sh
mv <./object-path> <./target-directory>
```
Examples
```sh
mv ./chewbacca.jpg /users/kirk/Documents/photos/Columbian
mv /users/Documents/photos/chewbacca.jpg /users/kirk/Documents/photos/Japanese
```

`cd ~` Jumps to the home directory

`pwd` = print working directory
Shows current directory in terminal

For relative file paths, use ./

Ex. Current directory: /users/kirk
Navigate to TheoWAF

```sh
./TheoWAF
```

You can also just type the path without ./
```sh
TheoWAF
```

Both commands navigate to:
```sh
/users/kirk/TheoWAF
```

`cd ..` Takes you up one directory
Add another `.` to go up +1 directory

`cd -` Takes you to the previous directory

`ls` Lists the contents of the current directory (aka "Lemme See" or "List Sh!t")

`ls --color=no` Turns off color for ls command

`ls --color=yes` Turns on color for ls command

`clear` Clears the terminal screen

What you pass after the command `-` or `--` is an argument
`-` is used to pass one letter arguments like "i" or "h"
`--` is used to pass arguments that contain more than one letter. Typically it will be an english word.

`ls -l`
`l` means long listing format.
This provides user friendly information about permissions, hard links, owner, groups, size, date and time, and filename.

`ls -n`
Works like `ls -l` but changes the user-friendly names to User Identifier (UID) and Group Identifier (GID) numbers.

For hidden objects, Linux uses `.` at the beginning of the object name. These are called `dotfiles`.

`ls -a`
Lists **all** files, including dotfiles and special entries. This shows dotfiles, regardless of their location.
When viewing results:
`.` is the current directory
`..` is the parent directory


`ls -A`
	Lists **almost all** files (excludes `dotfiles`)
	Excludes special entries `.` (current directory) and `..` (parent directory)

`.` and `..` can also be used with `ls`

`ls .` lists files in the current directory
`ls ..` lists files in the parent directory

Sorting
`ls` sorts alphabetically by default

Linux has different time stamps
`atime` - the last time a file was accessed
`mtime` - the last tie a file was modified
`ctime` - last metadata modification time (permissions changed, location of the file changed, etc.)

`date` - shows current time and date

`ls -t` lists files and sorts by last modification time (newest first)

Run `ls -ltu` to put in long list `-l`, sort by modification time `-t`, and show last modification time `u` 

The most useful way to run sorting commands is with the following arguments:

`ls -lta`  
- Lists files in long list form, sorted by last access time (`atime`), and shows last access time.
    
`ls -ltu`  
- Same as `ls -lta` but doesn't show `dotfiles` 
`ls -ltc`  
- Lists files in long list form, sorted by last status change time (`ctime`), and shows time of last metadata change (like permission, ownership change, etc.).

Everything in Linux, including arguments, is case-sensitive.
`ls -s` shows file size in blocks
`ls -S` sorts files by size (largest first)

The most useful way to sort by size is by running `ls -lS`

`--human-readable`, also known as `-h` transforms information to human readable forms 

`ls lh` shows long list with human readable text. For example, instead of 156940 blocks, file size shows as 154K.

`ls -lSh` shows long list, sorted by size, and in human readable format

`--format` Can be used when scripting and `ls` is used for input for other parts of the script.

`ls --format=long` same as `ls -l`

`ls --format=commas` same as `ls -m`
Formats the list with commas as the delimiter

`ls -lQ` prints the filenames in quotes, one file per line.

`--time-style` changes the way the date is formatted in long format

`ls -l --time-style=locale` (default for `ls -l`)
`ls -l --time-style=iso`
`ls -l --time-style=full-iso` 


`--time-style` changes the **date/time format** shown in **long listing format** (`ls -l`).
    
- Useful when you want **consistent, unambiguous timestamps** (e.g., for scripting, logs, or international teams).
    


`ls -l --time-style=locale`
Uses your system’s local date format (default).
- Example: `Sep 27 14:32`

`ls -l --time-style=iso`
Uses ISO 8601 date format (short).
 - Example: `2025-09-27 14:321`

`ls -l --time-style=long-iso`
Uses ISO format with year included.
 Example:`2025-09-27 14:32`

`ls -l --time-style=full-iso`
Full ISO 8601, including seconds and timezone.
- Example: `2025-09-27 14:32:05.123456789 -0400`

You can also pass a custom format:
```bash
ls -l --time-style="+%Y/%m/%d %H:%M:%S"
```

Output:
```
2025/09/27 14:32:05
```

Useful arguments

`ls -al --author` - prints the username of the creator of a file
`ls -ald` - prints directory level permissions
`ls -ali` - prints inodes
`ls -alR` - recursively prints all subdirectories
`ls -alr` - prints lists in the reverse order
`ls -alSr` - prints list by file size, in the reverse order
`ls --version` - prints the version of the binary
`ls --help` get help with commands and arguments
<br>
<br>

## <i>Linux: Lesson 2</i>
`man man` prints all pages of the Linux manual
`man` + `<command>` - prints the manual page for that command command
Example: `man ls`  prints the manual page for the `ls` command

`whatis <command>` - shows a short description of the functionality of a command.
ex `whatis ls` shows information about the `ls` command.

`man -k <command>` searches for the given command through all manual pages and returns them as output.
`man -w <command>` returns the location of the file from where the pages is rendered

<br>
<br>

### <i>Linux: Lesson 3: Directories</i>

`mkdir <dir-name>{IndexStart# ..IndexEnd#}`
Creates multiple directories.
Example: `mkdirk tesdir{1..10}` creates 10 directories (testdir1 . . . testdir10)

`mkdir -p<dir-Name>/<sub-dir-name>{IndexStart#..IndexEnd#}
Creates a parent directory that is filled with the number of indexed sub directories, named accordingly.
Tip: Index can be added to parent directory to create multiple parent directories as well.
Example: `mkdir -p parent_directory{1..25}/child_directory{1..50}`
Creates 25 folders named "parent_directory#" filled with 50 subdirectories named "child_directory#"

`ls -l <dir-path>` list files in a directory (absolute or relative path)
Example: `ls -l /users/kirk/Documents` or if in Documents, `ls -l my_class_documents

`echo $HOME` prints the absolute path of the home directory
`cd $HOME` navigates to home directory 
`cd ~` navigates to home directory (quicker)
`cd` navigates to the home directory **(quickest)**