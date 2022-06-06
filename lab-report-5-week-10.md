# Lab Report 5
## Mass Tests for Two Implementations of the `getLinks()` Method
---
In this lab report, we will look at two specific results of testing two implementations of the `getLinks()` method on 652 test files. The method is previously discussed in [Lab Report 2](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-2-week-4.html) and [Lab Report 4](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-4-week-8.html). The two implementations we will look at are:
1. My own, located in my [markdown-parser repository](https://github.com/isabelwang30/markdown-parser).
2. One provided to us for Lab 9, located in [this repository](https://github.com/nidhidhamnani/markdown-parser).

---
### 1. Finding Two Tests with Different Results
* I used a bash script with a for loop to run the `MarkdownParse` file with each of the 652 test files in the `test-files` folder:

![bash script](https://user-images.githubusercontent.com/103291789/172091175-adcb0b92-ef3f-4404-b662-d800993e4846.jpeg)

* For each implementation, I redirected the output to a file called `results.txt`, and then used `vimdiff` to compare the outputs.
* Two test files that resulted in different outputs from each implementation were [`489.md`](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/489.md) and [`519.md`](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/519.md).

### 2. Test File `489.md`
* The expected result for file `489.md` (according to VSCode's preview) is:

```
[]
``` 
![VSCode preview](https://user-images.githubusercontent.com/103291789/172091220-09052e58-15d5-4a49-afd8-58c8f6500b6d.jpeg)

* These are the results from my implementation (left) and the other implementation (right):

![vimdiff 489](https://user-images.githubusercontent.com/103291789/172091240-840c601a-9d3d-4083-a49d-3e049460c574.jpeg)

* My implementation is incorrect, since it adds the link with a newline character to the returned list. The other implementation is correct, since it doesn't add the link to the returned list. 
* To fix my implementation, I would add an `or` statement to the highlighted statement on line 28 to also check the link for any newline characters. If there are any newline characters, the link should not be added to the result list:

![code to change](https://user-images.githubusercontent.com/103291789/172091292-2e44a002-20ea-4142-9ac3-9365fe6db0b0.jpeg)

### 3. Test File `519.md`
* The expected result for file `519.md` (according to VSCode's preview) is:

```
[]
``` 
![VSCode preview](https://user-images.githubusercontent.com/103291789/172091335-e47684c5-7599-45c9-95a3-826dd76fdcc7.jpeg)

* These are the results from my implementation (left) and the other implementation (right):

![vimdiff 519](https://user-images.githubusercontent.com/103291789/172091371-7db8fcb5-16f3-4e03-abf5-f412a5554334.jpeg)

* My implementation is correct, since it returns an empty list. The other implementation is incorrect, since it adds an image link to the result list.
* To fix the other implementation, I would add an `and not` statement to the highlighted statement on line 75 to make sure there isn't a `!` immediately before the opening bracket `[`. Only if that condition is also satisfied should the link be added to the result list:

![code to change](https://user-images.githubusercontent.com/103291789/172091417-b5f05f1b-949c-47aa-b54d-12a9f5ed333a.jpeg)
