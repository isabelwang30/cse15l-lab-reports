# Lab Report 5
## Mass Tests for Two Implementations of the `getLinks()` Method
---
In this lab report, we will look at two specific results of testing two implementations of the `getLinks()` method on 652 test files. The method is previously discussed in [Lab Report 2](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-2-week-4.html) and [Lab Report 4](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-4-week-8.html). The two implementations we will look at are:
1. My own, located in my [markdown-parser repository](https://github.com/isabelwang30/markdown-parser).
2. One provided to us for Lab 9, located in [this repository](https://github.com/nidhidhamnani/markdown-parser).

---
### 1. Finding Two Tests with Different Results
* I used a bash script with a for loop to run the `MarkdownParse` file with each of the 652 test files in the `test-files` folder:

**insert screenshot here**

* For each implementation, I redirected the output to a file called `results.txt`, and then used `vimdiff` to compare the outputs.
* Two test files that resulted in different outputs from each implementation were [`489.md`](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/489.md) and [`519.md`](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/519.md).

### 2. Test File `489.md`
* The expected result for file `489.md` (according to VSCode's preview) is:

```
[]
``` 
**insert screenshot here**

* These are the results from my implementation (left) and the other implementation (right):

**insert screenshot here**

* My implementation is incorrect, since it adds the link with a newline character to the returned list. The other implementation is correct, since it doesn't add the link to the returned list. 
* To fix my implementation, I would add an `or` statement to the highlighted statement on line 28 to also check the link for any newline characters. If there are any newline characters, the link should not be added to the result list:

**insert screenshot here**

### 3. Test File `519.md`
* The expected result for file `519.md` (according to VSCode's preview) is:

```
[]
``` 
**insert screenshot here**

* These are the results from my implementation (left) and the other implementation (right):

**insert screenshot here**

* My implementation is correct, since it returns an empty list. The other implementation is incorrect, since it adds an image link to the result list.
* To fix the other implementation, I would add an `and not` statement to the highlighted statement on line 75 to make sure there isn't a `!` immediately before the opening bracket `[`. Only if that condition is also satisfied should the link be added to the result list.