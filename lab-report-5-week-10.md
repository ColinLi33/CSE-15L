# CSE 15L Week 10 Lab Report

## How to find the differences?
* I used the techniques we used in the week 9 lab and ran the script.sh and outputted it to a text file for both programs and then used diff on them.

# Case #1
* This was 201.md
```
[foo]: <bar>(baz)

[foo]
```
* Expected output: ```[]```

* My output: ```[baz]```
* Other output: ```[]```

## The Bug
* The way my code current works, is it checks for a complete set of hard brackets and then looks for a complete set of parenthesis, once it finds those, it says that whatever is inside is the link even if it is not a link. To fix this, I would need to add an if statement to check if what is inside is actually a link
```
if (nextCloseBracket + 1 == openParen) {
    toReturn.add(markdown.substring(openParen + 1, closeParen));
}
```
# Case #2
* This was 577.md
```
![foo](train.jpg)
```
* Expected output: ```[]```

* My output: ```[]```
* Other output: ```[train.jpg]```

## The Bug
* Looking at the provided code, it does not appear that there is any check to differentiate an image with a link. This is a problem because their syntax is very similar in markdown. A way to fix this would be to check for a ! before any hardbracket and if there is one, ignore it becuase that is the syntax for an image. This can be done here, where after you find the first open hard bracket, you check to see if there is a ! before it.
```
int nextOpenBracket = markdown.indexOf("[", currentIndex);
 ```