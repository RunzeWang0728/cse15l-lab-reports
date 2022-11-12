# report-3

Name: Runze Wang \
Date: 11/10/2022

***Goal: Researching command for less, find, grep***

# ``` less ```

```-N``` \
Using ```-N``` could show up the line number for the file we are opening. This is a great command because it could help us know how many lines are in the file and locate a specific line on purpose.

What I enter in terminal:

```
wangrunzedeMacBook-Air:911report wangrunze$ less -N preface.txt
```

below is the effect of this command with line numbers. I only paste the last number of lines to demonstrate the effect.
```
102                 pause, reflect, and sometimes change our minds as we studied these problems and
    103                 considered the views of others. We hope our report will encourage our fellow
    104                 citizens to study, reflect-and act.
    105             Thomas H. Kean, chair
    106             Lee H. Hamilton, vice chair
    107         
    108     
(END)
```

 ```ESC + Space``` \
 Using ESC + Space in the view mode could move down a screen number of line. It could help us move down the file we are viewing quickly. One thing to mention is that if we are at bottom of the file and use ```ESC + Space```, it still moves down with ```~``` to show you reach the end.

below is the demonstration of pressing ```ESC + Space``` at the end of the file after entering the ```-N``` command above \

What I enter in terminal:
```
wangrunzedeMacBook-Air:911report wangrunze$ less -N preface.txt
```
The demonstration of ```ESC + Space``` at the end of the file:


 ```
 108     
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)
 ```

```-e``` \
Using ```-e``` could quit the view mode once you reach the end of the file automatically. 

What I enter in the terminal: 
```
wangrunzedeMacBook-Air:911report wangrunze$ less -e preface.txt
```
With ```-e``` in the command, once I reached the last line of the preface.txt, which is line 108, it will automatically quit the view mode and back to the terminal. It could save time because we do not need to quit the view mode manually by pressing ```q```.

# ```find```
```name``` \
Using ```name``` could find the file with specific pattern we are looking for. 
For the purpose of demonstration,  I rename the file ```chapter-1.txt``` to ```Chapter-1.txt``` with capital ```C``` to show the constrast with ```iname``` for the next command.

What I enter in the terminal with output:
```
wangrunzedeMacBook-Air:technical wangrunze$ find . -name "chapter*.*"
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
```

As you can see, it shows up all the file with ```"chapter*.*"``` pattern we are looking for. ```name``` is extremely useful when we are trying to find the file with specific pattern. For example, if you forget the actually full name of a file, you can use this command to find all the files with part of the name as the pattern to narrow the search. \
Note: ```Chapter-1.txt``` is not showed in this output because I changed the name as I mentioned. Therefore, it is worth to mention ```-iname```.

```iname``` \
Using ```iname``` could find the file with insensitive case. For the purpose of demonstration, I rename the file ```chapter-1.txt``` to ```Chapter-1.txt``` with capital ```C```.

What I enter in terminal with output:
```
wangrunzedeMacBook-Air:technical wangrunze$ find . -iname "chapter*.*"
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/Chapter-1.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
```

```iname``` is useful when we try to find the file with insensitive case. If we just use ```name```, it will skip the ```Chapter-1.txt```. It will save a lot of time and avoid confusion when finding files.

```-size``` \
Using ```-size``` could find the file with a limitation of size you choose.

What I enter in terminal with output:
```
wangrunzedeMacBook-Air:technical wangrunze$ find . -iname "chapter*.*" -size +100k
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/Chapter-1.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-12.txt
```

the ```+100k``` means that we are looking for files with size ```greater``` than 100kb. if we enter ```-100k```, it would find files with size smaller than 100kb ```-size``` is really useful when we are trying to find files with specific size.

# ```grep```

```-n``` \
Using `-n` could show up the number of line the pattern you find. It is really useful if you try to locate the number of line this pattern. Without `-n`, even if you know the line the pattern is in, but it could be hard to locate it in a large file.

What I enter in command and output:
```
wangrunzedeMacBook-Air:911report wangrunze$ grep -n "Ham" preface.txt
106:            Lee H. Hamilton, vice chair
```

In the ```preface.txt```, I am looking for `"Ham"` and it shows up at line 106.

`-i` \
Using `-i` could look for the pattern with insensitive case. It is useful when you try to find a pattern but you do not know if it has capital word or not.

What I enter in command and output:
```
wangrunzedeMacBook-Air:911report wangrunze$ grep -i "ham" preface.txt
            Lee H. Hamilton, vice chair
```
As you can see, I put in `"ham"` but it helps me find `Hamilton` with capital `H`.

`-w`\
Using `-w` could find a complete word you are looking for. It is useful when you wnat to avoid some word with the pattern in the words.

What I enter in terminal with output:
```
wangrunzedeMacBook-Air:911report wangrunze$ grep -w "Ham" preface.txt
wangrunzedeMacBook-Air:911report wangrunze$ grep -w "Hamilton" preface.txt
            Lee H. Hamilton, vice chair
```

The first time I enter `"Ham"` as the pattern I am looking for but nothing shows up because `"Hamilton"` is the word contains the pattern but `"Ham"` is not showed up in the file as a complete word. For the second time I put in `"Hamilton"` and it shows up the line with the pattern.


# Thank you for reading it and hope you find something insteresting!