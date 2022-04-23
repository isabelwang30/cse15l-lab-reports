# Lab Report 2
## Incremental Development, Bugs, and Symptoms
---
In this lab report, we will look at three changes made to the `getLinks()` method to address bugs. The method, given a Markdown file, returns a list of all the webpage links present *in Markdown format*, ie: \[text to display](link).

---
### 1. Wrongly Adding Image Links 

![code change diff](https://user-images.githubusercontent.com/103291789/164933944-5bab024a-d9b7-4484-a492-76753174b6d0.jpeg)

* [Failure-inducing input](https://github.com/isabelwang30/markdown-parser/blob/main/test-file2.md)
* Symptom (unexpected output): 
```
[https://alink.com, anotherlink.html, https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/dog-puppy-on-garden-royalty-free-image-1586966191.jpg?crop=1.00xw:0.669xh;0,0.190xh&resize=1200:*]
```
* Expected output: 
```
[https://alink.com, anotherlink.html]
```
* The symptom in this case is an image link being wrongly added to the returned list. This was caused by a bug: not confirming that the open bracket (`[`) doesn't have an exclamation mark (`!`) immediately preceding it, before adding the substring within the parentheses to the list. The failure-inducing input (test-file2.md), allowed me to see the symptom, which then led me to searching for, finding, and fixing the bug.
