# Copy whole directories with scp -r
During Week 5, my group explored many options ranging from github access to ssh configuration. Here, I will show you option 3, how I was copying and running Markdown Parse files and commands in the cse 15L remote server. This included seperately copying the markdown parse directory and then running the commands on the remote computer, and also doing it together.

---
## Copying Markdown Parse Directory

By running: `scp -r . cs15lwi22aag@ieng6.ucsd.edu:~/CSE15L-Panther` I could copy my whole MarkdownParse Directory. This copies all files in this directory to the remote computer I specified. If you wanted to copy specific files, one would change the `.` to something else. For example, to copy all java files in the directory one would write `*.java` instead.

Copying Whole MarkdownParse Directory:
![Image](/labReport3Images/copyingFiles.PNG) 
![Image](/labReport3Images/copyingFiles2.PNG) 
![Image](/labReport3Images/copyingFiles3.PNG) 

## Running Tests in Remote Computer

I ran the following commands in order to log into my remote computer and run the test file. The first command logs me in through ssh. The second one makes me go to my directory. The third one runs the javac of the files I will be running. The last one runs the tests.

* `ssh cs15lwi22aag@ieng6.ucsd.edu` 
* `cd CSE15L-Panther`
* `javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParse.java MarkdownParseTest.java` 
* `java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest`

Running Tests on Remote Computer:
![Image](/labReport3Images/loginAndRun.PNG) 
![Image](/labReport3Images/loginAndRun2.PNG) 

## Doing it all in 1 line (combining `scp`, `;`, and `ssh`)

Although you can do the above 2 things seperatly, it's more fun to do it all in one line. With the power of the `;`, which seperates commands, this is possible. If you put all the commands together with `;` in between, you can run it all in one line. An example of this is shown below.

`scp -r *.java *.md lib\ cs15lwi22aag@ieng6.ucsd.edu:~\CSE15L-Panther; ssh cs15lwi22aag@ieng6.ucsd.edu "cd CSE15L-Panther; /software/CSE/oracle-java-se-14/jdk-14.0.2/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParse.java MarkdownParseTest.java; /software/CSE/oracle-java-se-14/jdk-14.0.2/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"`

Combining commands:
![Image](/labReport3Images/part3.PNG) 
![Image](/labReport3Images/part3-1.PNG) 