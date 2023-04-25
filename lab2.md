# Lab Report 1

## Part 1: StringServer
![Image](Images/stringserver.png)
Code for StringServer

![Image](Images/add1.png)

The following methods are called when "http://localhost:4321/add-message?s=1234" is visited.
  * `Integer.parseInt(args[0])` args[0] = 4321. This is given when running the command "java NumberServer 4321".
  * `Server.start(port, new Handler())` port = 4321.
  * `url.getPath().contains("/add-message")` Checking for the correct path "/add-message."
  * `url.getQuery().split("=")` Isolating the string "1234". This is stored in field "theString".

![Image](Images/add2.png)

The following methods are called when "http://localhost:4321/add-message?s=abcd" is visited.
  * `Integer.parseInt(args[0])` args[0] = 4321. This hasn't changed because the server is still active.
  * `Server.start(port, new Handler())` port = 4321.
  * `url.getPath().contains("/add-message")` Checking for the correct path "/add-message."
  * `url.getQuery().split("=")` Isolating the string "abcd". "theString" is concatenated with "\n" and then "abcd"
