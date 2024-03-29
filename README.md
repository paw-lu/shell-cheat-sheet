# Shell cheat sheet

Many users
don't write shell scrips often enough
to internalize its syntax,
but just often enough
to have to search search the same things over and over again.

This is a quick cheat sheet
for myself and others
to make those occasional scripts
go by a little smoother.

## References

- [Advancing the Bash Shell](http://samrowe.com/wordpress/advancing-in-the-bash-shell/)
- [Effective Shell](https://effective-shell.com/)
- [Linux Productivity Tools](https://www.usenix.org/sites/default/files/conference/protected-files/lisa19_maheshwari.pdf)
- [Shell Scripting Tutorial](https://www.shellscript.sh/)
- [Shell Style Guide](https://google.github.io/styleguide/shellguide.html)
- [Shell productivity tips and tricks](https://blog.balthazar-rouberol.com/shell-productivity-tips-and-tricks.html)
- [Ten Things I Wish I’d Known About bash](https://zwischenzugs.com/2018/01/06/ten-things-i-wish-id-known-about-bash/)
- [explainshell](https://explainshell.com/)
- [reasonable-shell-script](https://github.com/mjambon/reasonable-shell-script)
- [Standard Shell](https://devmanual.gentoo.org/tools-reference/bash/index.html)
- [Minimal safe Bash script template](https://betterdev.blog/minimal-safe-bash-script-template/)
- [Linux Terminal Tools](https://ketancmaheshwari.github.io/pdfs/LPT_LISA.pdf)

## Shell scripts

Commands most often used
in shell scripting.
Many of these descriptions
were pulled from
the [Shell Scripting Tutorial](https://www.shellscript.sh/quickref.html).

| Command    | Description                                                                 | Example                                                             |
| ---------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `&`        | Run the previous command in the background                                  | `ls &`                                                              |
| `&&`       | Logical AND                                                                 | `if [ "$foo" -ge "0" ] && [ "$foo" -le "9"]`                        |
| `\|\|`       | Logical OR                                                                  | `if [ "$foo" -lt "0" ] \|\| [ "$foo" -gt "9" ]` (not in Bourne shell) |
| `^`        | Start of line                                                               | `grep "^foo"`                                                       |
| `$`        | End of line                                                                 | `grep "foo$"`                                                       |
| `=`        | String equality (cf. -eq)                                                   | `if [ "$foo" = "bar" ]`                                             |
| `!`        | Logical NOT                                                                 | `if [ "$foo" != "bar" ]`                                            |
| `$$`       | PID of current shell                                                        | `echo "my PID = $$"`                                                |
| `$!`       | PID of last background command                                              | `ls & echo "PID of ls = $!"`                                        |
| `$?`       | exit status of last command                                                 | `ls ; echo "ls returned code $?"`                                   |
| `$0`       | Name of current command (as called)                                         | `echo "I am $0"`                                                    |
| `$1`       | Name of current command's first parameter                                   | `echo "My first argument is $1"`                                    |
| `$9`       | Name of current command's ninth parameter                                   | `echo "My ninth argument is $9"`                                    |
| `$@`       | All of current command's parameters (preserving whitespace and quoting)     | `echo "My arguments are $@"`                                        |
| `$*`       | All of current command's parameters (not preserving whitespace and quoting) | `echo "My arguments are $*"`                                        |
| `-eq`      | Numeric Equality                                                            | `if [ "$foo" -eq "9" ]`                                             |
| `-ne`      | Numeric Inquality                                                           | `if [ "$foo" -ne "9" ]`                                             |
| `-lt`      | Less Than                                                                   | `if [ "$foo" -lt "9" ]`                                             |
| `-le`      | Less Than or Equal                                                          | `if [ "$foo" -le "9" ]`                                             |
| `-gt`      | Greater Than                                                                | `if [ "$foo" -gt "9" ]`                                             |
| `-ge`      | Greater Than or Equal                                                       | `if [ "$foo" -ge "9" ]`                                             |
| `-z`       | String is zero length                                                       | `if [ -z "$foo" ]`                                                  |
| `-n`       | String is not zero length                                                   | `if [ -n "$foo" ]`                                                  |
| `-nt`      | Newer Than                                                                  | `if [ "$file1" -nt "$file2" ]`                                      |
| `-d`       | Is a Directory                                                              | `if [ -d /bin ]`                                                    |
| `-f`       | Is a File                                                                   | `if [ -f /bin/ls ]`                                                 |
| `-r`       | Is a readable file                                                          | `if [ -r /bin/ls ]`                                                 |
| `-w`       | Is a writable file                                                          | `if [ -w /bin/ls ]`                                                 |
| `-x`       | Is an executable file                                                       | `if [ -x /bin/ls ]`                                                 |
| `( ... )`  | Function definition                                                         | `function myfunc() { echo hello }`                                  |
| `$( ... )` | Expand command. May also use \`.                                            | `CURRENT_DIRECTORY="$(pwd)"`                                        |
| `<()`      | Treat command output as a file.                                             | `diff <(grep somestring file1) <(grep somestring file2)`            |

## Terminal

Shortcuts for working on the terminal.

| Command              | Description                                                                       | Example                                                                                                                                              |
| -------------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `!-n`                | Return the `n`th latest command. `!-1` refers to the last command.                | `❯ touch file.txt`<br><br> `❯ cat file.txt` <br><br> `❯ !-2` <br><br> `❯ touch file.txt`                                                             |
| `!!`                 | A shortcut for the last command. Equivalent to `!-1`.                             | `❯ touch file.txt`<br><br> `❯ cat file.txt` <br><br> `❯!!` <br><br> `❯cat file.txt`                                                                  |
| `^command1^command2` | Repeat the previous command, but replace `command1` with `command2`.              | `❯ cat file.txt` <br><br> `❯ ^cat^rm` <br><br> `❯ rm file.txt`                                                                                       |
| `!^`                 | Return first argument of the last command.                                        | `❯ diff file1.txt file2.txt` <br><br> `❯ !^` <br><br> `❯ file1.txt`                                                                                  |
| `!$`                 | Return last argument of the last command.                                         | `❯ diff file1.txt file2.txt` <br><br> `❯ !$` <br><br> `❯ file2.txt`                                                                                  |
| `:n`                 | Return the `n`th command. Can run `!:1-$` to get all arguments from last command. | `❯ diff file1.txt file2.txt` <br><br> `❯ !!:2` <br><br> `❯ file2.txt`                                                                                |
| `:h`                 | Return the parent folder of the filename                                          | `❯ grep hi Users/paulo/text.txt` <br><br> `❯ echo !!:h` <br> `Users/paw-lu`                                                                          |
| `{1..2}`             | Loop number range.                                                                | `❯ touch file{1..2}.txt` <br><br> `❯ ls` <br> `file1.txt file2.txt`                                                                                  |
| `{1..4..2}`          | Loop number range at set increment.                                               | `❯ touch file{1..4..2}.txt` <br><br> `❯ ls` <br> `file1.txt file3.txt`                                                                               |
| `~`                  | A shortcut for the home directory.                                                | `❯ echo ~` <br> `Users/paw-lu`                                                                                                                       |
| `~+`                 | A shortcut for the current directory.                                             | `❯ pwd` <br> `Users/paw-lu/folder` <br><br> `❯ echo ~+` <br> `Users/paw-lu/folder`                                                                   |
| `~-`                 | A shortcut for the previous directory.                                            | `❯ pwd` <br> `Users/paw-lu/folder` <br><br> `❯ cd ~` <br><br> `❯ echo ~-`<br>`Users/paw-lu/folder`                                                   |
| `cd -`               | Navigate to the previous directory.                                               | `❯ pwd` <br> `users/paw-lu` <br><br> `❯ cd folder`<br><br> `❯ pwd` <br> `Users/paw-lu/folder` <br><br> `❯ cd -` <br><br> `❯ pwd` <br> `Users/paw-lu` |
