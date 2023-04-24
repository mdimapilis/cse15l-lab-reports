# Lab Report 2

## Part 1: Web Server

The code block below is the code for ```StringServer```.

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {

    String s;

    public String handleRequest(URI url) {
        if(url.getPath().contains("/add-message")) {
            System.out.println("Path: " + url.getPath());
            String[] parameters = url.getQuery().split("=");
            
            String finalS;
            if(s != null) {
                finalS = s + "\n" + parameters[1];
                return finalS;
            }
            s = parameters[1];
            return s;

        }
        else
        return "404 Not Found!";
    }
}

public class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

The screenshots below are two uses of ```/add-message```.

[Image](StringServerAdd1.png)

* Which methods in your code are called?
* What are the relevant arguments to those methods, and the values of any relevant fields of the class?
* How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

[Image](StringServerAdd2.png)


## Part 2: Bug Review


## Part 3: Reflection
