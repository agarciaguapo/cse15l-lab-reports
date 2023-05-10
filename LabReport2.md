# LabReport 2
## Introduction
Knowing how to run and fix servers is a must for many programmers as it is one of the more important jobs in the world.
Especially when in todays world everything is know online and many biig companies want to expand their reach through the use of 
websites. So being able to fix and run servers can be very beneficial and many companies will be lokking for porgramers that have
this ability.

## Starting a Server
The goal this week was to start a web server that would be able to take in the command "/add-message?s=<String>" which allows a user
to input a message into where the "<String>" value would be and print a message on a page for example if someone where to type 
"/add-message?s=Hello" into the url, the page would then print Hello. The code that we used is this:

        import java.io.IOException;
        import java.net.URI;

        class Handler implements URLHandler {
        // The one bit of state on the server: a string that will be manipulated by
        // various requests.
        String message = "";

            public String handleRequest(URI url) {
                if (url.getPath().equals("/")) {
              return message;
            } else {
              if (url.getPath().equals("/add-message")) {
                 String query = url.getQuery();
                  if (query != null) {
                      String[] parameters = query.split("=");
                      if (parameters[0].equals("s")) {
                          if (message.isEmpty()) {
                              message = parameters[1];
                          } else {
                              message += "\n" + parameters[1];
                          }
                          return message;
                      }
                  }
              }
              return "404 Not Found!";
          }
      }
    }
        class StringServer {
            public static void main(String[] args) throws IOException {
                if (args.length == 0) {
                    System.out.println("Missing port number! Try any number between 1024 to 49151");
                    return;
                }

                int port = Integer.parseInt(args[0]);

                Server.start(port, new Handler());
            }
        }

This code allowed for the user on the website to type messages into the URl which can be seen in these screenshots below:
  
 ![Image](StartServer.png)
 
The image above is showing how to run the sever in which we have to compile the StringServer.java and Server.java files and afterwards we can start the String Server file but we also have to include a port in order for the server to function properly. 
  
 ![Image](BlankPage.png)
 
This image is showing the web server running however, there is nothing on the page as no message has been added. 
 ![Image](HelloMsg.png)
  
If you look at the url you can see that after the domain you can see the message "/add-message?s=Hello" which allowed the page to print a hello message.

  ![Image](msg2.png)

If you do it again as demonstrated on this image a new message will appear on a new line under the old message.
The way this is working is due to the fact that everytime the "/add" method is found this calls the handleRequest method from the code. 
When a request is made to /add-message?s=<string>, the handleRequest method is called with a URI object representing the requested URL. 
The URI object has a path of "/add-message" and a query of "s=<string>". In the handleRequest method, the message field of the Handler class gets cahnged
when a new message is added and since the message field is initially empty, it gets appended with the new message string.

## Bugs and Testing
        
Another important skill to have as a programmer is being able to catch bugs and be able to fix them. Bugs are always bound to happen since 
prorgammers will always make mistakes so one way to catch bugs is by making creating test which can help you see what bugs are happening and 
how to fix them.
        
The code in which we will be looking at is the code found in ArrayExamples.java:

        public class ArrayExamples {

          // Changes the input array to be in reversed order
         static void reverseInPlace(int[] arr) {
           for(int i = 0; i < arr.length; i += 1) {
             arr[i] = arr[arr.length - i - 1];
           }
         }
  
         // Returns a *new* array with all the elements of the input array in reversed
         // order
         static int[] reversed(int[] arr) {
          int[] newArray = new int[arr.length];
          for(int i = 0; i < arr.length; i += 1) {
            arr[i] = newArray[arr.length - i - 1];
            }
          return arr;
          }
        
          // Averages the numbers in the array (takes the mean), but leaves out the
          // lowest number when calculating. Returns 0 if there are no elements or just
          // 1 element in the array
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
  
  
        }
        
Based on the code the bug seems to be found in the revered method as it creates a new array with the same length as the input array.
        however, it copies the reversed elements into the input array which meams the original array gets modified instead of a new
        array being created.
Here are some Junit test that test the code.
Failure Inducing:
                           
# Failure Inducing:                               
        @Test
        public void testReverse(){
               int[] arr = {1,2,3,4,5,;
               ArrayExamples.reverseInPlace(arr);
               asserArrayEquals(new int[]{5,4,3,2,1), arr);
                }
        
# Non-Failure Inducing:
        @Test
        public void testAverageWithoutLowest(){
               double[] arr = {5.0,4.0,3.0};
               double result = ArrayExamples.averageWithoutLowest(arr);
               asserEquals(4.0, result, 0.0001);
        }
        
# Bug Code Before:
        static int[] reversed(int[] arr){
                int[] newArray = new int[arr.length];
                for( int i = 0; i < arr.length; i += 1){
                       arr[i] = newArray[arr.length - i -1];
                     }
                 return arr;
          }
                                               
 # Bug Code After:
          static int[] reversed(int[] arr){
                int[] newArray = new int[arr.length];
                for( int i = 0; i < arr.length; i += 1){
                       newArray[i] = arr[arr.length - i -1];
                     }
                 return newArray;
          }
           
As mentioned before the bug was due to the fact that the reversedlist was being copied onto the original line which meant there wasn't a new 
array being created to return. To fix this the reversed elemented needed to be copied onto a new array insetad of the original so we changed
"arr[i] = newArray[arr.length - i -1]" to  "newArray[i] = arr[arr.length - i -1]" and made it return the newArray instead.
        
        
## What I leanred
        
One of the coolest thing I leanred this week in my opinion was being able to start my own webserver. I didn't know that starting a web server was so simple
and although it was very simple, it was still cool to see how to be able to start one and be able to make certain commands that can change the page. I also didint know that in order to start a server I needed a port id and the more I think about it, the more it makes sense because if servers have the same port then that would cause a mess since there will people different people trying to access the same port. So by hvaing a unique port this allows the server to run smoothly. 
Finally it was cool to see how to update commands on a server which can change certain things on a page, I imagine that on an actaul website it is more complicated since there are so many other links to head towards but hopefully one day i'll be able to create an actual website myself.
