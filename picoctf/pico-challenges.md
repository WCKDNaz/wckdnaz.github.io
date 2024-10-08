---
layout: default
---
# General Challenges - PicoCTF
The following challenges are the ones that I felt were a bit higher than introductory, in my opinion, and were fun challenges to complete.
The goal of each challenge is to obtain a certain flag value, some challenges require you to download certain files, please refer to challenge name on PicoCTF,
if you so wish to try and solve it yourself or follow my methods.

## Challenge: Can You See
```
Requirements: The challenge requires you to download a given zip archive containing a jpg image.
Theory: We can use the tool exiftool to look at the image's properties and attributes.

$ unzip unknown.zip
- We are given a file named ukn_reality.jpg

$ exiftool ukn_reality.jpg
- We can see the properties and attributes, one particular form stands out which is the 'Attribution
URL', and it looks like it's base64 encoding of something.

$ echo 'cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==' | base64 -d
- We are then presented with the flag.
```

## Challenge: Time-Machine
```
Requirements: The challenge requires you to download a challenge.zip and unzip it first.
A directory named drop-in will be extracted in your webshell or local machine.

Theory: Since it's a git archive we can use git commands to help us solve this challenge
$ cd drop-in
$ ls - to show files in the directory
$ git log - This shows the commit logs, and you'll be presented with the flag.
```

## Challenge: Enhance
```
Requirements: A file is to be downloaded, drawing.flag.svg
Theory: After reading the documentation about svg files, it appears that they can be opened using a text editor like nano for example.

# $nano drawing.flag.svg
-- Solution: you can find the flag values distributed between tags at the end of the file.
```
