# Bandit-from-1-18-levels
Walkthrough of all the bandit levels from 1-18
--------------------------------------------------------------------------------------------------------------------------------------

Bandit Level 0
http://overthewire.org/wargames/bandit/bandit0.html

In their website they give us the username and password for bandit0 and we have to find the password for bandit1

Username: bandit0
Password: bandit0 

---------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 1
http://overthewire.org/wargames/bandit/bandit1.html

While logged into the bandit0 user profile I ran the “ls” command to see if I find any useful files. The output showed that there is a file named “readme”. I read the file using “cat readme” and it contained 1 line with the following text: “NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL”. I tried to use the string from the file to log into bandit1 and it worked.

Username: bandit1
Password: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

---------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 2
http://overthewire.org/wargames/bandit/bandit2.html

On the bandit website it says that the next password is saved in a file named -. When I logged into the account and ran "ls" I saw the file. I then ran "cat <-" and I saw that the password is: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi. In order to read files that start with a dash, you have to redirect them to stdin with the < operator. 

Username: bandit2
Password: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

---------------------------------------------------------------------------------------------------------------------------------------

Bandit Level 2 → Level 3
http://overthewire.org/wargames/bandit/bandit3.html

The password for the next user is stored in a file called spaces in this filename. I ran " cat "spaces in this filename" " and received the next password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG. In order to read files with spaces in the name you have to put the file name in quotation marks.

Username: bandit3
Password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

---------------------------------------------------------------------------------------------------------------------------------------

Bandit Level 3 → Level 4
http://overthewire.org/wargames/bandit/bandit4.html

The password is stored in a hidden file in the inhere directory. I ran "ls" to see what files and directories there are and then I ran "cd" to move into the inhere folder. Then I ran "ls -a" to see all of the files including the hidden ones. All hidden files and folders in linux are stored with a dot in front of their name. The hidden file is named .hidden and after running "cat .hidden" I saw that the next password is 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe.

Username: bandit4
Password: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

---------------------------------------------------------------------------------------------------------------------------------------

Bandit Level 4 → Level 5
http://overthewire.org/wargames/bandit/bandit5.html

The password is stored in file inside the inhere folder, most of the files in the directory as written in binary and only one of them has human readable text. I "cd" into the folder and saw all of the files in the folder. When trying to read the binary files with "cat" I would get something I could not read. I could tried to read every file and see which one has the password but I can also have a loop that gives me information on the files to see which one is the human readable one. To do this I ran the command below:

file ./*

The password seems to be in the -file07 file and to read it I ran "cat <-file07" and the password is lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR.

Username: bandit5
Password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh
