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
The same thing that happened in the first concantenation is happening here, except the user's query is different, so this time, different text is concatenated to the `mesasge` field of the `handler` object!
