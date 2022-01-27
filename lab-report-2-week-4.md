# Fixing Bugs!!!
Fixing 3 bugs in markdown parse!!

---
## Bug #1 : The infinite loop

Code Change Diff:
![Image](/labReport2Images/fixingloop.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/markdown-parse/blob/main/test-incorrect.md)

Symptom:

![Image](/labReport2Images/infiniteloop.PNG) 

The failure educing input of a link that contained characters like ( ) [ ] caused me to find a bug where we didn't register the right brackets. 
I recognized this bug because of the symptom that when I ran the code, it processed to infinitely loop. I saw these through some print statements I wrote.

---
## Bug #2 : The no show link

Code Change Diff:
![Image](/labReport2Images/fixedtest1.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/markdown-parse/blob/main/test-incorrect2.md)

Symptom:

![Image](/labReport2Images/failure2.PNG) 

The failure educing input of a link with "\]r l()" as text caused me to find a bug where we didn't check to see if we found the valid ] bracket, since you can put it into text with a \] in markdown. 
I recognized this bug because of the symptom that when I ran the code with a link description that contained "\]r l()", it processed no link even though there was a link present.

---
## Bug #3 : The fake link with spaces

Code Change Diff:
![Image](/labReport2Images/fixedtest3.PNG) 


Link to test file with failure inducing output!: [Click me!](https://github.com/CaylinCat/CSE15L-Panther/blob/main/test-file8.md)

Symptom:

![Image](/labReport2Images/failure1.PNG) 

The failure educing input of a fake link with spaces caused me to find a bug where we didn't check to see if the link had spaces, even though links can't have spaces. 
I recognized this bug because of the symptom that when I ran the code with a fake link that had spaces, it processed that as a link even though it shouldn't have. This made my junit spit out that we had an error.



