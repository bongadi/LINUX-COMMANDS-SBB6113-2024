# LINUX-COMMANDS-SBB6113-2024

Notes to introduce common commands that are used in windows subsystem for linux (wsl)

1. ### Opening Ubuntu in WSL
After you’ve installed Ubuntu in WSL, you can open it by typing wsl in your Windows terminal or search "Ubuntu" in your start menu. Once opened, you'll see a terminal window where you can enter Linux commands.

2. ### What is a Directory?
A directory is like a folder in Windows, where you store files and other directories. Think of it as a way to organize your data.

Command: `mkdir` is used to create a directory (folder).
Example:
Let's create a directory called practice.
```
mkdir practice
```
This creates a folder named "practice" where you can store files or other directories.

3. ### Navigating Directories
You are usually in the home directory when you first open Ubuntu. To move into the practice directory, you’ll use the `cd` (change directory) command.

Command: `cd` is used to move into a directory.
Command: `pwd` (print working directory) tells you where you are.
Example:
To go into your new directory, type:
```
cd practice
```
```
pwd
```
You should now be inside the practice directory. You can check your current location with `pwd`.

4. ### Creating Files
Now, let's create some files. There are different ways to do this, but we'll use the `touch` command for simplicity.

Command: `touch` is used to create an empty file.
Example:
Let's create files named fruits.txt and countries.txt.
```
touch fruits.txt countries.txt
```
This creates two empty files called "fruits.txt" and "countries.txt".

5. ### Listing Files in a Directory
To see what files are inside the practice directory, use the `ls` command.

Command: `ls` lists all the files and directories inside the current directory.
Example:
```
ls
```
You should see:
```
fruits.txt  countries.txt
```

5. ### Adding Content to the files we created
We will use `nano` to open the files and manually enter content.

Command:   nano   is a text editor you can use in the terminal.
Example:
To add fruits to fruits.txt:
```
nano fruits.txt
```
Once inside the nano editor, type the following lines:
```
Apple
Banana
Orange
Mango
Grapes
```
To save the file:

Press Ctrl + S (to save)
then
Press Ctrl + X to exit.
Do the same for countries.txt:
```
nano countries.txt
```
Add the following countries:
```
Kenya
Uganda
Tanzania
Ethiopia
Rwanda
```
Then save and exit as before (Ctrl + s, Ctrl + X).

6. ### Viewing File Content
You can now view the content using `cat`.
or if the content is large you can use the command `less` (the content will appear in the text editor, exit with Ctrl-X)

Example:
```
cat fruits.txt
```
```
cat countries.txt
```
7. ### Copying and Renaming Files
Use `cp` to copy files and `mv` to rename or move them.

Example:
Let’s copy countries.txt to nations.txt:
```
cp countries.txt nations.txt
```
To rename nations.txt to world_nations.txt:
```
mv nations.txt world_nations.txt
```
8. ### Removing Files
To delete a file, use the `rm` command.

Example:
```
rm world_nations.txt
```
9. ### Creating Nested Directories and Moving Files
We can create directories inside directories and move files between them.

Example:
Create a `data` directory inside `practice`:
```
mkdir data
```
Move `countries.txt` into `data`:
```
mv countries.txt data/
```

10. ## Introduction to Bash Scripting
A bash script is a text file containing a series of commands that the shell executes. It helps automate tasks.

Command: `bash` executes the script.
Example:
Let’s create a bash script that lists all files in a directory.

Create a file called list_files.sh:
```
nano list_files.sh
```
Add the following content:
```
#!/bin/bash
echo "Listing all files in the current directory:"
ls -la
```
Save and exit (Ctrl + S, Enter, Ctrl + X).

Execute the script:
```
bash list_files.sh
```
This script will print out all the files in the current directory with details.

11. #### Adding More Content with Nano
Let's create another file, numbers.txt, where we can add a list of numbers.

Example:
Create numbers.txt:
```
touch numbers.txt
```
```
nano numbers.txt
```
Add the following numbers:
```
1
2
3
4
5
```
Save and exit.

12. #### Basic Bash Scripting with Loops
Let’s extend your scripting knowledge by creating a simple bash script that reads the numbers in numbers.txt and prints them one by one.

Example:
Create a new file called print_numbers.sh:
```
nano print_numbers.sh
```
Add the following content:
```
#!/bin/bash
while read number; do
  echo "Number: $number"
done < numbers.txt
```
Save and exit
Execute it;
```
bash print_numbers.sh
```
This script will read through numbers.txt and print each number.

13. ## Learning more commands with a Small FASTA Sequence File
A FASTA file contains biological sequences (like DNA, RNA, or protein sequences) in a simple text format. It starts with a header line that begins with > followed by the sequence name, and the sequence data follows on the next lines.

Example:
Create a file called sequence.fasta:
```
nano sequence.fasta
```
Add the following content (a short DNA sequence for illustration):
```
>Sequence1
ATGCTAGCTAGCTCGATCGTAGCTAGCTGATCGTACG
>Sequence2
GCTAGCTAGCTAGCGGATCGATCGTAGCATCGTACGC
>Sequence3
CGTAGCTAGCATCGATCGCGATCGTACGATCGTAGCT
```
Save the file by pressing Ctrl + S, and exit with Ctrl + X.

Now you have a simple sequence.fasta file that mimics a small DNA dataset.

14. ### Viewing and Counting Lines, Words, and Characters in Files
The `wc` command (word count) allows you to count lines, words, and characters in a file.

Command: `wc` provides counts of lines, words, and characters.
Example:
```
wc sequence.fasta
```
Output:
```
6  12 152 sequence.fasta
```
6 = number of lines
12 = number of words
152 = number of characters
If you only want to count lines:
```
wc -l sequence.fasta
```
15. ### Searching for Patterns in Files Using Grep
The `grep` command is used to search for specific patterns within files. This is useful for finding sequences or specific identifiers in your FASTA files.

Command: `grep` searches for a pattern in files.
Example:
To find sequences that contain the nucleotide CGT:
```
grep "CGT" sequence.fasta
```
Output:
```
ATGCTAGCTAGCTCGATCGTAGCTAGCTGATCGTACG
CGTAGCTAGCATCGATCGCGATCGTACGATCGTAGCT
```
You can also search for specific sequence names (headers):
```
grep ">Sequence" sequence.fasta
```
Output:
```
>Sequence1
>Sequence2
>Sequence3
```
16. ### Editing File Content Using Sed
The `sed` command is a stream editor used to find and replace text in files. For example, let’s say you want to replace all occurrences of CGT with GTA in the FASTA sequence file.

Command: `sed` is used for text substitution in files.
Example:
To replace CGT with GTA in the file and print the result to the terminal (without editing the file):
```
sed 's/CGT/GTA/g' sequence.fasta
```
If you want to save the changes back into the file:
```
sed -i 's/CGT/GTA/g' sequence.fasta
```
Now, if you open sequence.fasta with `less` or use `cat`, you'll see that CGT has been replaced by GTA in the sequence.

17. ### Sorting and Removing Duplicates with Sort and Uniq
If you have a list of items, you can sort them and remove duplicates using `sort` and `uniq`.

Command: `sort` arranges lines alphabetically or numerically.
Command: `uniq` removes duplicate lines.
Example:
Let’s assume we create a file with some duplicate sequence names.

Create a file called `sequences.txt`:
```
nano sequences.txt
```
Add the following sequence names:
```
Sequence1
Sequence2
Sequence3
Sequence1
Sequence2
```
Save and exit.

Sort the file:
```
sort sequences.txt
```
Output:
```
Sequence1
Sequence1
Sequence2
Sequence2
Sequence3
```
Remove duplicates using `uniq`:
```
sort sequences.txt | uniq
```
Output:
```
Sequence1
Sequence2
Sequence3
```
You can also directly save the sorted, unique content back into a new file:
```
sort sequences.txt | uniq > sorted_sequences.txt
```
18. ### Counting Specific Patterns with Grep
You can count how many times a specific pattern appears in a file using `grep -c`.

Example:
To count how many times the sequence GTA appears in sequence.fasta:
```
grep -c "GTA" sequence.fasta
```
Output:
```
2
```
This tells you that the pattern GTA appears twice in the file.

19. ### Using Head and Tail Commands
Sometimes, you might want to view just the first few lines or last few lines of a file. This is where head and tail come in handy.

Command: `head` displays the first part of a file.
Command: `tail` displays the last part of a file.
Example:
View the first 5 lines of sequence.fasta:
```
head -n 5 sequence.fasta
```
View the last 5 lines:
```
tail -n 5 sequence.fasta
```
20. ### Redirecting Output to Files
You can redirect the output of commands to a file using > (overwrite) or >> (append).

Example:
To save the first 3 lines of sequence.fasta into a new file:
```
head -n 3 sequence.fasta > first_part.fasta
```
If you want to append the next 3 lines to this new file:
```
tail -n 3 sequence.fasta >> first_part.fasta
```
21. ### Combining Commands with Pipes
You can combine commands using the pipe `|` operator, which passes the output of one command as the input to another.

Example:
To count the number of lines in sequence.fasta that contain GTA:
```
grep "GTA" sequence.fasta | wc -l
```
22. ### Creating a More Advanced Bash Script
Let’s create a more advanced bash script that:

Reads a FASTA file
Searches for a specific sequence (e.g., GTA)
Counts how many times that sequence appears
Example:
Create a new bash script called search_sequence.sh:
```
nano search_sequence.sh
```
Add the following content:
```
#!/bin/bash
echo "Enter the sequence pattern to search for:"
read pattern
count=$(grep -c "$pattern" sequence.fasta)
echo "The pattern '$pattern' appears $count times in sequence.fasta"
```
Save and exit (Ctrl + S, Ctrl + X).

Execute the script:
```
bash search_sequence.sh
```
When prompted, enter GTA or any other sequence you want to search for, and the script will tell you how many times it appears.

23. ### Learning More Commands
`awk`: A text processing tool. You can use it to extract specific columns from files.

Example: To extract sequence names from sequence.fasta:
```
awk '/^>/ {print $1}' sequence.fasta
```
`cut`: Extract parts of lines in a file.

Example: To extract the first 10 characters from each line in sequence.fasta:
```
cut -c 1-10 sequence.fasta
```
`find`: Locate files and directories.

Example: To find all .fasta files in your directory:
```
find . -name "*.fasta"
```
`*` its a wildcard learn more about wildcards and how to use it

`diff`: Compare two files line by line.

Example: To compare sequence.fasta and first_part.fasta:
```
diff sequence.fasta first_part.fasta
```
