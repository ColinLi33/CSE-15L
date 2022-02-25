# CSE 15L Week 8 Lab Report

## Repos Used
* [Mine](https://github.com/ColinLi33/markdown-parse)
* [Reviewed](https://github.com/jordan-nishi/markdown-parse)

# Test #1:
```
[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
* VSCode preview says the output should be:

    ```["`google.com", "google.com", "ucsd.edu"]```

* Here is the test I wrote for this case
![Image](https://i.imgur.com/zAfTm5c.png)

* The test failed for my code
![Image](https://i.imgur.com/2MeJgfz.png)

* The test failed for the other group's code as well
![Image](https://i.imgur.com/NycTHaS.png)

## The Fix
* I think to fix this, the code would need to be changed to better recognize what is a link and what isn't. The code I currently have thought that the first line in the snippet was a link, but it wasn't because of the backticks, so that would need to be adjusted.


# Test #2:
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
* VSCode preview says the output should be

    ``` ["a.com", "a.com(())", "example.com"]```
* Here is the test I wrote for this case
![Image](https://i.imgur.com/QqhM9J2.png)
* The test failed for my code
![Image](https://i.imgur.com/4c5iQYr.png)
* The test failed for the other group's code as well
![Image](https://i.imgur.com/QLJlnGZ.png)

## The Fix
* I think to fix this, the code would be changed to deal with nested parenthesis better. Currently, when my code sees an open parenthesis or bracket, it looks for the next closed one, but if there are 2 open parenthesis in a row before a closing one it breaks. I think to fix this, I would need to keep track of every open and closed parenthesis to make sure that each one has a match.

# Test #3:
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
* VSCode preview says the output should be

    ``` ["https://ucsd-cse15l-w22.github.io/"] ```
* Here is the test I wrote for this case
![Image](https://i.imgur.com/Fmdlt9X.png)
* The test failed for my code
![Image](https://i.imgur.com/72st3Ec.png)
* The test failed for the other group's code as well
![Image](https://i.imgur.com/UtH073c.png)

## The Fix:
* There might be an easy fix for this that involves handling newlines using \n, but I'm not sure how effective it will be. Real links do not contain new line characters, so we can just disregard any link that contains a newline and it should be fine.
