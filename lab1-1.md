# Lab 1 Report: Remote Access and File Systems
Ferrari Guan
<br />
## Introduction  
<br />
Lab 1 encompassed the basics of a command line interface. A command line interface is typically used in a terminal or PowerShell. The commands used were ```javac```, ```java```, ```pwd```, ```ls```, ```cd```, and ```cat```. The command ```git clone https://github.com/ucsd-cse15l-f23/lecture1``` added a directory called ```lecture1``` that contains a java file named ```Hello.java```, a directory named ```messages```, and a file named ```README```. 
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
<br />
* Example 2: 
<br />
Command: ```[user@sahara ~]$ pwd lecture1/```
<br />
Output: ```/home```
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although another directory was included as an input to the command, ```pwd``` only returns the current directory.
<br />
* Example 3: 
<br />
Command: ```[user@sahara ~]$ pwd lecture1/Hello.java/```
<br />
Output: ```/home```
<br />
The command ran in the ```/home``` directory. Since the command was used in the home directory, the output was ```/home```. The command did not produce an error because its intended application was used. Although a file was included as an input to the command, ```pwd``` only returns the current directory. 
<br />
<br />

**The** ```ls``` **command:**
<br />
```ls``` stands for "list". As the name suggests, this command returns a list of files and directories in the input directory as the output. 
<br />
* Example 1: 
<br />
Command: ```[user@sahara ~]$ ls```
<br />
Output: ```lecture1```
<br />
The command ran in the ```/home``` directory. Since nothing was inputted as an argument and the only directory in the home directory is ```lecture1```, the output was ```lecture1```. The command did not produce an error because its intended application was used. 
<br />
* Example 2: 
<br />
Command: ```[user@sahara ~]$ ls lecture1/```
<br />
Output: ```Hello.java  messages  README```
<br />
The command ran in the ```/home``` directory. As mentioned previously, the ```lecture1``` contains a java file named ```Hello.java```, a directory named ```messages```, and a file named ```README```. Since the ```lecture1``` directory was inputted as an argument, the output was ```Hello.java  messages  README```. The command did not produce an error because its intended application was used.
<br />
* Example 3: 
<br />
Command: ```[user@sahara ~]$ ls lecture1/Hello.java/```
<br />
Output: ```lecture1/Hello.java```
<br />
The command ran in the ```/home``` directory. Since the ```lecture1/Hello.java``` file was inputted as an argument, the output was ```lecture1/Hello.java``` because ```lecture1/Hello.java``` is the only file in ```lecture1/Hello.java```. The command did not produce an error because its intended application was used.
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
<br />
* Example 2:
<br />
Command: ```[user@sahara ~]$ cd lecture1/```
<br />
Output: N/A
<br />
The command ran in the ```/home``` directory. Since the ```cd``` command only changes your directory, an output was not produced. However, the prompt changed to ```[user@sahara ~/lecture1]$```. The command did not produce an error because a valid directory was inputted as the argument.
<br />
* Example 3:
<br />
Command: ```[user@sahara ~]$ cd lecture1/Hello.java/```
<br />
Output: ```bash: cd: lecture1/Hello.java: Not a directory```
<br />
The command ran in the ```/home``` directory. Since the ```cd``` command only changes your directory, the output was ```bash: cd: lecture1/Hello.java: Not a directory``` because ```/home/lecture1/Hello.java``` is a file. The command produced an error because a file was inputted as the argument instead of a directory. 
<br />
<br />

**The** ```cat``` **command:**
```cat``` stands for "concatenate". This command sticks all the characters of the input files together and returns them as the output. In other words, the ```cat``` command uses a file as an input argument and outputs the contents as a combined string. 
* Example 1:
<br />
Command: ```[user@sahara ~]$ cat```
<br />
Output: ```bash: cat: No such file or directory```
<br />
The command ran in the ```/home``` directory. Since the ```cat``` command returns the contents of its inputs, an error was produced as the output. As the error suggests, nothing was inputted as an input argument. 
<br />
* Example 2:
<br />
Command: ```[user@sahara ~]$ cat lecture1/```
<br />
Output: ```cat: lecture1/: Is a directory```
<br />
The command ran in the ```/home``` directory. Since the ```cat``` command returns the contents of its input files, an error was produced as the output. As the error suggests, a directory was inputted as an input argument instead of a file. 
<br />
* Example 3:
<br />
Command: ```[user@sahara ~]$ cat lecture1/Hello.java/```
<br />
Output:
<br />
```
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
```
<br />
The command ran in the ```/home``` directory. Since the ```cat``` command returns the contents of its input files, the contents of the ```/home/lecture1/Hello.java``` file were returned as the output. The command did not produce an error because its intended application was used.
