# Snippet Testing in MarkdownParse
During Week 7, my group exchanged code with another code and we got to critique and analyze it. Then, we received feedback on our code. This lab report is about testing our code and their code of MarkdownParse, a file that parses links in mardown files, against 3 tests provided.

---
Before we get started, here a few links and definitions to a few things to help clear out the instructions:

My markdown parse respository: [https://github.com/CaylinCat/CSE15L-Panther](https://github.com/CaylinCat/CSE15L-Panther)

Other group's markdown parse respository: [https://github.com/ShashankVenkatramani/markdown-parse](https://github.com/ShashankVenkatramani/markdown-parse)

Snippet: the snippet of code that we are testing against our code
Preview: A way of viewing the .md file as what it would look like on the website
My Implementation: running the tests on my group's code
Their Implementation: running the tests on their group's code

---
## Snippet 1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
VSCode Preview and Code: ![Image](/labReport4Images/preview1.PNG)

Looking at this, I believe the expected output should be: ``\[google.com, google.com, ucsd.edu]`.

To turn it into a test, I added it into the MarkdownParseTest file:
![Image](/labReport4Images/addingtests1.PNG)

My implementation did not pass this test, as shown below:
![Image](/labReport4Images/runningcommands.PNG)

The test failure is indicated by the first error, as it did not meet the expected output for Snippet 1.

Their implementation also did not pass the test, as shown below:
![Image](/labReport4Images/runningcommands2.PNG)

Their test failure is indicated by the first error, as it did not meet the expected output for Snippet 1.

I do not believe that there is a small fix that could allow my code to pass snippet 1, it would require a more involved change as described below. If I search for `](` instead of just `]` or `(` I believe this would allow my code not to get confused by the extra `]` or `[` present. I then would have to account for the random ``\` in the code, and make sure a needed `[` or `]` was not in between one of those tic marks.

---
## Snippet 2

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
VSCode Preview And Code: ![Image](/labReport4Images/preview2.PNG)

Looking at this, I believe the expected output should be: `[a.com, a.com(0), example.com]`.

To turn it into a test, I added it into the MarkdownParseTest file:
![Image](/labReport4Images/addingtests2.PNG)

My implementation did not pass this test, as shown below:
![Image](/labReport4Images/runningcommands.PNG)

The test failure is indicated by the second error, as it did not meet the expected output for Snippet 2.

Their implementation also did not pass the test, as shown below:
![Image](/labReport4Images/runningcommands2.PNG)

Their test failure is indicated by the second error, as it did not meet the expected output for Snippet 2.

I do not believe that there is a small fix that could allow my code to pass snippet 2, it would require a more involved change as described below. I would have to consider the case of having multiple links inside links, which make it so only the inside link is a real link. To do this I would have to check if theres a valid link inside a link, which would be a more involved change than a simple <10 line code change.

---
## Snippet 3

```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```
VSCode Preview And Code: ![Image](/labReport4Images/preview3.PNG)

Looking at this, I believe the expected output should be: `[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]`.

To turn it into a test, I added it into the MarkdownParseTest file:
![Image](/labReport4Images/addingtests3.PNG)

My implementation did not pass this test, as shown below:
![Image](/labReport4Images/runningcommands.PNG)

The test failure is indicated by the third error, as it did not meet the expected output for Snippet 3.

Their implementation also did not pass the test, as shown below:
![Image](/labReport4Images/runningcommands2.PNG)

Their test failure is indicated by the third error, as it did not meet the expected output for Snippet 3.

I do not believe that there is a small fix that could allow my code to pass snippet 2, it would require a more involved change as described below. I would have to consider multi line code and breaks and which code is valid that has multilines. Though it does seem that all the code with proper multi line produces links, some of it does not produce links where it should, and thus we need to consider if that still does consitute a proper link in terms of a Markdown file. This would be a less involved fix as the other two as currently the code does not care if the code is one line or multiple lines.