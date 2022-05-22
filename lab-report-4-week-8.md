# Lab Report 4
## JUnit Tests for 2 Implementations of the `getLinks()` Method
---
In this lab report, we will look at running three test methods for two different implementations of the `getLinks()` method, which is discussed in [Lab Report 2](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-2-week-4.html). The two implementations of `getLinks()` we will look at are:
1. My own, located in my [markdown-parser repository](https://github.com/isabelwang30/markdown-parser).
2. One from lab group 6, located in [Leah Kuruvila's markdown-parser repository](https://github.com/leahkuruvila/markdown-parser).

---
### Test 1: Link Formatting Containing Backticks (`) for Inline Code
* This is the first markdown snippet being passed in: 
```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

* This is the expected output (from using VSCode's preview):
```
["`google.com", "google.com", "ucsd.edu"]
```

**insert screenshot here**

* This is the test method I wrote for the snippet:

**insert screenshot here**

* The test failed when running on my implementation. This is the output that shows the failure:

**insert screenshot here**

* The test also failed when running on the other implementation. This is the output that shows the failure:

**insert screenshot here**

// TODO: answer code change question

### Test 2: Link Formatting Containing Nested Parentheses and Brackets, and Escaped Brackets
* This is the second markdown snippet being passed in: 
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

* This is the expected output (from using VSCode's preview):
```
["a.com", "a.com(())", "example.com"]
```

**insert screenshot here**

* This is the test method I wrote for the snippet:

**insert screenshot here**

* The test failed when running on my implementation. This is the output that shows the failure:

**insert screenshot here**

* The test also failed when running on the other implementation. This is the output that shows the failure:

**insert screenshot here**

// TODO: answer code change question

### Test 3: Link Formatting Containing Line Breaks and a Lot of Text in the Link Name
* This is the third markdown snippet being passed in: 
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```

* This is the expected output (from using VSCode's preview):
```
["https://www.twitter.com", "https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule", "https://cse.ucsd.edu/"]
```

**insert screenshot here**

* This is the test method I wrote for the snippet:

**insert screenshot here**

* The test failed when running on my implementation. This is the output that shows the failure:

**insert screenshot here**

* The test also failed when running on the other implementation. This is the output that shows the failure:

**insert screenshot here**

// TODO: answer code change question