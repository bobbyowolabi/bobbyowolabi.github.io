---
layout: post
title: What Makes a Good Test
bigimg: 
description: null
comments: true
published: false
---



Testing Principles
Readability
Quickly See
Inputs
Component Under Test
Output
Assertions
I’ve recently been using the Builder pattern a lot for this where i make assertions a lot easier to read by hiding the assertion logic while stringing together a bunch of well named assertions.
Boilerplate Code Can Be distracting
Extract, test Data, Assertion Log
Reliable & Trustworthy 
The problem with end to end system testing is flakiness
User experience when getting failure summary, you are sure something is wrong and not a false positive
Actionable
Goes to one of the points “Working towards providing more context into why a given test case fails, analyzing error logs from tests, and providing users with hints to reduce troubleshooting time.”  I go to lengths of even making sure that exception messages are correct (in a flexible way).  You could throw the same exception but for different reasons and at different branches.
