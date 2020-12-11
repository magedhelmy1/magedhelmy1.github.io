---
title: A Developer Guide to Writing CL Changes
date: 2019-04-01 14:00:00 +0100
categories: [Blogging, Code Hygiene]
tags: [developer_guide]
---
## Writing a Good ChangeList (CL) Description:

A CL description is a record of what change is being made, and why it has been made. This is submitted along with the code you have written. It will also be part of the version history making it a critical piece of the overall design structure. Potentially, many hundreds of future developers will read it to understand why certain piece of code was implemented that way.

There are several standards that can be followed on how to fill the CL. For example, in the medical world there is an extensive document IEC 62304 containing all the information the CL should consist of.
In general, a CL first line should contain a short summary of what the code changes actually does. This line should be a good summary that future developers can search this change by keywords in this line.
For the body of the CL, it can include a brief description of the problem, and why this specific approach has been implemented with the shortcomings of this method. It can also be relevant to include bug numbers, benchmark result and links to design documents.  Everything that needs to be understood about the code change is found in the CL.

## Smaller CL:
Creating smaller, simpler CL should always be the aim. They are easier to review and are less likely to have back-forth comments to explain things. Smaller CL are also likely to introduce bugs, and it will be less wasted time if rejected.  A small CL can define as a change that does just one thing. This can be part of a feature rather than the whole feature at ones.  Moreover, if the CL is big, you can separate the validating tests, refactoring tests and integration tests into separate CL. However, if separate CL will break the build, then it is better to submit a large CL. The code reviewer may implement the CLs with a few minutes gap and in those gaps we don’t want to break the build. It is also good practice to speak with the code reviewer before hand about the CL size and what is acceptable.

## Handling Reviews:
It is highly likely to get comments back on the CL, don’t take it personally. The code reviewer goal is to help you and keep the codebase healthy. Even if the critique seems frustrating, ask yourself “What is the constructive thing the reviewer is trying to tell me ?” Never respond to anger since this is not professional etiquette. Book a meeting with the reviewer and explain it in a constructive and polite way. Always start with the question, “is the reviewer correct” if you do not understand the comments, ask for clarifying comments. Sometimes since you have been working on the code for a while, the reviewer has no context of what you have been working on. So do fill them in with more information and context when necessary.
If the code reviewer does not understand the code, it is highly likely future developers will also not understand the code.  Therefore, elaborate in your CL or your simplify the code.
