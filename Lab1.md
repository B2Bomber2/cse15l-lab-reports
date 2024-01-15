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
<br />
<br />

**The** ```javac``` **and** ```java``` **commands:**
<br />
```javac``` and ```java``` are commands used in the Java programming language. The ```javac``` command compiles a java file and converts it into a binary file. The ```java``` command runs the java binary file. 
<br />
* Example 1:
<br />
Command: ```[user@sahara ~]$ javac```
<br />
Output:
<br />

```
Usage: javac <options> <source files>
where possible options include:
@<filename> Read options and filenames from file
-Akey[=value] Options to pass to annotation processors
--add-modules <module>(,<module>)*
Root modules to resolve in addition to the initial modules,
or all modules on the module path if <module> is ALL-MODULE-PATH.
--boot-class-path <path>, -bootclasspath <path>
Override location of bootstrap class files
--class-path <path>, -classpath <path>, -cp <path>
Specify where to find user class files and annotation processors
-d <directory> Specify where to place generated class files
-deprecation
Output source locations where deprecated APIs are used
--enable-preview
Enable preview language features.
To be used in conjunction with either -source or --release.
-encoding <encoding> Specify character encoding used by source files
-endorseddirs <dirs> Override location of endorsed standards path
-extdirs <dirs> Override location of installed extensions
-g Generate all debugging info
-g:{lines,vars,source} Generate only some debugging info
-g:none Generate no debugging info
-h <directory>
Specify where to place generated native header files
--help, -help, -? Print this help message
--help-extra, -X Print help on extra options
-implicit:{none,class}
Specify whether to generate class files for implicitly referenced files
-J<flag> Pass <flag> directly to the runtime system
--limit-modules <module>(,<module>)*
Limit the universe of observable modules
--module <module>(,<module>)*, -m <module>(,<module>)*
Compile only the specified module(s), check timestamps
--module-path <path>, -p <path>
Specify where to find application modules
--module-source-path <module-source-path>
Specify where to find input source files for multiple modules
--module-version <version>
Specify version of modules that are being compiled
-nowarn Generate no warnings
-parameters
Generate metadata for reflection on method parameters
-proc:{none,only,full}
Control whether annotation processing and/or compilation is done.
-processor <class1>[,<class2>,<class3>...]
Names of the annotation processors to run;
bypasses default discovery process
--processor-module-path <path>
Specify a module path where to find annotation processors
--processor-path <path>, -processorpath <path>
Specify where to find annotation processors
-profile <profile>
Check that API used is available in the specified profile.
This option is deprecated and may be removed in a future release.
--release <release>
Compile for the specified Java SE release.
Supported releases: 
8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21
-s <directory> Specify where to place generated source files
--source <release>, -source <release>
Provide source compatibility with the specified Java SE release.
Supported releases: 
8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21
--source-path <path>, -sourcepath <path>
Specify where to find input source files
--system <jdk>|none Override location of system modules
--target <release>, -target <release>
Generate class files suitable for the specified Java SE release.
Supported releases: 
8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21
--upgrade-module-path <path>
Override location of upgradeable modules
-verbose Output messages about what the compiler is doing
--version, -version Version information
-Werror Terminate compilation if warnings occur
```

<br />
Command: ```[user@sahara ~]$ java```
<br />
Output: 
<br />

```
Usage: java [options] <mainclass> [args...]
(to execute a class)
or  java [options] -jar <jarfile> [args...]
(to execute a jar file)
or  java [options] -m <module>[/<mainclass>] [args...]
java [options] --module <module>[/<mainclass>] [args...]
(to execute the main class in a module)
or  java [options] <sourcefile> [args]
(to execute a single source-file program)

Arguments following the main class, source file, -jar <jarfile>,
-m or --module <module>/<mainclass> are passed as the arguments to
main class.

where options include:

-cp <class search path of directories and zip/jar files>
-classpath <class search path of directories and zip/jar files>
--class-path <class search path of directories and zip/jar files>
A : separated list of directories, JAR archives,
and ZIP archives to search for class files.
-p <module path>
--module-path <module path>...
A : separated list of elements, each element is a file path
to a module or a directory containing modules. Each module is either
a modular JAR or an exploded-module directory.
--upgrade-module-path <module path>...
A : separated list of elements, each element is a file path
to a module or a directory containing modules to replace
upgradeable modules in the runtime image. Each module is either
a modular JAR or an exploded-module directory.
--add-modules <module name>[,<module name>...]
root modules to resolve in addition to the initial module.
<module name> can also be ALL-DEFAULT, ALL-SYSTEM,
ALL-MODULE-PATH.
--enable-native-access <module name>[,<module name>...]
modules that are permitted to perform restricted native operations.
<module name> can also be ALL-UNNAMED.
--list-modules
list observable modules and exit
-d <module name>
--describe-module <module name>
describe a module and exit
--dry-run create VM and load main class but do not execute main method.
The --dry-run option may be useful for validating the
command-line options such as the module system configuration.
--validate-modules
validate all modules and exit
The --validate-modules option may be useful for finding
conflicts and other errors with modules on the module path.
-D<name>=<value>
set a system property
-verbose:[class|module|gc|jni]
enable verbose output for the given subsystem
-version print product version to the error stream and exit
--version print product version to the output stream and exit
-showversion print product version to the error stream and continue
--show-version
print product version to the output stream and continue
--show-module-resolution
show module resolution output during startup
-? -h -help
print this help message to the error stream
--help print this help message to the output stream
-X print help on extra options to the error stream
--help-extra print help on extra options to the output stream
-ea[:<packagename>...|:<classname>]
-enableassertions[:<packagename>...|:<classname>]
enable assertions with specified granularity
-da[:<packagename>...|:<classname>]
-disableassertions[:<packagename>...|:<classname>]
disable assertions with specified granularity
-esa | -enablesystemassertions
enable system assertions
-dsa | -disablesystemassertions
disable system assertions
-agentlib:<libname>[=<options>]
load native agent library <libname>, e.g. -agentlib:jdwp
see also -agentlib:jdwp=help
-agentpath:<pathname>[=<options>]
load native agent library by full pathname
-javaagent:<jarpath>[=<options>]
load Java programming language agent, see java.lang.instrument
-splash:<imagepath>
show splash screen with specified image
HiDPI scaled images are automatically supported and used
if available. The unscaled image filename, e.g. image.ext,
should always be passed as the argument to the -splash option.
The most appropriate scaled image provided will be picked up
automatically.
See the SplashScreen API documentation for more information
@argument files
one or more argument files containing options
--disable-@files
prevent further argument file expansion
--enable-preview
allow classes to depend on preview features of this release
To specify an argument for a long option, you can use --<name>=<value> or
--<name> <value>.
```

<br />
The command ran in the ```/home``` directory. Since the ```javac``` and ```java``` are intended to be used on Java files, a list of possible use cases was returned as the output. The command did not produce an error because a Java file was not inputted as an argument.
* Example 2:
<br />
Command: ```[user@sahara ~]$ javac lecture1/```
<br />
Output:
<br />
```
error: invalid flag: lecture1/
Usage: javac <options> <source files>
use --help for a list of possible options
```
<br />
Command: ```[user@sahara ~]$ java lecture1/```
<br />
Output:
<br />
```
Error: Could not find or load main class lecture1.
Caused by: java.lang.ClassNotFoundException: lecture1.
```
<br />
The command ran in the ```/home``` directory. Since the ```javac``` and ```java``` are intended to be used on Java files, the output was an error. As the error suggests, ```/home/lecture1/``` is a directory instead of a Java file. 
<br />
* Example 3; proper usage:
<br />
Command: ```[user@sahara ~]$ javac lecture1/Hello.java/```
<br />
Output: N/A
<br />
Command:
```
cd lecture1/
[user@sahara ~/lecture1]$ java Hello messages/en-us.txt/
```
<br />
Output: ```Hello World!```
<br />
The command ran in the ```/home``` directory. Since the ```javac``` command was used on a Java file, nothing was outputted. However, the ```Hello.class``` binary file was created in the ```/home/lecture1/``` directory. After changing to directory to ```/home/lecture1/```, the ```java``` command could be used on the ```Hello.class``` file. The ```Hello.class``` file takes in a text file as an input argument and returns the contents as the output. Hence, the output was ```Hello World!```.
