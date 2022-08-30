# Exercises and Solutions

=====================================

**a) Managing packages - Ubuntu**
---
**1. Install the package "nano"**
```shell
# Before installing the new package we should first update the Database's package.
$ apt update
$ apt install nano
```

**2. Uninstall the package "nano"**
```shell
$ apt remove nano
```

**b) Navigating the file system / Manipulating files and directories**
---

**1. Go the home directory and create a directory named "folder1"**
```shell
$ cd ~
mkdir folder1
```

**2. Rename the directory "folder1" to "new-folder" and create a file "hello.txt" inside this directory**
```shell
$ mv folder1 new-folder
$ touch hello.txt
```

**3. Create 4 additional files using only one command: file1.txt file2.txt file3.txt**
```shell
$ tocuh file(1..4)txt
```

**4. Remove 2 files: "file1.txt" and "file2.txt"**
```shell
$ rm file1.txt file2.txt
```

**5. Remove all files starting with "file"**
```shell
$ rm file*
```

**6. Remove the directory "new-folder"**
```shell
rm -r new-folder
```

**7. List all the files that contain either the letter "c" or "d"**
```shell
$ ls -l *[cd]
```

**8. List all the files whose name contain "ile"**
```shell
$ ls -l ?ile*
```

c) Editing and viewing files
----

**1. Go the home directory, create a new file named "file.txt", install nano and edit this file**
```shell
$ cd ~
$ apt update
$ apt install nano
$ nano file1.txt
```

**2. Print out the content of the file.txt**
```shell
$ cat file.txt 	                    # "cat" for files with short text
$ less /etc/adduser.conf 			# "less" for files with long text
$ head -n 5 /etc/adduser.conf 		# it shows the first 5 lines of this file
$ tail -n 5 /etc/adduser.conf       # it shows the last 5 lines of this file
```

d) Redirection
----
Standard input - represents the keyboard
Standard output - represents the screen

**1. Read the content from both "file1.txt" and "file2.txt" and print to the screen**
```shell
$ cat file1.txt file2.txt
```

**2. *Redirection*- take the content of "file1.txt" and put it into "file2.txt**
```shell
$ cat file1.txt > file2.txt 
```

**3. Redirection: take the content of "file1.txt" and "file2.txt", and put it into "combined.txt"**
```shell
$ cat file1.txt file2.txt > combined.txt
```

**4. Do "echo Hello World" and put this into the whatever.txt file**
```shell
$ echo Hello World > whatever.txt
```

**5. Add the following to the "whatever.tx" file: "I am Joao Pedro da Silva"**
```shell
$ echo "I am Joao Pedro da Silva" >> whatever.txt
```

**6. Get the long list of the files in the "etc" directory and write the output to a file called "files.txt"**
```shell
$ ls -l /etc > files.txt
```

**7. Using only one command, write a text "xxxxx", save it into a file and displays the result on the screen**
```shell
$ echo "Learning linux is so much fun" | tee file.txt
```

**8. Append the following sentence to the file.txt file you created above: "Learning Linux is easy, it feels like learning Portuguese"**
```shell
$ echo "Learning Linux is easy, it feels like learning Portuguese." | tee -a file.txt
```

**9.# Split file.txt into 300 lines per file and output to childfileaa, childfileab and childfileac**
```shell
$  split –l 300 file.txt childfile
```

e) Searching for text
----
**1. Search for the word "hello" in the file.txt**
````shell
$ grep hello file.text 			# case sensitive
$ grep -i hello file.text 		# case insensitive
````

**2. Search for the word "root" in /etc/password**
```shell
$ grep -i root /etc/passwd
```

**3. Search for the word "hello" inside multiple files "file1.txt", "file2.txt"**
```shell
$ grep -i hello file1.txt file2.txt
$ grep -i hello file*
```

**4. Search for the word "hello" in the files inside the current directory and all its sub-directory**
```shell
$ grep -i -r hello .
$ grep -ir hello .
```

f) Filters / Text Processors Commands
----
Create a file named "my-group" with the following content below:

```
Jerry Seinfeld
Cosmo Kramer
Eliane Benes
George Costanza
Newman mailman
Frank Costanza
Morty Seinfeld
Babes Kramer
Alton Benes
J Peterman
George Steinbrenner
Uncel Leo
David Puddy
Justin Pitt
Kenny Bania
```
**1. Get the first character / letter of everyline of the file**
```shell
$ cut -c1 my-group
```

**2. Get the first, second and fourth character / letter of every line of the file**
```shell
$ cut -c1,2,4 my-group
```
**3. List range of characters - get from the first character all the way until the fourth character / letter of every line of the file**
```shell
$ cut -c1-4 my-group
```

**4. List a specific range of character - get from the first until the third character and from fourth until the seventh character of every line of the file**
```shell
$ cut -c1-3,4-7 my-group
```

**5. Get the list of character by the byte size - display a character of 3 bytes of every line of the file**
```shell
$ cut -b1-3 my-group
```

**6. Display a list of a column of this file by specifying the delimeter - List the first 6th column separated by :**
e.g. joao:x:1000:1000:Joao Pedro da Silva:/home/iafzal:/bin/bash

```sh
$ cut -d: -f 6 new-file -> the output should be "/home/iafzal"
```

**7. Display a list of a column of this file by specifying the delimeter - List the first 6th and 7th column separated by :**
e.g. joao:x:1000:1000:Joao Pedro da Silva:/home/iafzal:/bin/bash

```sh
$ cut -d: -f 6-7 new-file -> the output should be "/home/iafzal:/bin/bash"
```

**8. From your home directory get a list of everything in there and display the second all the way to the fourth character.**
```sh
$ ls -l | cut -c2-4
```

**9. Display the first column of the file**
```sh
$ awk '{print $1}' my-group
```
**10. List 1 and 3rd field of "ls –l" command output**
```sh
$ ls –l | awk '{print $1,$3}'
```

**11. List the last column of "ls -l" comand output**
```sh
$ ls –l | awk '{print $NF}'
```

**12. Print the column that that contains the word "Jerry"**
```sh
$ awk '/Jerry/ {print}' my-group
```

**13. Ouput only 1st field of /etc/passwd**
```sh
$ awk -F: '{print $1}' /etc/passwd
```

**14. Do this command << echo "Hello Joao" >> and output replace the word "Joao" with "Adam"**
```sh
$ echo "Adam" | awk '{$2="Adam"; print $0}'
```

**15. Change every surnames of the list with "Smith"**
```sh
$ cat my-group | awk '{$2="Imran"; print $0}'
```

**16. Get lines that have more than 15 byte size**
```sh
$ awk 'length($0) > 15' my-group 
```

**17. Get the column matching "Music" in /home/username**
```sh
$ ls -l | awk '{if($9 == "seinfeld") print $0;}'  # $9 -> last column
```

**18. Find the total number of columns of the file**
```sh
$ ls -l | awk '{print NF}'
```

**19. Search for the word "Seinfeld" in my-group file.**
```sh
$ grep Seinfeld my-group
```

**20. Search for "Seinfeld" and count how many times it shows up in the file.**
```sh
$ grep -c Seinfeld my-group
```

**21. Search for "Seinfeld" and ignore case-sensitive.**
```sh
$ grep -i seinfeld my-group
```

**22. Search for "Seinfeld", display the matched lines and their line numbers.**
```sh
$ grep -n Seinfeld my-group
```

**23. Display every lines that don't contain the word "Seinfeld".**
```sh
$ grep -vi seinfeld my-group
```

**24. Search for all the lines that don't contain the word "Seinfeld" and print only the first column.**
```sh
$ grep -i seinfeld my-group | awk '{print $1}'
```

**25. Search for all the lines that don't contain the word "Seinfeld" and print only the first column with a range (get from the first until the third character).**
```sh
$ grep -i seinfeld my-group | awk '{print $1}' | cut -c1-3
```

**26. From your home directory print only the line that matches the file or directory "desktop".**
```sh
$ ls -l | grep Desktop
```

**27. Search for 2 keywords "" "" on the my-group file.**
$ egrep -i "Seinfeld|Costanza" my-group

**28. Sort the file in alphabetical order**
```sh
$ sort my-group
```

**29. Sort in reverse alphabetical order**
```sh
$ sort -r my-group
```

**30. Sort by the second column**
```sh
$ sort -k2 my-group
```

**31. Removes duplicates line from the files**
```sh
$ sort my-group | uniq
```

**32.Sort the list, filters it, and counts how many times a duplicate showed up**
```sh
$ sort file | uniq –c
```

**33. Only show repeated lines.**
```sh
$ sort file | uniq –d
```

**34. Check file line count, word count and byte count**
```sh
$ wc file
```

**35. Get the number of lines in a file**
```sh
$ wc –l file
```

**36. Get the number of words in a file**
```sh
$ wc –w file
```

**37. Get the number of bytes in a file**
```sh
$ wc –c file
```

**38. Get the number of files in a particular directory**
```sh
$ ls –l | wc -l
```
