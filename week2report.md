# CSE 15L Tutorial

## 1. Installing VSCode
* Go to this [link](https://code.visualstudio.com/download) and download VSCode for your OS

* You can set your theme by going to Settings -> Color Theme
![Image](https://i.imgur.com/QuShN08.png)

## 2. Remotely Connecting
* **Windows Users Only**: Install OpenSSH [here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

* Find your course account [here](https://sdacs.ucsd.edu/~icc/index.php)
    > Your course account will begin with cs15lwi22 and have 3 unique characters ending it

* Open your terminal on VSCode by going to Terminal -> New Terminal or the shortcut: Control + Shift + `
![Image](https://i.imgur.com/ZrboxTv.png)

* Type the command below and replace [unique characters] with the ones from your account
```
ssh cs15lwi22[unique chacters]@ieng6.ucsd.edu
```

* Enter the password for your account ![Image](https://i.imgur.com/LTUNizh.png)

* This is what it should look like if you logged in successfully
![Image](https://i.imgur.com/wscsINT.png)

## 3. Cool Commands!
* Now that you have successfully connected to your remote machine, you might be wondering, how do I do anything without a screen? *Try some commands!*

* `ls` -> this lists all the files in the current directory
* `cd` -> this changes the directory you are in (cd .. will go backwards)
* `clear` -> this clears your terminal

![Image](https://i.imgur.com/kC9Fh0q.png)


## 4. Moving Files With scp

* Create any file that you would like to send over to your remote machine and put it in the directory that your terminal is in

* Type the command
```
scp [file name and extension] cs15lwi22[unique characters]@ieng6.ucsd.edu:~/
```
* For example: ```scp picture.png cs15lwi22apy@ieng6.ucsd.edu:~/``` and enter your password

* If you did it correctly you should be able to ls in your remote machine and see the file you copied 
![Image](https://i.imgur.com/VZfEeSu.png)

## 5. Setting up an SSH key
* SSH keys will allow you to not have to enter your password when running commands

* Run the command below and follow the prompts, leave the passphrase blank
```
ssh-keygen
```
![Image](https://i.imgur.com/VbcOwsZ.png)

* On Windows you will have to follow these extra [steps](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation) 

* Then copy the public key to the .ssh directory of your remote machine using the scp command like we did above

## 6. Optimizing Remote Running
* You can run commands without having to fully connect to your remote machine by using
```
ssh cs15lwi[unique characters]@ieng6.ucsd.edu "[command]"
```
* For example: ```ssh cs15lwi22apy@ieng6.ucsd.edu "ls"```
![Image](https://i.imgur.com/8b53uBi.png)

* If you want to run multiple commands, use semicolons to separate them
* For example: ```javac Helloworld.Java; java Helloworld```