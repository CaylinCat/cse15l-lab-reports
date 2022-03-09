# 652 commonmark-spec tests
During Week 9, we got a new directory called `test-files/` which held 625 tests. We had to test these tests on our Markdown Parse directory and a given Markdown Parse directory. I downloaded the directory, updated the `script.sh`, and then ran the tests and put the results in 2 `results.txt` files and compared them.

---
## Comparing the 652 tests

I used a bash for loop in `script.sh` and I used `script.sh > results.txt` in both directories to put the output of the tests into there. Then I ran `diff CSE15L-Panther/results.txt markdown-parse/results.txt` to compare the two as shown below.

Output of `diff`:
![Image](/labReport5Images/diff1.PNG) 
![Image](/labReport5Images/diff2.PNG)

## Test #1: line 212

This is test `194.md`, present on line 212 of the `results.txt` file.

My code resulted in: `[]`
Markdown Parse resulted in: `[url]`

![Image](/labReport5Images/test1.PNG)

I believe the correct implementation is their Markdown Parse as the link is shown on the preview of the test.

![Image](/labReport5Images/test194.PNG)

The bug with my mark down parse code is that when there is a space between `]` and `(` it does not register it as a link as shown below. On line 27, the requirement is that there must not be a space between the next close bracket and open parenthesis as shown by the if statement. When this is not present, the if statement will not run and thus the link will not be added.

![Image](/labReport5Images/line27.PNG)

## Test #1: line 212

This is test `201.md`, present on line 230 of the `results.txt` file.

My code resulted in: `[]`
Markdown Parse resulted in: `[baz]`

![Image](/labReport5Images/test2.PNG)

I believe the correct implementation is my Markdown Parse as the link is not shown on the preview of the test.

![Image](/labReport5Images/test201.PNG)

The bug with their mark down parse code is that on line 75, the conditional to check if it is a link does not consider if there is a `<>` in between the `]` and the `(`. The `<>` should make the link invalid.

![Image](/labReport5Images/line75.PNG)



