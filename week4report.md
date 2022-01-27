# CSE 15L Week 4 Lab Report

## 1. Out of Memory Error
**The Symptom**
![Image](https://i.imgur.com/dxFj21u.png)

>[The File that Caused the Symptom](memory.txt)

**What Caused This?**
* The out of memory error was caused by a bug in the code where the while loop never finishes, creating an infinite loop. The infinite loop happens due to the test file containing a pair of paranthesis in the link. The infinite loop causes the JVM to hit the memory limit and cause an exception.

**The Fix**
![Image](https://i.imgur.com/A1Ix9DG.png)
* I used a variable to keep track of what the previous currentIndex was, and checked at the end of the loop if the previous currentIndex is the same as the currentIndex, and if it is just return what we have because it is in an infinite loop.

## 2. Images Appearing in Output
**The Symptom**
![Image](https://i.imgur.com/JiBSfmu.png)

>[The File that Caused the Symptom](image.txt)

**What Caused This?**
* Due to the fact that in markdown, links and images use similar syntax, the original code was not able to distinguish between the two. The original code took whatever was after the two brackets and between the two parenthesis, which images also fit that syntax. 

**The Fix**
![Image](https://i.imgur.com/mGvceKI.png)
* I checked the string in between the hard brackets to make sure that it isn't an image. If it is an image, we don't add it to the output array.

## 3. Index Out of Bounds Error
**The Symptom**
![Image](https://i.imgur.com/kh4m428.png)
>[The File that Caused the Symptom](noLink.txt)

**What Caused This**
* Because there were no hard brackets or parenthesis, when we call indexOf on those strings, it returns -1, which is not a valid substring to take, so when we try to take the substring, it throws an out of bounds exception.

**The Fix**
![Image](https://i.imgur.com/gOtNcAd.png)
* To fix this, all that we have to do is check if any of the indexOf calls returned -1, and if it did, then the file was most likely written incorrectly, or it does not contain a link so we break out of the loop and return an empty arraylist.

