---
layout: post
title: What Makes a Good Test
bigimg: 
description: null
comments: true
published: false
---

In our current age in software engineering with AI, testing is becoming more and more of a talking point.  If code 
generation is becoming cheaper and cheaper and no longer the value proposition, verification and quality might be the new 
coveted outputs.  

Recently, a widely used open source library would re-written, next.js, by 1 engineer in a week [reference Evan king's post].  How was this accomplished? 
The AI made the new implementation pass all the tests.  So the tests are very valuable and are becoming the more important 
than the code itself.  The tests were the specification instead of seardhing and trying to understand the codebase.  
There is a growing school of thoguht that writing code will at somepoint become taboo in the same way the average engineer would never think to write machine code.  
Someone even compared looking at source code in the future will be as archiacic as looking at 
machine code or binary stuff, things that you just don't do.

Given all the emphasis on tests, I'd thought I'd share what I believe are good qualities of a test.  Its ironic, this blog post could become irelevant in 6months given the rapid pace of change in the industry.  but I like testing, so why not?  
Also, the verification of AI systems and also verying AI produced code isn't totally a solved problem. [reference carlos post on testing ai systems]
I am talking more of the standpoint of a unit like test that you would write in code.  There are different types of tests and verification
methods. (i.e. simulation, adverserial, mutation testing ,etc).  For this purposes.  I am talking about good olf classic
unit tests.

# Readable
What is a test.  I like to think of a test as consisting of 3 things:
Inputs / Environment State
Execution Call / Sequence of System Under Test
Assertions of Output

I love it when these 3 things are very clear and are easy to read.  
'It should be easy to see what conditions of the system under are being tested.  In recent time, i have played around with using the Builder pattern for expressing state.  It shouldk be easy to see how the component is being called.
```java
System.o
```
I’ve recently been using the Builder pattern a lot for this where i make assertions a lot easier to read by hiding the assertion logic while stringing together a bunch of well named assertions.
Boilerplate Code Can Be distracting and should be abstracted away.
It should be easy to see what verifications are being made.

Tests are written to ensure that a system works, but they are also written for humans (well we don't know for how long).  If a test fails, you often have 
to debug and reason with it, I think it is worth the investment to make sure that they are easy to read.


Reliable & Trustworthy 
Getting False positves - engineers will tune out the test reports,  sorta like the wolf that cried wolf.
The problem with end to end system testing is flakiness
User experience when getting failure summary, you are sure something is wrong and not a false positive

Actionable
Show example of test failing due to IOException.  this is not actionable and is a terrible experience.  You have to start at square one to debug what's going on
Goes to one of the points “Working towards providing more context into why a given test case fails, analyzing error logs from tests, and providing users with hints to reduce troubleshooting time.”  I go to lengths of even making sure that exception messages are correct (in a flexible way).  You could throw the same exception but for different reasons and at different branches.


https://www.linkedin.com/posts/carlos-arguelles-6352392_so-excited-that-my-conversation-with-fellow-activity-7399487491898183681-repc?utm_source=share&utm_medium=member_desktop&rcm=ACoAAC29vlYBxPI-WLwEl7Gn_bFXjdVcoTiAN1U
https://www.linkedin.com/posts/evan-king-40072280_the-cloudflare-nextjs-rewrite-is-all-over-activity-7432466656611774464-Ta_F/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAC29vlYBxPI-WLwEl7Gn_bFXjdVcoTiAN1U