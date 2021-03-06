[< Home](https://isabelwang30.github.io/cse15l-lab-reports/)
# Lab Report 2
## Incremental Development, Bugs, and Symptoms
---
In this lab report, we will look at three changes made to the `getLinks()` method to address bugs. The method, given a Markdown file, returns a list of all the webpage links present *in Markdown format*, ie: `[text to display](link)`.

---
### 1. Wrongly Adding Image Links 

* [Failure-inducing input](https://github.com/isabelwang30/markdown-parser/blob/main/test-file2.md)
* Symptom (unexpected output): 
```
[https://alink.com, anotherlink.html, https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/dog-puppy-on-garden-royalty-free-image-1586966191.jpg?crop=1.00xw:0.669xh;0,0.190xh&resize=1200:*]
```
* Expected output: 
```
[https://alink.com, anotherlink.html]
```
* Changes made: 

![code change diff](https://user-images.githubusercontent.com/103291789/164939007-eae000f5-67fc-42d9-a305-e59bdb6a92e1.jpeg)

* The symptom in this case was an image link being wrongly added to the returned list. This was caused by a bug: not confirming that the open bracket (`[`) doesn't have an exclamation mark (`!`) immediately preceding it, before adding the substring within the parentheses to the list. The failure-inducing input (test-file2.md) allowed me to see the symptom, which then led me to searching for, finding, and fixing the bug.


### 2. Empty Lines at the End of the File

* [Failure-inducing input](https://github.com/isabelwang30/markdown-parser/blob/main/test-file2.md) (there are two blank lines at the end of this file)
* Symptom (Exception thrown):
```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: -2
        at java.base/java.lang.StringLatin1.charAt(StringLatin1.java:48)
        at java.base/java.lang.String.charAt(String.java:1512)
        at MarkdownParse.getLinks(MarkdownParse.java:19)
        at MarkdownParse.main(MarkdownParse.java:31)
```
* Changes made:

![code change diff](https://user-images.githubusercontent.com/103291789/164939329-fdfcccdf-fa7f-42d7-a21e-e1ca61b93df7.jpeg)

* The symptom in this case was a `StringIndexOutOfBoundsException` being thrown when there were empty lines at the end of the input file. The error message indicated that the program was trying to index a string at index -2, which is an error in Java. The bug causing this was that the `indexOf()` method returns `-1` when the specified substring is not found starting at the given index. Then, the code block that checks for an image link subtracts 1 from the `openBracket` index (which in this case is -1), which leads to the attempted indexing at index -2. The failure-inducing input (test-file2.md) allowed me to see the symptom, which then led me to searching for, finding, and fixing the bug.


### 3. Brackets and Parentheses Far Apart in the File

* [Failure-inducing input](https://github.com/isabelwang30/markdown-parser/blob/main/test-file4.md)
* Symptom (unexpected output):
```
[link.com]
```
* Expected output:
```
[]
```
* Changes made:

![code change diff](https://user-images.githubusercontent.com/103291789/164939476-a3d070db-2a36-4f59-a7c4-35799c5274e5.jpeg)

* The symptom in this case was that a "link" was added to the list, even though it wasn't in proper Markdown format (the pairs of brackets and parenthese were not back-to-back). The bug causing this was the method not confirming that the closing bracket was immediately preceding the opening parentheses. The failure-inducing input (test-file4.md) allowed me to see the symptom, which then led me to searching for, finding, and fixing the bug.
