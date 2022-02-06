# Fixing Bugs - MarkdownParse.java
During Weeks 3 and 4, my group, Team Panther tackled the challenge of interacting with MarkdownParse.java and finding/fixing bugs in that program. MarkdownParse.java is a program that is suppose to obtain the links from a markdown file and put it into an array. However, when we recieved it it was not perfect and there were test cases that broke it's function. Here is documentation of 3 test cases that broke our program and how we solved it.

Below showcases the code change difference that we made to solve it, a link to the test file that broke our program initilally, the symptom we saw, and an explanation of how all these things relate.

---
## Bug #1 : The infinite loop

Code Change Diff:
![Image](/labReport2Images/fixingloop.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/markdown-parse/blob/main/test-incorrect.md)

Symptom:

![Image](/labReport2Images/showingfirsterror.PNG) 

The failure educing input of a link that contained characters like `(` `)` `[` `]` caused me to find a bug where we didn't register the right brackets. 
I recognized this bug because of the symptom that when I ran the code, it processed to infinitely loop. I saw these through some print statements I wrote.

Our solution was to break the loop if we couldn't find a next open bracket. This would stop the infinite loop from happening, however our code was still not fully functional for all test cases, and we went on to do more debugging.

---
## Bug #2 : The no show link

Code Change Diff:
![Image](/labReport2Images/fixedtest1.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/markdown-parse/blob/main/test-incorrect2.md)

Symptom:

![Image](/labReport2Images/failure2.PNG) 

The failure educing input of a link with `\]r l()` as text caused me to find a bug where we didn't check to see if we found the valid `]` bracket, since you can put it into text with a `\]` in markdown. 
I recognized this bug because of the symptom that when I ran the code with a link description that contained `\]r l()`, it processed no link even though there was a link present.

Our solution was to change our code to detect `](` instead of just `]` or `(` to ensure that we got the ending bracket and open parenthesis that help create the link format. This allowed us to avoid random other brackets or paranthesis that might be in the text.

---
## Bug #3 : The fake link with spaces

Code Change Diff:
![Image](/labReport2Images/fixedtest3.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/CSE15L-Panther/blob/main/test-file8.md)

Symptom:

![Image](/labReport2Images/bug3incode.PNG) 

The failure educing input of a fake link with spaces caused me to find a bug where we didn't check to see if the link had spaces, even though links can't have spaces. 
I recognized this bug because of the symptom that when I ran the code with a fake link that had spaces, it processed that as a link even though it shouldn't have. This made my junit spit out that we had an error.

Our solution was to change our code to detect if there was a space in our link. If there was a space in our link, it would not be a valid link so we would not include it.



