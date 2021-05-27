# Bandit
Linux command

https://overthewire.org/wargames/bandit/
The challenge is to complete these 34 levels in the next 48 hours.

This game, like most other games, is organised in levels. You start at Level 0 and try to “beat” or “finish” it. Finishing a level results in information on how to start the next level. The pages on this website for “Level <X>” contain information on how to start level X from the previous level. E.g. The page for Level 1 has information on how to gain access from Level 0 to Level 1
  
  
Bandit Level 0
  The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and   the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.
  
    ssh bandit0@bandit.labs.overthewire.org -p 2220
    bandit0
  
Bandit Level 0 → Level 1
  The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password     for a level, use SSH (on port 2220) to log into that level and continue the game.
  
    ls 
    cat readme (copy the password)
    ssh bandit1@bandit.labs.overthewire.org -p 2220
    paste the password
  
Bandit Level 1 → Level 2
  The password for the next level is stored in a file called - located in the home directory
  
    cat <- (copy password)
 
Bandit Level 2 → Level 3
     The password for the next level is stored in a file called spaces in this filename located in the home directory
           
     ssh bandit2@bandit.labs.overthewire.org -p 2220
     paste the last copied password
     ls
     cat sp and clicked on tab button (copy password)

 Bandit Level 3 → Level 4
      The password for the next level is stored in a hidden file in the inhere directory.
           
     ssh bandit3@bandit.labs.overthewire.org -p 2220
     paste the last copied password
     cd inhere
     ls -a (to see hinden files) 
     cat .hidden
     copy the password
     exit
       
 Bandit Level 4 → Level 5
     The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
           
       ssh bandit4@bandit.labs.overthewire.org -p 2220
       paste the last copied password
       ls
       cd inhere
       ls
       file ./-file00
       file ./-file01
       ...
       file ./-file07 (till we found which file conatins ASCII text)
       cat ./-file07
       copy password
   
 Bandit Level 5 → Level 6
           The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
                  human-readable
                  1033 bytes in size
                  not executable
           
       ssh bandit4@bandit.labs.overthewire.org -p 2220
       paste the last copied password
       ls
       cd inhere
       ls
       find -type f -size 1033c ! -executable
       cat .maybehere07/.file2
       copy password
   
  Bandit Level 6 → Level 7
      The password for the next level is stored somewhere on the server and has all of the following properties:
          owned by user bandit7
          owned by group bandit6
          33 bytes in size
           
            ls
            bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c -type f 2>/dev/null
            /var/lib/dpkg/info/bandit7.password
            bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
            copy the password
  
  
  Bandit Level 7 → Level 8
    The password for the next level is stored in the file data.txt next to the word millionth
  
       grep millionth data.txt
       copy millionth password

  Bandit Level 8 → Level 9
    The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
    
      ls
      cat data.txt | sort | uniq -u OR sort data.txt | uniq -u  (copy the password)
 
  Bandit Level 9 → Level 10
    The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
  
      strings data.txt | grep “=” 
      strings data.txt | grep “==”  (copy the password)
  
  
 Bandit Level 10 → Level 11
  The password for the next level is stored in the file data.txt, which contains base64 encoded data
    
    base64-d data.txt
    copy the password
  
 Bandit Level 11 → Level 12
  The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

    cat data.txt |tr 'n-za-mN-ZA-M' a-zA-z  (copy the password)
 
 Bandit Level 12 → Level 13
    The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.
    For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123.
  
      ~ ssh bandit12@bandit.labs.overthewire.org -p 2220
      bandit12@melinda:~$ ls
      data.txt
      bandit12@melinda:~$ mkdir /tmp/kan1shka9
      bandit12@melinda:~$ cp data.txt /tmp/kan1shka9
      bandit12@melinda:~$ cd /tmp/kan1shka9
      bandit12@melinda:/tmp/kan1shka9$ ls
      data.txt
      bandit12@melinda:/tmp/kan1shka9$ file data.txt
      data.txt: ASCII text
      bandit12@melinda:/tmp/kan1shka9$ xxd -r data.txt > data_xxd_reverse
      bandit12@melinda:/tmp/kan1shka9$ file data_xxd_reverse
      data_xxd_reverse: gzip compressed data, was "data2.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
      bandit12@melinda:/tmp/kan1shka9$ zcat data_xxd_reverse > data_zcat
      bandit12@melinda:/tmp/kan1shka9$ file data_zcat
      data_zcat: bzip2 compressed data, block size = 900k
      bandit12@melinda:/tmp/kan1shka9$ bzip2 -d data_zcat
      bzip2: Can't guess original name for data_zcat -- using data_zcat.out
      bandit12@melinda:/tmp/kan1shka9$ file data_zcat.out
      data_zcat.out: gzip compressed data, was "data4.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
      bandit12@melinda:/tmp/kan1shka9$ ls
      data.txt  data_xxd_reverse  data_zcat.out
      bandit12@melinda:/tmp/kan1shka9$ zcat data_zcat.out > data_zcat_2
      bandit12@melinda:/tmp/kan1shka9$ file data_zcat_2
      data_zcat_2: POSIX tar archive (GNU)
      bandit12@melinda:/tmp/kan1shka9$ tar xvf data_zcat_2
      data5.bin
      bandit12@melinda:/tmp/kan1shka9$ file data5.bin
      data5.bin: POSIX tar archive (GNU)
      bandit12@melinda:/tmp/kan1shka9$ tar xvf data5.bin
      data6.bin
      bandit12@melinda:/tmp/kan1shka9$ file data6.bin
      data6.bin: bzip2 compressed data, block size = 900k
      bandit12@melinda:/tmp/kan1shka9$ bzip2 -d data6.bin
      bzip2: Can't guess original name for data6.bin -- using data6.bin.out
      bandit12@melinda:/tmp/kan1shka9$ file data6.bin.out
      data6.bin.out: POSIX tar archive (GNU)
      bandit12@melinda:/tmp/kan1shka9$ tar xvf data6.bin.out
      data8.bin
      bandit12@melinda:/tmp/kan1shka9$ file data8.bin
      data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
      bandit12@melinda:/tmp/kan1shka9$ zcat data8.bin > data8_zcat
      bandit12@melinda:/tmp/kan1shka9$ file data8_zcat
      data8_zcat: ASCII text
      bandit12@melinda:/tmp/kan1shka9$ cat data8_zcat
      The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
      bandit12@melinda:/tmp/kan1shka9$
  
  Bandit Level 13 → Level 14
     The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a      private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
  
      ssh bandit13@bandit.labs.overthewire.org -p 2220    (paste the previous copied password)  
      ls
      file sshkey.private
      cat sshkey.private
      copy the sshkey 
      ssh bandit14@localhost -i sshkey.private -p 2220 
      cat /etc/bandit_pass/bandit14 (copy password)
  Bandit Level 14 → Level 15
    The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
  
    ssh bandit13@bandit.labs.overthewire.org -p 2220    (paste the previous copied password)  
    nc localhost 30000 (nc here stands for netcat is a computer networking utility for reading from and writing to network connections using TCP or UDP)
    and paste the last copied password   
    copy password for next level
  
 Bandit Level 15 → Level 16
   The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.
  
      ssh bandit13@bandit.labs.overthewire.org -p 2220    (paste the previous copied password)  
      openssl s_client -connect localhost:30001 -ign_eof (Inhibit shutting down the connection when end of file is reached in the input)
      again paste password you will get new password.
  
 Bandit Level 16 → Level 17
  The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of   these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others       will simply send back to you whatever you send to it.
  
    ssh bandit13@bandit.labs.overthewire.org -p 2220    (paste the previous copied password)  
  
     
  
    
       
      
  
  
  
  
  
  
  
  
  
  
  
   
  
  
  


  
  
  
  
  
           
           
          
           
           
          
           
           
           
        
    
    
  

