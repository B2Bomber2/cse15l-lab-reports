# Lab 2 Report: Servers and SSH Keys

<br />
Ferrari Guan A17917695
<br />

## Introduction
<br />
Lab 2 encompasses the basics of web servers, including Uniform Resource Locators (URLs) and Uniform Resource Identifiers (URIs). Secure Shell (ssh) was also introduced. During the lab sessions, students learned to log into the ssh for the UC San Diego ieng6 cluster. 
<br />

## Part 1: Chat Server
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
            if (url.getQuery().contains("&") == false ||
                url.getQuery().contains("=") == false){
                return("Please use the format:
                /add-message?s=<String>&user=<user>");
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
                currentChat = currentChat + currentUser + ": " +
                currentContent + "\n";
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
            System.out.println("Missing port number! Try any number
            between 1024 to 49151");
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

* The ```main``` method in the ```ChatServer``` class was called when the server started. After the path was inputted, the ```handleRequest``` method in the ```Handler``` class was called. 
* The ```main``` method uses an integer argument as a port number in order to start a web server. The ```handleRequest``` method uses a URI argument to create a chat. The relevant field is ```currentChat```. 
* In this request, ```currentChat``` adds ```currentUser``` and ```currentContent``` to itself separated by a colon and line break character. So, ```currentChat``` becomes ```Duolingo: Have you finished your Spanish lesson today?\n```. 

<br />
<br />
![Ferrari Responds](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-1.png)
<br />

* Since the web server is already running, only the ```handleRequest``` method in the ```Handler``` class was called in this case. 
* The ```main``` method uses an integer argument as a port number in order to start a web server. The ```handleRequest``` method uses a URI argument to create a chat. The relevant fields are ```currentChat```, ```currentUser```, and ```currentContent```. 
* Similar to the previous use case, ```currentChat``` adds ```currentUser``` and ```currentContent``` to itself separated by a colon and line break character. So, ```currentChat``` becomes ```Ferrari: No, I have been doing my the CSE 15L lab report instead.\n```.  

## Part 2: SSH
<br />
As shown in the image below, the absolute path to the private key for my SSH key for logging into ieng6 on my computer is ```/Users/ferrariguan/.ssh/id_rsa```. 
<br />
![private key](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-3.png)
<br />

<br />
As shown in the image below, the absolute path to the public key for my SSH key for logging into ieng6 is ```/home/linux/ieng6/oce/5o/f1guan/.ssh/authorized_keys```.
<br />
![public key](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-4.png)
<br />

<br />
The image below shows me accessing the contents of a markdown file in the ieng6 SSH without my password. 
<br />
![SSH terminal activities](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-5.png)
<br />

## Part 3: Reflection
<br /> 
I learned about SSH and how to manipulate content within a remote server. Although I have heard of SSH keys before, this was my first time learning how to generate one. Also, I learned how to create and transfer files between my own computer and a remote server. Overall, I learned a lot about web servers in this lab. 
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Here is the full chat log from part 1 if you are curious. 
<br />
![Ferrari disappears](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab2-2.png)
