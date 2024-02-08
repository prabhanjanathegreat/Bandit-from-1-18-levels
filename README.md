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

Bandit - Level 3

http://overthewire.org/wargames/bandit/bandit3.html

The password for the next user is stored in a file called spaces in this filename. I ran " cat "spaces in this filename" " and received the next password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG. In order to read files with spaces in the name you have to put the file name in quotation marks.

Username: bandit3

Password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

---------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 4

http://overthewire.org/wargames/bandit/bandit4.html

The password is stored in a hidden file in the inhere directory. I ran "ls" to see what files and directories there are and then I ran "cd" to move into the inhere folder. Then I ran "ls -a" to see all of the files including the hidden ones. All hidden files and folders in linux are stored with a dot in front of their name. The hidden file is named .hidden and after running "cat .hidden" I saw that the next password is 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe.

Username: bandit4

Password: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

---------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 5

http://overthewire.org/wargames/bandit/bandit5.html

The password is stored in file inside the inhere folder, most of the files in the directory as written in binary and only one of them has human readable text. I "cd" into the folder and saw all of the files in the folder. When trying to read the binary files with "cat" I would get something I could not read. I could tried to read every file and see which one has the password but I can also have a loop that gives me information on the files to see which one is the human readable one. To do this I ran the command below:

"file ./*"

The password seems to be in the -file07 file and to read it I ran "cat <-file07" and the password is lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR.

Username: bandit5

Password: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 6

http://overthewire.org/wargames/bandit/bandit6.html
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable

1033 bytes in size

not executable

To start I "cd" into the inhere folder and ran "ls" to see the files and folders and noticed that there were a bunch of folder and inside those folders a couple of files.

To make it easier and not have to read every file I tried to "find" a way to look for the specific file with the properties given. I looked through the manual page of the find command and looked for ways of pointing out the properties of the file. I found the -size, -type, and -executable options.

I put them together with the properties given and I ran the "find" command below:

find -type f -size 1033c ! -executable

It looks for a file that is size 1033 bytes and it is not executable. The output was ./maybehere07/.file2 and then I read the file I see that the password is: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU.

Username: bandit6

Password: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU.

-----------------------------------------------------------------------------------------------------------------------------------------


Bandit - Level 7
http://overthewire.org/wargames/bandit/bandit7.html

The password for the next level is stored somewhere on the server and has all of the following properties:

       owned by user bandit7

       owned by group bandit6

       33 bytes in size

For this part I used the find command below to find a file owned by user bandit7, owned by group bandit6 and 33 bytes of size.

       find / -user bandit7 -group bandit6 -size 33c 2>/dev/null

       / from root folder

       -user the owner of the file.

       -group the group owner of the file.

       -size the size of the file.

       2>/dev/null redirects error messages to null so that they do not show on stdout.

With that command we found the file in the following directory: /var/lib/dpkg/info/bandit7.password. When I read the file I found that the password is z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

Username: bandit7

Password: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

-----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 8
http://overthewire.org/wargames/bandit/bandit8.html

The password for the next level is stored in the file data.txt next to the word millionth.

When I logged into the profile I saw the data.txt file and when I read it a bunch of lines came up and it looked like all of the lines had the same structure. It was a word followed by some spaces and then a possible password. The hint was that the password is next to the word millionth, so I used the command below to read the file and then grep the word millionth.

      cat data.txt | grep millionth

The command only return 1 line and it contained the password:

      millionth TESKZC0XvTetK0S9xNwm25STk5iWrBvP
Username: bandit8

Password: TESKZC0XvTetK0S9xNwm25STk5iWrBvP

----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 9
http://overthewire.org/wargames/bandit/bandit9.html

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

To do this I ran the command below in order to sort the lines alphabetically and then remove all duplicates from the output.

       sort data.txt | uniq -u

The password is: EN632PlfYiZbn3PhVK3XOGSlNInNE00t

Username: bandit9

Password: EN632PlfYiZbn3PhVK3XOGSlNInNE00t

----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 10
http://overthewire.org/wargames/bandit/bandit10.html

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several �=� characters.

According to the hint, the file contains both strings and binary data which can make it difficult to read. In order to sort out the plain text I ran "cat data.txt | string". The next part is to grep the lines that start with the = sign. To do everything in 1 line I used the command below:

cat data.txt | strings | grep ^=

This returned 3 strings:

========== password

========== ism

========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

They all start with several = signs and if all of the passwords follow the same format the password should be the last line: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s.

Username: bandit10

Password: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

------------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 11
http://overthewire.org/wargames/bandit/bandit11.html

The password for the next level is stored in the file data.txt, which contains base64 encoded data

The data.txt contains 1 line that was encoded in base64. In order to decode the file I ran the command below:

cat data.txt | base64 --decode

The output was the following: The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

Username: bandit11

Password: 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

------------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 12
http://overthewire.org/wargames/bandit/bandit12.html

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

The data.txt file contains 1 line that was encrypted with the ROT13 algorithm. In order to decrypt it, I have to replace every letter by the letter 13 positions ahead. For example, with this encryption the letter a would be replaced with n. The word banana would encrypt to onanan. To decrypt the line I ran the command below:

cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'

The command above send the line to stdout where tr shifts every letter 13 positions. After running that command the output was:

The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

Username: bandit12

Password: JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

------------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 13
http://overthewire.org/wargames/bandit/bandit13.html

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

First we have to create a folder under the tmp directory to do this we run "mkdir /tmp/idk". This will give us a permission error that can be bypass by adding the -p option which will create the necessary parent directories in order to create the folder as explained in the mkdir manual page. Once the folder is created I copied the data.txt file to the folder with "cp data.txt /tmp/idk". In order to decypher the hexdump of the file I ran "xxd -r data.txt > bandit" which reverses the hexdump and saves it into a file named bandit. The hint stated that the file was compressed multiple times so I ran "file bandit" to see if it can determine the compression method used. The output for the command was:

bandit: gzip compressed data, was "data2.bin", from Unix, max compression

The output says that it was compressed with gzip, so we can add the .gz extension to the file in order to see what is inside. To do so we run "mv bandit bandit.gz", this will create the file and to decompress it I ran "gunzip bandit.gz" which gave us a file named bandit. I tried to read the file with "cat" but I noticed that it was still displaying binary data. I ran "file bandit" again to see what they used to compress the file. The output is below:

bandit: bzip2 compressed data, block size = 900k

It says that the compression was done with bzip2 so I added the bzip2 extension with "mv bandit bandit.bz2" and unzipped the file with the command "bzip2 -d bandit.bzip2" which gave us another bandit file. I ran "file bandit" and the output is below:

bandit: gzip compressed data, was "data4.bin", from Unix, max compression

It looks like the used gzip again. The hint did stated that it was compressed multiple times so I just have to keep unzipping until I find the next password. I added the .gz extension to the file and unzipped it and ran "file bandit" which gave me the following output.

bandit: POSIX tar archive (GNU)

The next compression was done with tar, so we have to add the .tar extension to the file with "mv bandit bandit.tar", to decompress it I ran "tar -xf bandit.tar" to extract all files. The command gave us a file named data5.bin, I ran the "file data5.bin" and I received the following output:

data5.bin: POSIX tar archive (GNU)

The file was still compressed with tar so I added changed the .bin extension with a .tar extension and decompressed the file and we received a new file named "data6.bin". I ran "file data6.bin" and the output was the following:

data6.bin: bzip2 compressed data, block size = 900k

The file was compressed again with bzip2, so I changed the .bin extension to the .bz2 extension and unzipped the file which gave us a file named data6. I ran "file data6" and the output was:

data6: POSIX tar archive (GNU)

The file is still not fully decompress because they compressed it with tar. I added the .tar extension and extracted the data which gave us a file named data8.bin. Upon running "file data8.bin" I saw the following output:

data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression

The file was compressed with gzip, so I changed the extension and then unzipped the file. I received a new file named data8 and when I ran "file data8", it said that the data contained ASCII text meaning we finally reached the end of the layers of compression. I ran "cat data8" and I received the next password: The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw.

Username: bandit13

Password: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 14
http://overthewire.org/wargames/bandit/bandit14.html

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don�t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on.

When I logged into the machine and I ran "ls" I saw a file named sshkey.private which must be the SSH private key the hint was talking about. In order to log into the bandit14 user�s profile I ran "ssh -i sshkey.private bandit14@localhost". The -i means that I am using an identity file in order to login to bandit14 on the server since all of the bandit users are on the same machine. After I logged into bandit14 I ran "cd /etc/bandit_pass/" as specified on the hint and then I read file bandit14 which gave us the next password: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt.

Username: bandit14

Password: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 15
http://overthewire.org/wargames/bandit/bandit15.html

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

According to the hint we have to connect to port 30000 on localhost and we have to send a string containing the current password. To do this I ran "nc localhost 30000" and once I saw that I was connected I pasted the password for bandit14 and then I received the following output

Username: bandit15

Password: JQttfApK4SeyHwDlI9SXGR50qclOAil1

-----------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 16
http://overthewire.org/wargames/bandit/bandit16.html

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting "HEARTBEATING" and "Read R BLOCK"? Use -ign_eof and read the "CONNECTED COMMANDS" section in the manpage. Next to R and Q, the B command also works in this version of that command...

I tried connecting to the port 30001 with the command below which seemed to work and I was able to type in the password of bandit15.

      openssl s_client -connect localhost:30001

After I typed in the password I received the following message:

      JQttfApK4SeyHwDlI9SXGR50qclOAil1

      HEARTBEATING

      read R BLOCK

      read:errno=0

This is the error message the hint was talking about. After reading the man page of openssl I tried looking up the pattern -ign_eof by hitting the / key and typing the string. However I was unable to find anything about it. I then tried to see what options are available for s_client by running openssl s_client -h which was not a valid command but I did get all of the options for s_client. I was then able to find the -ign_eof option the hint was talking about. As explained by the manual "-ign_eof" ignores the input eof. When we run the command below and I typed the password for bandit15 I received the new password.

openssl s_client -ign_eof -connect localhost:30001

Username: bandit16

Password: cluFn7wTiGryunymYOu4RcffSxQluehd

---------------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 17
http://overthewire.org/wargames/bandit/bandit17.html

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don�t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

As explained by the hint we have to find which host are up and running SSL. To do this we can run a nmap scan that will look check every port from 31000 to 32000 and check what services is running on that port. To do this I ran the command below:

nmap -v -A -T4 -p 31000-32000 localhost

The -A option in the command allows us to detect the OS, version detection or if there are any scripts running and -v increases the verbosity.

As we can see, there are 5 host online and 3 of them are running the echo service 1 of them is running msdtc and port 31790 is running ssl. After connecting to the 31790 port with "openssl s_client -connect localhost:31790" and entering the password for bandit16 I received a private RSA key.

-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----


I then created a folder with the "mkdir -p /tmp/bandit17" command and then copied the key and saved it to a file named bandit17.key then changed the file permissions with the "chmod 600 bandit17.key" command. I ran "ssh -i bandit17.key bandit17@localhost" and I was able to log into the bandit17�s profile. In the profile I ran "ls" and I found 2 files named "passwords.new" and "password.old" which both have many lines of possible password which some of them seem to repeat. To remove the duplicates between the 2 files I used the "diff passwords.new passwords.old" command which gave us the following passwords:

< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

---

> BS8bqB1kqkinKJjuxL6k072Qq9NRwQpR

I tried to log in with both passwords but they did not work. I remembered that in a previous level it said that all passwords are stored in the /etc/bandit_pass folder which I "cd" into and then I ran the "cat bandit17" command and I was able to get the password which I tried and I was able to login.

Username: bandit17

Password: xLYVMN9WE5zQ5vHacb0sZEVqbrp7nBTn

-----------------------------------------------------------------------------------------------------------------------------------

Bandit - Level 18
http://overthewire.org/wargames/bandit/bandit18.html

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see �Byebye!� when trying to log into bandit18, this is related to the next level, bandit19

Well since I did this on the previous level. I ran "diff password.new passwords.old" and I received the following output:

< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

---

> BS8bqB1kqkinKJjuxL6k072Qq9NRwQpR

I tried to login with both password but only the 1st one worked and just like the hint said I received the "Byebye!" output and I was kicked out.

Username: bandit18

Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
