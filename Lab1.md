# Lab 1 Report: Remote Access and File Systems
Ferrari Guan
<br />
## Introduction  
<br />
Lab 1 encompassed the basics of a command line interface. A command line interface is typically used in a terminal or PowerShell. The commands used were javac, java, pwd, ls, cd, and cat. The command ```git clone https://github.com/ucsd-cse15l-f23/lecture1``` added a java file named ```Hello.java```, a directory named ```messages```, and a file named ```README```. 
<br />
## The Commands 
<br />
**The** ```pwd``` **command:**
<br />
```pwd``` stands for "print working directory". As the name suggests, this command returns the current directory as the output. 
<br />
* Example 1: 
<br />
Command: ```[user@sahara ~]$ pwd```
<br />
Output: ```/home```
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. 
* Example 2: 
<br />
Command: ```[user@sahara ~]$ pwd lecture1```
<br />
Output: ```/home```
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although another directory was included as an input to the command, ```pwd``` only returns the current directory.
* Example 3: 
<br />
Command: ```[user@sahara ~]$ pwd lecture1/Hello.java```
<br />
Output: ```/home```
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although a file was included as an input to the command, ```pwd``` only returns the current directory. 
<br />
<br />
**The** ```ls``` **command:**
<br />
```ls``` stands for "list". As the name suggests, this command returns a list of files and directories in the current directory as the output. 
<br />
* Example 1: 
<br />
Command: ```[user@sahara ~]$ ls```
<br />
Output: 
<br />
The command ran in the ```/home``` directory. Since the only directory in the home directory is ```lecture1```, the output was ```lecture1```. The command did not produce an error because its intended application was used. 
* Example 2: 
<br />
Command: ```[user@sahara ~]$ ls lecture1```
<br />
Output: 
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although another directory was included as an input to the command, ```pwd``` only returns the current directory.
* Example 3: 
<br />
Command: ```[user@sahara ~]$ ls lecture1/Hello.java```
<br />
Output: 
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although a file was included as an input to the command, ```pwd``` only returns the current directory. 
<br />
<br />
**The** ```cd``` **command:**
<br />
```cd``` stands for "change directory". As the name suggests, this command changes the directory or folder. When given an argument or input, the ```cd``` command will change your directory to the input directory.
* Example 1:
<br />
Command: ```[user@sahara ~]$ cd```
<br />
Output: N/A
<br />
The command ran in the ```/home``` directory. Since the ```cd``` command only changes your directory, an output was not produced. The command did not produce an error because nothing was inputted as the argument. Hence, the directory remained the same. 
* Example 2:
<br />
Command: ```[user@sahara ~]$ cd lecture1/```
<br />
Output: N/A
<br />
The command ran in the ```/home``` directory. Since the ```cd``` command only changes your directory, an output was not produced. However, the prompt changed to ```[user@sahara ~/lecture1]$```. The command did not produce an error because a valid directory was inputted as the argument.
* Example 3:
<br />
Command: ```[user@sahara ~]$ cd lecture1/Hello.java```
<br />
Output: ```bash: cd: lecture1/Hello.java: Not a directory```
<br />
The command ran in the ```/home``` directory. Since the ```cd``` command only changes your directory, the output was ```bash: cd: lecture1/Hello.java: Not a directory``` /home/lecture1/Hello.java is a file. The command produced an error because a file was inputted as the argument instead of a directory. 
<br />
<br /> 

<br />
<br />
**The** ```javac``` **and** ```java``` **commands:**
<br />
```javac``` and ```java``` are commands used in the Java programming language. 
<br />
