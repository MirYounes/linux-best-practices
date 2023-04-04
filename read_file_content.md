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


# Wc
wc stands for word count. As the name implies, it is mainly used for counting purpose.

- It is used to find out number of lines, word count, byte and characters count in the files specified in the file arguments
- By default it displays four-columnar output.
- First column shows number of lines present in a file specified, second column shows number of words present in the file, third column shows number of characters present in file and fourth column itself is the file name which are given as argument

### Syntax:
    wc [OPTION]... [FILE]...

### Options:
- l: prints the number of lines present in a file
- w: prints the number of words present in a file
- c: displays count of bytes present in a file
- m: displays count of characters from a file

### Examples:
- count line of single file:
```
    $ wc -l state.txt
    5 state.txt
```
- count line of more than one file:
```
    $ wc -l state.txt capital.txt
    5 state.txt
    5 capital.txt
    10 total
```
- count all files and folders present in directory:
```
    $ ls gfg
    a.txt 
    b.txt  
    c.txt  
    d.txt  
    e.txt  
    geeksforgeeks  
    India

    $ ls gfg | wc -l
    7
```


# Cut
The cut command in UNIX is a command for cutting out the sections from each line of files and writing the result to standard output. It can be used to cut parts of a line by byte position, character and field. Basically the cut command slices a line and extracts the text. It is necessary to specify option with command otherwise it gives error. If more than one file name is provided then data from each file is not precedes by its file name.

### Syntax:
    $ cut -d {delimiter} -f {field number} {file_path}


# Sort:
SORT command is used to sort a file, arranging the records in a particular order. By default, the sort command sorts file assuming the contents are ASCII. Using options in the sort command can also be used to sort numerically. 

### Syntax:
```
    $ sort [Options] ... [File]
```

### Options:
- o: Unix also provides us with special facilities like if you want to write the output to a new file, output.txt, redirects the output like this or you can also use the built-in sort option -o, which allows you to specify an output file.
```
    $ sort inputfile.txt > filename.txt
    $ sort -o filename.txt inputfile.txt
```
-  r: ou can perform a reverse-order sort using the -r flag. the -r flag is an option of the sort command which sorts the input file in reverse order i.e. descending order by default.
-  n: To sort a file numerically used –n option. -n option is also predefined in Unix as the above options are. This option is used to sort the file with numeric data present inside.
-  nr: To sort a file with numeric data in reverse order we can use the combination of two options as stated below.
-  u: To sort and remove duplicates pass the -u option to sort. This will write a sorted list to standard output and remove duplicates.
-  c: This option is used to check if the file given is already sorted or not & checks if a file is already sorted pass the -c option to sort. This will write to standard output if there are lines that are out of order. The sort tool can be used to understand if this file is sorted and which lines are out of order

# Uniq:
The uniq command in Linux is a command-line utility that reports or filters out the repeated lines in a file. 
In simple words, uniq is the tool that helps to detect the adjacent duplicate lines and also deletes the duplicate lines. uniq filters out the adjacent matching lines from the input file(that is required as an argument) and writes the filtered data to the output file.
by default remove duplicates and return data.

uniq command require sorted content

### Syntax:
    $ uniq [OPTION] [INPUT]

### Options:
- c: It tells how many times a line was repeated by displaying a number as a prefix with the line.
- d: It only prints the repeated lines and not the lines which aren’t repeated.
- u: It allows you to print only unique lines.
- i: By default, comparisons done are case sensitive but with this option case insensitive comparisons can be made.
