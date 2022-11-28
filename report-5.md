# Lab Report 5
Runze Wang

A16343512

The code for grade.sh:
```
set -e
rm -rf student-submission
git clone $1 student-submission
echo "successfully copy"
cd student-submission
if [[ -e ListExamples.java ]]
then
    echo "The file exist"
else
    echo "Not found"
    exit 1
fi
cd ../
cp -rf lib student-submission
cp -f TestListExamples.java student-submission
cd student-submission
ls 
if [[ -e TestListExamples.java ]]
then
   echo "The Testlistexamples file is been copy"
else
   echo "Not copied successfully"
   exit 1
fi
cpath=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

set +e
javac -cp $cpath *.java


if [[ $? -eq 0 ]]
then
  echo "compiled"
else
  echo "compiled wrong"
  exit 1
fi

java -cp $cpath org.junit.runner.JUnitCore TestListExamples > out.txt

if [[ $? -eq 0 ]]
then
  grep "OK" out.txt
  exit 0
else
  grep "Tests run:" out.txt
  exit 1
fi
```

The screenshots for three different student submissions:

https://github.com/ucsd-cse15l-f22/list-methods-lab3:
![Image](https://i.imgur.com/IxNYQvS.png)


https://github.com/ucsd-cse15l-f22/list-methods-corrected:
![Image](https://i.imgur.com/MAYk6VI.png)

https://github.com/ucsd-cse15l-f22/list-methods-compile-error:
![Image](https://i.imgur.com/HdNVAtg.png)

As a demenstration of trace using the second screenshot. the `bash grade.sh` will first copy the link of the github `https://github.com/ucsd-cse15l-f22/list-methods-corrected` into the student submission file. Then, run the `TestListExamples.java` to the file we just cloned. If it passes the test (In this case, it passed), it will print out OK with how many tests it passed (In this case, it is 4 tests)
