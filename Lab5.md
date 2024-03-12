# Lab Report 5 - Putting it All Together
Ferrari Guan A17917695

## Introduction

The main topic of this lab is debugging. This includes using Bash scripts to autograde programming assignments and the Java Debugger (JDB). The Bash script moves files into a grading area and runs Junit tests. The JDB is used to debug a Java program in the command-line interface by stopping at specified points. At those stop points, a user can verify field and variable values, step-by-step analysis, and etc. 

## Part 1 - Debugging Scenario 

This section will feature a debugging scenario between a teaching assistant and a student. 
<br />
<br /> 
#### Anonymous Student:
<br />
I got this message when I put my code into the auto-grader. I ran ```bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-nested```, but it says that the file is not found. I submitted my PA with a file called ```ListExamples.java```.
<br />
![The student's error](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab5-1.png) <br />

#### Teaching Assistant:
<br />
Show me your working directory by using the ```pwd``` command. Also, show me your code for this PA. 
<br />

#### Anonymous Student: 
<br />
Here is what I got after doing that:
```/home/linux/ieng6/cs15lwi24/f1guan/list-examples-grader``` <br />
Here is my code for the PA: 
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }
    return result;
  }


}
```
<br />

#### Teaching Assistant: 
<br />
The code looks good. Can you show me the file structure for your submission? 
<br />

#### Anonymous Student: 
<br />
The file structure is: 
```
|-- student-submission
|---- pa1
|------ ListExamples.java
```
<br />

#### Teaching Assistant: 
<br />
I see the issue now, try moving your Java file out of the ```pa1``` directory. Use the ```cp``` command to copy your Java file into the ```student-submission```. Then, remove the ```pa1``` directory using the ```rm``` command. 
<br />

#### Anonymous Student: 
<br />
It works now, thank you!
<br />

## Part 2 – Reflection 

I found out that professors use bash scripts to test student submissions on GradeScope. I also found out that Java has a built-in debugger that can run through code line by line. I thought that this process could be much more thorough than trying to figure out why a test case failed. Lastly, through attending lab sections, I learned how to appear like a hacker to my humanities major friends. 
