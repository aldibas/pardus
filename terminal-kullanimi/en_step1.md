###  Level: Beginner

#### What is Linux?

Linux is a freely distributable, multi-tasking, multi-user UNIX operating system type.

Linux is a no-cost operating system that is developed collectively by many interested and involved people over the Internet and can run on many platforms, including servers and personal computers.

Linux is managed from a command-line interface, also known as a shell. In addition to the kernel, which manages hardware and software processes, Linux distributions include a range of Linux software to access and control hardware.

It is important to know that all operating systems run the kernel in a protected and restricted memory called the **kernel space** to prevent the kernel from terminating or crashing the system.

When a user runs an application or tool, it runs in the **user space**. This distinction is critical. By running these applications in a separate space from the kernel space, they cannot interfere with kernel resources and cannot cause the system to panic or crash.

## How Did Linux Come About?
We mentioned that Linux is a UNIX variant.

UNIX was developed in the mid-1970s as a multi-user operating system for large computers. Over time, it spread and spawned many variants. Today, there are UNIX variants written for computers ranging from personal computers to supercomputers.

Linux was developed primarily through the contributions of Linus Torvalds, a student at Helsinki University, and many interested programmers on the Internet. The development of Linux is done openly. This means that every stage of the operating system is openly published on the Internet, tested by users worldwide, and errors and deficiencies are identified and corrected and developed.

## Learning Objectives
After completing the Linux Playground environment;

+  You will be able to perform basic operations such as file management, copying, deleting, and moving,
+  You will learn how to update the system, package commands, installations, and management,
+  You will learn user management,
+  You will learn system monitoring and process management.


## Prerequisites

+ Basic computer use and ability to install programs. Other than that, you do not need any basic knowledge of Linux. Everything you need is available in "Bulut Bilişim Akademi".

## Scenario 1

+ Basic Linux Commands

In the first scenario, you will learn **echo**, **whoami**, **ls**, **cd**, **cat** and **pwd** commands that will allow you to perform various file operations at a basic level. Let's start in order:



The `whoami` command allows you to view the user account that is currently logged in to the terminal. In other words, you can see who you are:
``` {.sh}
BulutBilisimAkademi@playground:~$ whoami
>>> BulutBilisimAkademi
```

You can use the `ls` command to list the files in the current directory:
``` {.sh}
BulutBilisimAkademi@playground:~$ ls
>>> bin   dev  home  lib    lib64   lost+found  mnt  proc  run   snap  sys  usr  
boot  etc  init  lib32  libx32  media       opt  root  sbin  srv   tmp  var 
```


Use the `cd`  command to navigate to the directory you want to go to:
``` {.sh}
BulutBilisimAkademi@playground:~$ cd /home
BulutBilisimAkademi@playground:/home$
```

You can use the `pwd` command to find out the path of the current working directory:
``` {.sh}
BulutBilisimAkademi@playground:/home$ pwd 
>>>/home
``` 

You can use the `touch` command to create a new file from scratch in the current directory:
``` {.sh}
BulutBilisimAkademi@playground:~$ touch info.txt
```

You can use the `echo` command to display any desired text in the terminal:
``` {.sh}
BulutBilisimAkademi@playground:~$ echo "Bulut Bilişim Akademiye Hoş Geldiniz!"
>>>Bulut Bilişim Akademiye Hoş Geldiniz!  
```

Again, using the `echo` command, we can redirect the output of any desired text to the inside of a file:
``` {.sh}
BulutBilisimAkademi@playground:~$ echo "Bulut Bilişim Akademi: Linux Playground" > info.txt
```

You can use the `cat` command to view the contents of a file:
``` {.sh}
BulutBilisimAkademi@playground:~$ cat info.txt
>>>Bulut Bilişim Akademi: Linux Playground
```


You can use the `mkdir` command to create a new directory (folder) from scratch. The abbreviation of mkdir is **Make Directory**:
``` {.sh}
BulutBilisimAkademi@playground:~$ mkdir klasor1
```

Let's look at the folder you just created using the `mkdir`  command:
``` {.sh}
BulutBilisimAkademi@playground:~$ ls
>>>
info.txt  
klasor1
```


The `file` command allows you to find out the type of a file:
``` {.sh}
BulutBilisimAkademi@playground:~$ file klasor1
>>>klasor1: directory
```


You can use the `cp` command to copy a file or directory. The abbreviation of `cp` is **Copy** :
``` {.sh}
BulutBilisimAkademi@playground:~$ cp info.txt klasor1
```

You can use the `mv` command to move a file or directory from its current directory. The abbreviation of `mv` is **Move**:
``` {.sh}
BulutBilisimAkademi@playground:~$ mv info.txt klasor1 
```

You can use the `rm` command to delete a file or directory. The abbreviation of rm is **Remove** :
``` {.sh}
BulutBilisimAkademi@playground:~$ rm info.txt
``` 


The `help` command provides information about the usage of parameters and arguments of the command it is used with. It can be used in the form of** help <'command'>** or **<'command'> --help** :
``` {.sh}
BulutBilisimAkademi@playground:~$ rm --help
 >>> Usage: rm [OPTION]... [FILE]...
Remove (unlink) the FILE(s).  
  -f, --force           ignore nonexistent files and arguments, never prompt  
  -i                    prompt before every removal  
  -I                    prompt once before removing more than three files, or
                          when removing recursively; less intrusive than -i,
                          while still giving protection against most mistakes  
...
``` 

The abbreviation of `man`is **Manual Pages**, which means **Guide Pages** . These guide pages provide detailed information about the command they are used with, including components such as **Name** (the name and description of the command), **Synopsis** (how to use the command), **Description** (detailed information about the function of the command), **Examples** (examples related to the use of the command), and **See Also** (related topics to the command):
``` {.sh}
BulutBilisimAkademi@playground:~$ man rm
>>>NAME
       rm - remove files or directories  
SYNOPSIS
       rm [OPTION]... [FILE]...  
DESCRIPTION  
       This  manual  page  documents  the  GNU version of rm.  rm removes each
       specified file.  By default, it does not remove directories.  
       If the -I or --interactive=once option is given,  and  there  are  more
       than  three  files  or  the  -r,  -R, or --recursive are given, then rm
       prompts the user for whether to proceed with the entire operation.   If
       the response is not affirmative, the entire command is aborted.   
       Otherwise,  if  a file is unwritable, standard input is a terminal, and
       the -f or --force option is not given, or the -i  or  --interactive=al‐
       ways  option  is  given,  rm prompts the user for whether to remove the
       file.  If the response is not affirmative, the file is skipped.  
OPTIONS
       Remove (unlink) the FILE(s).

```

In the above sections, you learned how to navigate to the directory where folders are located using the **cd** and **ls** commands. But how do you search for a specific file among hundreds or thousands of files? That's where the power of the **find** and **grep** commands comes into play.

You can easily find out which directory your desired file is in using the `find` command:
``` {.sh}
BulutBilisimAkademi@playground:~$ find info.txt 
>>>klasor1
``` 

Using the `grep` command, you can determine whether the word or text you are looking for is present in the specified file:
``` {.sh}
BulutBilisimAkademi@playground:~$ grep "Akademi" info.txt
>>>Bulut Bilişim **Akademi** : Linux Playground
```
