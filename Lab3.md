# Lab 3 Report: Bugs and Commands (Week 5)
Ferrari Guan A17917695

## Introduction

<br />
Lab 3 encompassed testing and debugging; command line manipulation, especially for finding files; and Bash scripting. The commands ```find```, ```less```, and ```grep``` were introduced during the lab session. 
<br />

## Part 1: Bugs
<br />

The following shows the process of debugging a method in Java by utilizing the JUnit framework. 
The following buggy method is being tested. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```
*A failure-inducing input for the buggy program, as a JUnit test is shown below.
```
@Test
public void testReversedFail() {
  int[] input1 = {3,4};
  assertArrayEquals(new int[]{4,3}, ArrayExamples.reversed(input1));
}
```
* An input that does not induce a failure, as a JUnit test is shown below. 
```
public void testReversedPass() {
  int[] input1 = { };
  assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
}
```
* The symptom, as the output of running the tests, is shown below. 

![JUnit terminal output](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab3-0.png)

* The bug, as the before-and-after code change required to fix it, is described below. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```
The code body of the loop needs to be changed. Since the elements of ```arr``` need to be transferred to ```newArray```, the correct code for the loop body is ```newArray[arr.length - i - 1] = arr[i];```. Afterward, ```newArray``` needs to be returned because a new array is the expected output. The revised code below passes both of the previous test cases. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[arr.length - i - 1] = arr[i];
  }
  return newArray;
}
```

## Part 2: Researching Commands
<br />
For this section, I will choose to research the ```grep``` command. 
<br />
