# Lab Report 4 - Vim (Week 7)
Ferrari Guan A17917695

## Introduction

<br />
Lab 4 introduced Vim, a text editor inside the terminal. Since Vim is built into the terminal, it does not have mouse support. However, it has a plethora of shortcuts and commands that can often make editing files faster. When the ```vim``` command is used in the terminal, a window opens up. In this window, text can be added and deleted. 
<br />

## Part 1: Editing from the command line: ```vim```

<br />
The task for the lab session this week is shown below. <br />
Task: <br />
Log into ```ieng6``` <br />
Clone your fork of the repository from your GitHub account (using the SSH URL) <br />
Run the tests, demonstrating that they fail <br />
Edit the code file to fix the failing test <br />
Run the tests, demonstrating that they now succeed <br />
Commit and push the resulting change to your GitHub account (you can pick any commit message!) <br />

<br />
![Log in to ieng6](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-1.png) <br />
<br />
Keys pressed: ```ssh <space> f1guan@ieng6-202.ucsd.edu <enter>``` <br />
```cs15lwi24 <enter>``` <br />
Explanation: ```ssh``` enters the secure shell. Since the target server is ```ieng6```, the argument is ```f1guan@ieng6-202.ucsd.edu```. ```f1guan``` is my username, so it will differ depending on who logs into ```ieng6```. Lastly, ```cs15lwi24``` is used to enter the winter 2024 CSE 15L course, which will differ depending on the course. 
<br />

![Cloning my fork of the repository from my GitHub account using the SSH URL](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-2.png) <br/>
Keys pressed: ```git <space> clone <space> git@github.com:B2Bomber2/lab7.git <enter>``` <br />
Explanation: ```git clone``` clones a repository. The argument is ```git@github.com:B2Bomber2/lab7.git```, which is my repository. So, it will differ depending on which repository is used. 
<br />

![Run the tests, demonstrating that they fail](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-3.png) <br />
Keys pressed: ```cd <space> la <tab> <enter>``` <br />
```bash <space> te <tab> <enter>``` <br />
Explanation: ```cd``` is for changing directories and ```<tab>``` is used to autofill ```la``` to ```lab7/```. ```bash``` is used to run shell scripts. Similar to the previous usage of ```<tab>```, ```te``` is auto-filled to ```test.sh```. The ```test.sh``` shell script runs the Java testers on the ```ListExamples``` class. 
<br />

![Edit the code file to fix the failing test](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-4.png) <br />
Keys pressed: ```vim <space> Li <tab> .java <enter>``` <br />
```43j we r2 :x <enter>``` <br />
Explanation: The ```vim``` command opens the Vim text editor. The argument is ```ListExamples.java``` for this case, but will differ depending on the file. As mentioned in the previous explanation, ```<tab>``` auto-fills ```Li <tab>``` to ```ListExamples```. The commands inputted in the Vim window are ```43j we r2 :x <enter>```; ```43j``` moves the cursor down 43 lines, ```we``` moves the cursor to the end of the next word, ```r2``` replaces the character that the cursor is on with 2, and ```:x``` saves and exits the Vim window. 
<br />

![Run the tests, demonstrating that they now succeed](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-5.png) <br />
Keys pressed: ```<up> <up> <enter>``` <br />
Explanation: The up arrow key moves to the previous command. Since the command that executed the ```test.sh``` shell script was used 2 steps ago, the up arrow key was pressed twice. 
<br />

![Commit and push the resulting change to your GitHub account](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab4-6.png) <br />
Keys pressed: ```git <space> add <space> . <enter>``` <br />
```git <space> commit <space> -m <space> "fixed the index error" <enter>``` <br />
```git <space> push <enter>``` <br />
Explanation: The ```git add``` command adds the changes and ```git commit``` copies the change. The ```-m``` command-line option allows users to add a comment. In this case, the comment is ```"fixed the index error"```. Lastly, ```git push``` pushes the copy of changes into GitHub. 
