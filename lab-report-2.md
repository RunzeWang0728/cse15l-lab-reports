Oliver Wang \
PID: A16343512

This report has two parts: 1) A demonstration of my **Simplest Search Engine**; 2) Explain two bugs and symptoms from two selected java file.

**Part 1**

The Simplest Search Engine is a page where you can add words (strings) to a list in a web page by using URL and search through the list to find the strings that contains a substring you desire.

Here is my complete code for Simplest Search Engine:

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.List;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    List<String> dict = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return "This is a search engine! Add words to my data!";
        } else if (url.getPath().contains("/search")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    List<String> output = new ArrayList<>();
                    for (String s: dict){
                        if (s.contains(parameters[1])){
                            output.add(s);
                        }
                    }
                    if (output.isEmpty()){
                        return "We do not find such word(s) in my data!";
                    }
                    return String.format("We found %s", output.toString());
                }
        
        }else{ 
            System.out.println("Path: " + url.getPath());
            if(url.getPath().contains("/add")){
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                dict.add(parameters[1]);
                for (String s: dict){
                    return dict.toString();
                }
            }
            }
            return "404 Not Found!";
        }
        return "404 Not Found!";
    }
}


class SearchEngine {
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

![Image](https://i.imgur.com/TwXXbLv.png)

For the first screenshot, it is the default page for this search engine. In the java file, ```main``` in ```SearchEngine``` class is been called and create a server with a port (In this case is 4000). Then, inside class ```Handler```, ```handleRequest``` is been use. Specifically, the first **if** statement is been used in this case where it returns a simple introduction! 

![Image](https://i.imgur.com/eqGSR4K.png)

For the second screenshot, it is a demonstration of the adding string to the list for Search Engine. handleRequest method is been used. Specifically, the **else** statement is the major part. When we check the path with "/add", if parameter first index is **s**, we add what comes after equal sign to the ArrayList we created, dict. 

![Image](https://i.imgur.com/ufNhEzf.png)

Last screenshot is a demonstration of search function for our Search Engine. Inside ```handleRequest```, if we find ```/search``` in the url and the index 0 for the parameter is **s**, we would perform the search function: 1) create a new ArrayList called **output** to hold the desired output 2) For loop the **dict** with using ```.contains()```  3) return a string where output is changed to String by ```.toString()```.

**Part2**

For this part, I am showing the bug for ```filter``` method inside ```ListExamples.java``` and ```reversedInPlace``` inside ```ArrayExamples.java```

For ```reversedInPlace``` method, The failing input is [1,3,5,7,9]
The symptom is giving out a wrong output as what we expected

The bug in the code is that it is changing value in the original array so the for loop will use the updated elements rather than the original.

The change I make in the code is creating a new temp array and updating the elements into the temp array and making the original array equal temp array for reversed order.

![Image](https://i.imgur.com/cxi7Yad.png)
![Image](https://i.imgur.com/crPYjUx.png)

For ```filter```method, before testing, I create a checkString which it will return true if the length of the string is small or equal to 4 as shown below:


![Image](https://i.imgur.com/iJZ2lxw.png)

The failing input is an ArrayList with ["qweeee","123","zxc"] as shown below in the test.
The symptom is giving out a wrong order output as what we expected. 

The bug in the code is that the new list inside the mthod add elements from input list, which returns true from checkString, to the index 0 so it messes the order it it requests. 

The change I make is delete the index 0 in the ```.add()``` so that the passing string will add to the tail of the ArrayList.

![Image](https://i.imgur.com/GZskSVC.png)
![Image](https://i.imgur.com/GqDOisN.png)

Thank you for reading!