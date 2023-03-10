# Part 1
Code for StringServer.java:
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    // int num = 0;
    ArrayList<String> stringList = new ArrayList<>();

    String message = "Use /add-message?s=<string> to add concatenate text to this page!";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return message;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    message += "\n" + parameters[1];
                    return message;
                } 
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
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
\
Code for Server.java
```
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url);
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
    }
}
```

## On server start:
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/onstart.png) \

## First Concatenation:
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/firstconcat.png) \
`Server.java`'s start method is called in `StringServer.java`'s main method, the command-line specified port and a new `Handler` object are passed in as parameters to the start method of `Server.java`. `Server.java`'s start method creates a `server` object using `HttpServer`'s create method and calls the `server` object's createContext method with the root URI and a new `ServerHttpHandler` object (start method's handler parameter passed in) passed is as parameters. Inside of `ServerHttpHandler`, `StringServer.java`'s `handleRequest` method is called on the `handler` object which was created at the beginning of `ServerHttpHandler` as a field. `handleRequest` has the logic for our program and what it does is modify the `message` field of the `handler` object by adding a `\n` and the query which the user input in the url. The newly modified `message` field is then returned and displayed on the page via the remaining code in the `ServerHttpHandler` object.

## Second Concatenation:
![Image](https://rutracrafter.github.io/cse15l-lab-reports/assets/secondconcat.png) \
The same thing that happened in the first concantenation is happening here, except the user's query is different, so this time, different text is concatenated to the `message` field of the `handler` object!

# Part 2
Chosen bug: Array reversed method
\
Failure inducing input: {5, 6, 7, 8, 9}
```
@Test
public void testReversed2() {
    int[] input = {5, 6, 7, 8, 9};
    assertArrayEquals(new int[]{9, 8, 7, 6, 5}, ArrayExamples.reversed(input));
}
```
\
Non-failure inducing input: {} (empty array)
```
@Test
public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
}
```

The symptom: \
\
When the input is {5, 6, 7, 8, 9}, the symptom is {0, 0, 0, 0, 0} whereas the expected output would be {9, 8, 7, 6, 5}. \
\
When the input is {} (empty array) the symptom is that it passes the test, however, even though it works for this specific case, the code is still buggy for other imputs as there is a slight error in the logic of the `reversed` method. This is a symptom because it gives the illusion that the method is working properly, however, for input which consists of arrays of non-zero size, the test would not pass. \
\
Before fixing bug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
}
```
\
After fixing bug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```
The reason that the change addressed the issue is because before we were assigning the value from newArray to arr in reverse order and returning arr, and since newArray is an empty array at the start, then arr was just being filled with zeros. After the change, the values from arr are being assigned to newArray in reverse order, and newArray is returned!

# Part 3
When I used to debug programs I never thouht about taking a super systematic approach, and I feel like I was debugging like the students in the papers that we read. After reading this paper, and doing lab 3, I feel like I am now approaching debugging with a much systematic approach, rather than just reading through the code over and over again until realizing the mistake I had made. I really like the method of looking at bugs and symptoms of the program and making associations between the two to figure out what needs to be fixed. I am so glad that I have this new knowledge because I can assure you that it is going to save me a lot of time in the future!
