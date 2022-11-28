# Lab Report 5

### My grade.sh

    # Create your grading script here
    
    rm -rf student-submission
    true > output.txt
    true > error.txt
    git clone $1 student-submission 1>output.txt 2>error.txt
    
    if [[ $? -eq 0 ]]
    then
    	echo "Git clone successed. Points +10."
    else
    	echo "Git clone failed."
    	exit 1
    fi
    
    aim1="student-submission/ListExamples.java"
    aim2="student-submission/*/ListExamples.java"
    
    if [[ -e $aim1 ]]
    then
    	echo "Find file ListExample.java. Points +10."
    	index=$aim1
    elif [[ -e $aim2 ]]
    then
    	echo "Find file ListExample.java in directory. Points +10."
    	index=$aim2
    else
    	echo "Not find file ListExample.java."
    	exit 1
    fi
    
    cp $index ListExample.java
    
    javac ListExample.java 2>error.txt
    
    if [[ $? -eq 0 ]]
    then
    	echo "Complie successed. Points +10."
    else
    	echo "Complie error with ListExample.java."
    	exit 2
    fi
    
    echo "Start test your method:"
    
    true > output.txt
    true > error.txt
    
    #javac -cp $cp *.java
    javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
    #java -cp $cp org.junit.runner.JUnitCore TestListExample.java
    java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples 1>output.txt 2>error.txt
    
    if [[ $? -eq 0 ]]
    then
    	echo "All tests passed. Points +20"
    else
    	echo "Some tests failed."
    	exit 1
    fi
    
    exit 0

### Three Screenshots:

**url:** https://github.com/ucsd-cse15l-f22/list-methods-corrected

![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab-report5/2.png)

**url:** https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab-report5/3.png)

**url:** https://github.com/ucsd-cse15l-f22/list-methods-signature

![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab-report5/4.png)

### Trace

I choose to trace the first one: https://github.com/ucsd-cse15l-f22/list-methods-corrected, which has the methods corrected.

- the stderr and stdoutput for `rm -rf` `true > ...` are both terminal. Their return code should always be 0 since there is no error.
- for `git clone`, stderr is redirect to error.txt, stdoutput is redirect to output.txt. The return code should always be 0 unless I typed the url wrong.
- For the first if statement, this statement check the status of git clone command. As described above, it should always be 0 unless the url is wrong.
- Next I declared two arguments aim1 and aim2, they represents the possible location of the ListEamples.java.
- The next if statement check if the file ListExamples.java is exit. In this example, there is a ListExample.java in student-submission/, therefore this is true, and print Find file...points +10 to the terminal.
- Next I copy the file ListExamples.java to the working folder. The stderr and std output of cp are both terminal.
- Next I javac the ListExamples.java. The stderr is redirect to error.txt. The stdoutput is the terminal. The return code of this example is 0.
- Next if statement, I check the return code of the javac command. If the ListExamples.java compline faled, the return code should be 1 and the terminal will print Complie error with ListExample.java. But in this example, the compline succcessed. 
- Next I echo "Start test your method." The stderr and std output of cp are both terminal. The return code is 0.
- Next I javac all the test file I needed, and run java to test method. The stderr is redirected to the error.txt, stdoutput is redirected to output.txt. The return code of this example is 0.
- Next if statement check the return code of the test. In this example the return code is 0 so the first if statement is true, I print all tests passed.
- Finally, the `exit 0` leave the script with return code 0.  The stderr and std output of cp are both terminal.


