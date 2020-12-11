---
title: A Code Reviewer Guide to Code Review
date: 2020-05-01 14:00:00 +0100
categories: [Blogging, Code Hygiene]
tags: [code_reviewer_guide]
---
## Introduction
This article aims to present the code reviewer developer guide adopted by Google. The goal of having code reviews is to maintain the quality of the code, and ultimately the product. A code review process can be described as a person examining a code other than the author of the code.

## **How to do a code review ?**
A code reviewer usually looks for design, functionality, complexity, tests, naming, comments, style, and the documentation (we will go into detail of each of these later in this article) of the changelist (CL) and the code associated with it. A CL is (change or path in other companies) is a list of changes submitted by a developer with their code. A code-review can also happen via pair-programming where code is written jointly with a senior and junior developer then it is considered reviewed already.

## **The Standard of Code Review**

Generally, there are two tradeoffs to look at when examining code, the quality of code itself vs frequency of time code changes are being submitted by the developers.

In terms of quality of code: if they are pressured for quality with no time constraints then no code will ever be submitted which means the codebase will never be improved. The "perfect code" syndrome in developers might lead to no code being a developer at all. Moreover, if the standards are too high, developers can also feel demotivated since none of their work is making it to production.

In terms of code frequency:  if developers are rushed to submit code, they will take shorts cuts which will affect the overall health of the codebase, since there will be no adequate time for proper design and thoughtful consideration of the code functionality. The codebase health will generally be reduced across time as code gets bulkier, more processes to execute with the features, and might clog the whole process of code review.

Therefore, a threshold must be set to balance both the quality of code and code frequency.

As a general thumb of rule, a code that improves the overall code health of the system should be approved even if it is not perfect. On the other hand, if a code is perfect and well-designed but is a feature that is not requested then it should be denied. There is no such thing as perfect code but rather a better code. Code that gives forward progress to the product with better overall health should always be the preferred code.

Code reviews should be based on technical facts and evidence with data rather than the personal preference of an individual. In terms of styling, the official style guide of the language/framework is the supreme authority. This will make it easier for other developers to understand code and onboard fresh developers in the future. When it comes to resolving conflicts, it is always best that the developer and the reviewer agrees. If no agreement is reached, then it should be escalated to a technical lead or an engineering manager. Regardless of the choice, a CL should not sit around in the tasks because the reviewer and the developer cannot agree.

## **What to look for in a code review**

Here are the 12 things a code reviewer should look in a CL submitted by a developer.

Design: The first question is, does the interaction between the different pieces of class, functions, and code interact well with each other and in a way that makes sense? This is to ensure the overall health of the codebase and facilitates understanding when onboarding new developers. The second question to ask is if this is a good time to add functionality to the database.

Functionality: A changelist should tick two boxes. First, does it do what the developer intends it to do (mentioned in the CL), and secondly, does it work as the user who requested the feature does? and finally, can other developers build functions on top of it and extend it. A code reviewer should be thinking about edge cases, how the intended user will use it, and concurrency problems. Sometimes, it is hard to understand the full impact of a CL, so it is always good to also examine the UI change coming along with the code change. A demo of how the UI change is best. It is also important to examine the code to check for any deadlocks or race conditions that might raise from parallel programming.

Complexity: this can be a tricky world to describe, as in "how complex is considered complex?" As a rule of thumb, when a class or function is not understood quickly by a code reader that usually means developers can introduce bugs when they call it or modify the code down the line. Another type of complexity is “over-engineering” where the code does more than intended or extends features that are not requested. The code must resolve current bugs or add currently required features and not speculate on what the user might want in the future. Moreover, a CL might bulk up a lot of changes, so it might make sense to split a CL into multiple CLs.

Tests: CL must ship with their unit tests, integration tests, and functional tests (unless it is an emergency, we defined that terminology later). Tests should fail if the code is broken or does not mean the CL and/or feature requirement, and not produce false positives. The test should be checked by a human and makes sure they are simple, useful with correct assertions.

Naming: a good name describes what the item does.

Comments: are the comments there actually necessary? Comments should explain why this particular code exists and not what the function is doing. The code should be clear enough to explain itself without needing any comments. This is not to be confused with documentation that expresses the purpose of the code, how it should be used, and how it must behave.

Style: Follow the official style guide. Another good resource is the official style guides by Google http://google.github.io/styleguide/

Consistency: By following the guide, consistency will naturally prevail in the codebase

Documentation: A CL change should also include updating relating API docs, READMEs, and any other referenced documents.

Every line: Code reviewers should read every line and try to understand the code. If a line does not make sense, ask the developer for an explanation or find a qualified person if it is out of your expertise area.

Context: Sometimes it would make more sense to look at the bigger picture by examining the whole file instead of the few changed lines to get a perspective of the code change. It is usually helpful to think of the CL as part of the general codebase health and judge if this increases the overall health of the codebase. Most systems eventually get complex by many minor small changes, so it is important to always stop minor complexities in new changes.

Good Things: Code reviewers usually focus on the bad things and criticizing, it is also important to show encouragement and appreciation. It is also important to tell what has been done well and what practices have been met. Developers will usually then thrive to meet such expectations for the next time.

Taking the above points into consideration, one can ensure a good code review practice. Another important question to tackle is, how fast should code reviews be carried out? A maximum of one business day! This will help to not frustrate the developer. Developers usually start working on the next feature as soon as they submit a CL and if the code reviewer is not fast enough that might interrupt the developer several times to look at the CL which probably they have already forgotten about. However, it is important to also not sacrifices the quality of code for velocity. Ideally, the feedback should be in one business day, but the reviewing process can take longer especially if it is a large CL that cannot be divided into smaller CL. The only time code review can be relaxed is during an emergency. An emergency is a small CL that will allow a major launch and fixes a bug that is significant for production, handles a legal issue, or closes a major security hole. The only thing that is important for the cod review part is "does it resolve the emergency?" Every other rule can be relaxed. After the emergency is dealt with, the code can be examined thoroughly as to standard procedures being implemented in the company.

To finalize, let us talk on how to write code review comments. Always be kind, explain your reasoning, and encourage developers to simplify code rather than explain to you. Always comment about the code and not the developer. By adjusting the above to fit your code review needs, I'd hope you have a smoother and healthier codebase for your products!
