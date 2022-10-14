Oliver Wang\
Lab Report 1

This report is about how to get the remote access to the Filesystem.

**First step**:\
Installing Visual Studio Code in <https://code.visualstudio.com> and it will have the menu like this (mine is black background):

![Image](https://i.imgur.com/sD07tuI.png)


\
**Second Step**:\
Access the remote server. We are going to use ssh in terminal in vscode for this step. 

open a new terminal by click "Terminal" and "new terminal"

Inside the new terminal, type:
```
ssh cs15lfa22@ieng6.ucsd.edu 
```

type yes and press enter for a message and enter the password(password will not show up in the terminal)

![Image](https://i.imgur.com/NE95Bh9.png)
\
**Third Step**:

Try some interesting commands in the remote server and our own computer like:
```
cd ~

cd

ls -lat

ls -a

ls /home/linux/ieng6/cs15lfa22/cs15lfa22eg

cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/
cat /home/linux/ieng6/cs15lfa22/public/hello.txt
```

It turns out some of the commands are working in the remote server but they are not working in my own Windows computer


If we look closer to the error message (mine is in Chinese), it shows that the command could not find the path. Therefore, we need to make sure where you are when you use command (local or remote).

![Image](https://i.imgur.com/36JyEMM.png)
\
**Fourth Step**:

Moving Files over SSH with scp

we need to create a file called WhereAmI.java in our computer with 
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
run the program in terminal by:
```
javac WhereAmI.java

java WhereAmI
```
When we try to scp the file into our remote server by using:
```
scp WhereAmI.java cs15lfa22eg@ieng6.ucsd.edu:~/
```


![Image](https://i.imgur.com/xpMOQuS.png)

\
**Fifth step**:
SSH keys is a program to save public key and private key and use it in your desired location.

We create SSH keys because the repetitive step is really frustrating and we can use SSH keys to be more productive!

type: ```ssh-keygen``` in terminal and press enter twice but remember the default link in the code.

**Note**: Pressing enter twice is because there is default path for keygen, and we could check the path from the lines.

We go to the remote server and type:
```
mkdir .ssh
```
log out the server and type: 
```
scp C:\Users\wrzol/.ssh/id_rsa.pub cs15lfa22eg@ieng6.ucsd.edu:~/.ssh/authorized_keys
```
**Note**: you need to change **wrzol** to your username for your local computer!

![Image](https://i.imgur.com/SyJweTI.png)

Now we could get on our remote server without entering the password again!

![Image](https://i.imgur.com/m3JuzYj.png)
\
**Last step**: Optimizing

We could optimize our remote server process like:

We could use ```WhereAmI.java``` in remote server with only one line! we could perform a command in a quote.
```
ssh cs15lfa22eg@ieng6.ucsd.edu "java WhereAmI"
```
**Note**: change the email to your ieng email!

![Image](https://i.imgur.com/FFplhwg.png)

Also we could perform multiple command by using semicolon:




```
$ cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```


![Image](https://i.imgur.com/slxwAKn.png)

In this way, we could perform multiple command in just one line by seperating the command with ```;``` Inthis specific example, I firstly copy ```WhereAmI.java``` and  ```OtherMain.java```. Then successfully compile ```WhereAmI.java```



Thank you for reading!!!
