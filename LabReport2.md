# Lab Report 2

## Part 1: Web Server

The code block below is the revised code for ```StringServer```.
> Note: The code is now generalized to be able to add any number of strings.

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {

    String s;
    ArrayList<String> alList = new ArrayList<>();

    public String handleRequest(URI url) {
        if(url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");

            s = "";

            alList.add(parameters[1]);
            for(String str : alList) {
                s += str + "\n";

            }
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

> First time using ```/add-message```

![Image](StringServerAdd1.png)

* In the screenshot above, the methods in my code that are called are ```.getPath()``` ```.contains(Object object)``` ```.getQuery()``` ```.add(String object)``` and ```.split(String regex)```.
* The relevant argument to the ```.getPath()``` method is the ```URI url``` parameter passed through the handleRequest method.  The relevant argument to the ```.contains(Object object)``` method is the string "/add-message" which checks if the correct path gets typed to keep track of a string.  The ```.getQuery()``` method gets the string after the "?" in the URL instance named url. The ``.add(String object)``` method adds the string to the ArrayList<String> called alList.  The ```.split(String regex)``` method takes in the string argument "=" to split up the query in order to get the running string which would be "Hello". 
* From this specific request, the elements inside the ```ArrayList<String> alList``` field would be changed from null and the running string "Hello" would be added via the ```.add(String object)``` method.  Then, the enhanced for loop in the handleRequest method would concatenate the elements of the alList field and update the ```String s``` field to "Hello", and that field would be returned, as portrayed in the image above.

> Second time using ```/add-message```.

![Image](StringServerAdd2.png)

* In the screenshot above, the methods in my code that are called are the same as the methods in the image before.
* The relevant arguments to the methods are the same as before except for the ```.split(String regex)``` method takes in the string argument "=" to split up the query in order to get the running string which would be "How are you". 
* From this specific request, the elements inside the ```ArrayList<String> alList``` field would be changed from "Hello" and the running string "How are you" would be added.  Then, the enhanced for loop in the handleRequest method would concatenate the elements of the alList field and update the ```String s``` field to "Hello\nHow are you", as portrayed in the image above.


## Part 2: Bug Review

The bug chosen from lab 3 is the one found in the ```static double averageWithoutLowest(double[] arr)``` method.

* The failure-inducing input for the buggy program is shown below in the code block as a JUnit test.  The method is supposed to to return the average of numbers in an array of type ```double``` without including the lowest value in the array.  However, this input will result in a failure because all the elements in the array are the same value and does not return the correct average since the method does not detect that there is no lowest value since all the elements are the same.

> JUnit test with failure-inducing input

```
@Test
  public void testAvgWOutLow5() {
    double[] doubleArr = {3.0, 3.0, 3.0, 3.0};
    double result = ArrayExamples.averageWithoutLowest(doubleArr);
    assertEquals(3.0, result, 0.0001);
  }
```

* The input shown in the code block below is a JUnit test that does not induce a failure.  It does not induce a failure because there is value that can be considered the lowest and all the elements in the array are of type ```double``` so these meet all the requirements for the method to work properly.
Note: The method will still work properly if an array of type ```double``` is passed and there are no elements.  If that happens, the result will be 0.0. The method will also work if there are only two elements of type ```double```, as long as if one element can be considered the lowest value.

> JUnit test with proper input

```
@Test
  public void testAvgWOutLow2() {
    double[] doubleArr = {2.0, 3.0, 1.0, 4.0};
    double result = ArrayExamples.averageWithoutLowest(doubleArr);
    assertEquals(3.0, result, 0.0001);
  }
```

* The, symptom, otherwise known as the output of both the inputs previously explained and depicted above is shown as a screenshot below.  

> Output of JUnit tests in VSCode terminal

![Image](SymptomJUnitLab3.png)

> Note: In order to run the JUnit tests in a VSCode terminal on a Windows OS machine, the following code blocks must be used, specifically for the ArraysTest.java file.

```
local $ javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
local $ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
```

* The following code blocks below (1) show the method before the bug was fixed and (2) show the method after the bug was fixed.

> Before the code was changed

```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```

> After the code was changed

```
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    int count = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num;}
    else if(num == lowest) { count++;}
    }

    if(count == arr.length) {
      return lowest;
    }

    return sum / (arr.length - count);
    
  }
```

The fix addresses the issue because the method now adds elements that are only greater than the lowest value then finds the average of those numbers.  If all the elements in the array are of the same value, then the number in the array is returned.

## Part 3: Reflection

In week 2's lab, I learned how to make a web server and how a web server can work locally and remotely.  In order to use a web server locally, it is as simple as compiling and running the server in a terminal like a normal program.  However, in order to use it remotely, I learned to clone the server via git and the server would run through a remote computer which would allow me to use the server on a browser the same way that I could use it locally.  I also understood how to make a simple web server using Java, but it took some time to understand how the code in the file influences the behavior of the server.  I found it interesting that the path and query of a url heavily influences the behavior of the web server.  Overall, this is something that I learned in week 2's lab that I didn't know before.
