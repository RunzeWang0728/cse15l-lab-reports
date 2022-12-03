# report-4

Name: Runze Wang \
Date: 11/14/2022

## Part1

I choose to change the name of the `start` parameter and its uses to `base`

The command I used are following with explanations:

```
//open the file with vim
vim DocSearchServer.java

//replace all `start` to `base`
:%s/start/base/g<Enter>

//save the change and quit
:wq<Enter>
```
The first command will open the DocSearchServer.java with vim mode and we will operate the change in the vim mode.

The second command is the main command we perform. The %s is the command the replace. the first input is what we want to replace and the second input is what we are going to replace with. g means we will replace all the occurance in the java file. When we enter the start in the command, the cursor will highlight all the start in the vim mode which means it finds what we are looking for. After pressing the enter, all the start will become base!

The last command is saving the change we just made and quit the file safely. And now all the `start` parameter in DocSearchServer.java will be `base`.


In this way, we could replace all `start` to `base` in DocSearchServer.java with 21 presses :-)

-----

## Part 2

For the edit, I choose to change all `base` to `find` in DocSearchServer.java

When I performed the `scp` method, I used 5 mins and 22 seconds. 

When I performed in remote server directly, I used 3 mins and 46 seconds.

### Q1: Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?


A: I prefer edit on the remote server because it saves time and vim is useful in remote server to go through the file and edit it. In the past, I had a hard time to edit file in remote server, so I have to edit the file at the local server and `scp` to the remote server. Now, with vim, I could easily edit the file on the remote server. 

<br/>



### Q2: What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

A: first, if the file is incredibly large, `scp` the file from local to remote could take huge amount of time. For the `./technical` in skill demo 1, it has already taken a while so I could not imagine how long it could take for a much larger file. Second, some commands could not perform easily on Windows system, so remote server is useful and time saving in this way.
