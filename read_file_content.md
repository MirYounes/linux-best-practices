# Cat

The simplest way to view text files in Linux is the cat command. It displays the complete contents in the command line without using inputs to scroll through it.

    cat {file_path}

# Head

Sometimes the information needed is in the first lines of a file. In that case, use the head command to view the first ten lines of a file in Linux

    head -n {line_number} {file_path}

use the -n flag with the head command to display the desired number of lines, starting from the beginning of a given file.

# Tail

    tail -n {line_number} -f {file_path}

A user can select how many lines the command should display by passing the  -n flag (where n is an integer).

Another helpful flag used with the tail command is -f. It outputs the last ten lines of a file by default, but it also keeps displaying new entries as the file is updated. This function is beneficial when viewing the latest updates in log files to troubleshoot an issue. If you only want to use this functionality, you can use the tail -f command, and it will only display the entries that appeared in the file after running the command.

# More
Another way to view file contents in Linux is the more command. It displays a file in the terminal, one page at a time. While using the more command, the Enter key scrolls through the file line by line, or the Space key scrolls one full screen at a time. Finally, you can close the file by pressing the Q key.

    more {file_path}

# Less
While more is a handy command, it does come with a drawback. After closing a file, its contents stay written in the terminal window, filling it with text, forcing users to either clear the window or scroll back up to find something. It can also be slow, as it loads the entire file though displaying only one page at a time.

That’s where the less command comes in handy. It’s very similar to more, but with the benefit of not keeping all the text in the terminal window. The less command also comes with a built-in search function, allowing you to highlight the parts of the file for which you are looking. To search with less, press the forward slash key followed by the text you want to search.

    less {file_path}

# Tac
Another exciting way to display the contents of a file in Linux is in reverse order. To do so, use the tac command. It is similar to cat but reversed, reading and displaying the file starting from the last line.

For better readability, pipe the tac command into less to scroll through the file. Users accomplish piping using the desired command, the pipe character, and the other command. 

    tac {file_path}| less

# Grep
While not used for displaying the contents of a file, the grep command is handy for filtering the output of commands. For example, grep works for searching for specific text in a file.

    grep -i -c -n -l {file_path} {search_term}
    grep {file_path} '{space_separated_search_term}'
    grep {file_path} {search_term1}|{search_term2}

### Options

- c: Count the number of lines in which the string exists
- i: Perform a case-insensitive search for the specified string
- n: Prints the line number along the line containing the specified string
- string1|string2: Find and prints multiple strings from a file

In addition, pipe the output of other commands through grep, narrowing the search to what we are looking for in the file.

Here is an example of piping the output from the head command into the grep command.

    head -20 /proc/cpuinfo | grep AMD

Similarly, you can use the ^ meta character with the grep command to display all the matching strings that begin with certain characters.

For instance, the following command pipes the env command output as an input to grep and displays variables that begin with "HO":

    env | grep ^HO
