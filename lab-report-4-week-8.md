# Lab Report 4
## JUnit Tests for 2 Implementations of the `getLinks()` Method
---
In this lab report, we will look at running three test methods for two different implementations of the `getLinks()` method, which is discussed in [Lab Report 2](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-2-week-4.html). The two implementations of `getLinks()` we will look at are:
1. My own, located in my [markdown-parser repository](https://github.com/isabelwang30/markdown-parser).
2. One from lab group 6, located in [Leah Kuruvila's markdown-parser repository](https://github.com/leahkuruvila/markdown-parser).

---
### Test 1: Link Formatting Containing Backticks (`) for Inline Code
* This is the first markdown snippet being passed in: 

    `[a link`](url.com)

    [another link](`google.com)`

    [`cod[e`](google.com)

    [`code]`](ucsd.edu)

* This is the expected output (from using VSCode's preview):

    ["`google.com", "google.com", "ucsd.edu"]

![snippet1 preview](https://user-images.githubusercontent.com/103291789/169705323-269e1566-583e-408b-a1ea-0ba32df153bc.jpeg)

* This is the test method I wrote for the snippet:

![snippet1 test](https://user-images.githubusercontent.com/103291789/169705353-72c7df39-be94-4a26-ae8d-2cd2386db93b.jpeg)

* The test failed when running on my implementation. This is the output that shows the failure:

![test1 my implementation](https://user-images.githubusercontent.com/103291789/169705366-09bdd19f-cf55-43c6-b198-dc6378a04365.jpeg)

* The test also failed when running on the other implementation. This is the output that shows the failure:

![test1 other implementation](https://user-images.githubusercontent.com/103291789/169705385-fcd60e9e-3ddb-46f8-ae5d-81e3aea055e0.jpeg)


// TODO: answer code change question

### Test 2: Link Formatting Containing Nested Parentheses and Brackets, and Escaped Brackets
* This is the second markdown snippet being passed in: 

    [a [nested link](a.com)](b.com)

    [a nested parenthesized url](a.com(()))

    [some escaped \[ brackets \]](example.com)

* This is the expected output (from using VSCode's preview):

    ["a.com", "a.com(())", "example.com"]

![snippet2 preview](https://user-images.githubusercontent.com/103291789/169705394-7fbc13e6-f403-4b41-a40e-e81e081ce47e.jpeg)

* This is the test method I wrote for the snippet:

![snippet2 test](https://user-images.githubusercontent.com/103291789/169705442-523b4d11-569b-410f-9085-30aa29adef0f.jpeg)

* The test failed when running on my implementation. This is the output that shows the failure:

![test2 my implementation](https://user-images.githubusercontent.com/103291789/169705460-fc47f776-5deb-4f61-96e9-e7058814813a.jpeg)

* The test also failed when running on the other implementation. This is the output that shows the failure:

![test2 other implementation](https://user-images.githubusercontent.com/103291789/169705475-3b190e6c-fdfd-4742-a544-96cca2804739.jpeg)


// TODO: answer code change question

### Test 3: Link Formatting Containing Line Breaks and a Lot of Text in the Link Name
* This is the third markdown snippet being passed in: 

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

* This is the expected output (from using VSCode's preview):

    ["https://www.twitter.com", "https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule", "https://cse.ucsd.edu/"]

![snippet3 preview](https://user-images.githubusercontent.com/103291789/169705518-7b2e85a8-a3c8-4c3a-a83e-793e5bba196a.jpeg)

* This is the test method I wrote for the snippet:

![snippet3 test](https://user-images.githubusercontent.com/103291789/169705527-6fc35ebd-e14a-426f-92b1-cba775842203.jpeg)

* The test failed when running on my implementation. This is the output that shows the failure:

![test3 my implementation](https://user-images.githubusercontent.com/103291789/169705536-150e4a60-2928-448e-8d41-edb588c5bc25.jpeg)

* The test also failed when running on the other implementation. This is the output that shows the failure:

![test3 other implementation](https://user-images.githubusercontent.com/103291789/169705551-33f4ee46-c754-41ea-980a-eb5429c28450.jpeg)


// TODO: answer code change question
