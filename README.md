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
    cat data.txt | sort | uniq -u OR
                  sort data.txt | uniq -u
    copy the password
 
 Bandit Level 9 → Level 10
   The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
  
  strings data.txt | grep “=” 
  then
  strings data.txt | grep “==”
  copy the password
  
  
 Bandit Level 10 → Level 11
  
  The password for the next level is stored in the file data.txt, which contains base64 encoded data

  Commands you may need to solve this level
  grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
  
   base64-d data.txt
  copy the password
  
  
  
 Bandit Level 10 → Level 11
  The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

  Commands you may need to solve this level
  grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
  
  
  cat data.txt |tr 'n-za-mN-ZA-M' a-zA-z
  copy the password
  
  
  
  
  
  
  
  
  
   
  
  
  


  
  
  
  
  
           
           
          
           
           
          
           
           
           
        
    
    
  

