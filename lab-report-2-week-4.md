# Derek Ma Lab Report 2

Hello! This lab report demonstrates 3 code changes that our group did in labs 3 and 4.

## Code Change one

Screenshot of code change diff:

![sscc1](sscc1.png)

Link to test file for this failure-inducing input:

[test2.md](https://raw.githubusercontent.com/Prodlax/markdown-parse/ccc40cabe3dcb0edf868570196ae4491a0388432/test2.md)

Symptom of failure inducing output:

`[, hello.html]`

Explanation:

For this output, we had a set of `[]` and `()` that was seperate from each other but in succession. The way our programs output before the change is that it looks for the characters `[]()` in that order and takes the link, which is whatever is in between `()`. However, `[]()` in that order may not actually refer to a link, as shown in test2.md (we have an array and then a pair parenthesis thrown in the file). The symptom we get is an unexpected output: we are expecting `[hello.html]`, but in reality we get `[, hello.html]` since our output detects the links improperly.

## Code Change two

Screenshot of code change diff: 

![sscc2](sscc2.png)

Link to test file for this failure-inducing input:

Symptom of faiure inducing output:

![ssfailure2.png](ssfailure2.png)

