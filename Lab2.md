## Lab 2 Report: Servers and SSH Keys

<br />
Ferrari Guan A17917695
<br />

# Introduction
<br />
Lab 2 encompasses the basics of web servers, including Uniform Resource Locators (URLs) and Uniform Resource Identifiers (URIs). Secure Shell (ssh) was also introduced. During the lab sessions, students learned to log into the ssh for the UC San Diego eng6 cluster. 
<br />

# Part 1: Chat Server
<br />

The following is my code for ChatServer.java. 
<br />
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String currentChat = "";

    public String handleRequest(URI url) {
        String currentContent = " ";
        String currentUser = null;

        if (url.getPath().equals("/")) {
            return currentChat;
        } 
        else if (url.getPath().contains("/add-message")){
            if (url.getQuery().contains("&") == false || url.getQuery().contains("=") == false){
                return("Please use the format: /add-message?s=<String>&user=<user>");
            }
            String[] parameters = url.getQuery().split("&");
            String[] parameters1 = parameters[0].split("=");
            String[] parameters2 = parameters[1].split("=");
            if (parameters1[0].equals("s")) {
                currentContent = parameters1[1];
            }
            if (parameters2[0].equals("user")){
                currentUser = parameters2[1];
            }
            if (currentUser != null){
                currentChat = currentChat + currentUser + ": " + currentContent + "\n";
            }
            else{
                return("Please enter a username.");
            }
            currentContent = " ";
            currentUser = null;
            return currentChat;
        }
        else{
            return "404 Not Found!";
        }
    }
}

class ChatServer{
    public static void main(String[] args)throws IOException{
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

<br />
<br />
![Duolingo Appears](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-0.png)
<br />

* Which methods in your code are called?
* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

<br />
<br />
![Ferrari Responds](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-1.png)
<br />


* Which methods in your code are called?
* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

# Part 2: SSH
<br />
The absolute path to the private key for my SSH key for logging into ieng6 on my computer is 
<br />
!

<br />
The absolute path to the public key for your SSH key for logging into ieng6 (this is the one you copied to your account on ieng6, so it should be a path on ieng6's file system)
<br />
!

<br />
A terminal interaction where you log into your ieng6 account without being asked for a password.
<br />
!
<br />

# Part 3: Reflection
<br /> 
I learned about 
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
![Ferrari disappears](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-2.png)
