---
layout: post
title:  "Why We Should Refactor"
date:   2016-08-29 20:00:00 +0700
categories: programming
published: true
---

An application, in course of time, tends to grow. The reason for its growth is usually feature addition, rarely a bug fix adds complexity to existing software. Additional requirements, in the other hand, will add complexity to the application.

And in a company, a software is often not maintained by a single person. Variation of coding skill and styles can add another complexity to the old codebase. One common sign that your application is suffering this problem is when a mere bug fix can break the whole system.

<!--more-->

# Examples

## _God Object_

In object oriented programming world, we know classes. A specific class can be reused in another place, this is one basic principle of object orinted programming. Sometimes, when we reuse a class, we might think that we need an additional _feature_ for that class to solve our current (new) problem.

Time passes, and when we realized, we already added a whole thousand lines to the original class. By this time, we will realize that:

  * Some functions/variables should be in another place
  * The code is horrendously difficult to test
  * Some orphaned code block(s)
  * Some unnecessary inheritances/implementations
  * ...and so on

<img src="https://hsto.org/storage2/4b3/14a/414/4b314a414b39ff15f116d6f99841b65c.png" />

The _maintenance cost_ of the class become increasingly high, feature addition involving this class will become a high risk task, writing test (if the class is testable at all) is unnecessarilly dificult.

## _Cyclomatic Complexity_

Control flows are good. It represents logical flow of the application. Heck, a program cannot make decision without it. But excessive usage of control flows makes the code difficult to read and debug.

<img src="http://www.expertsmind.com/CMSImages/206_Determine%20the%20cyclomatic%20complexity.png" />

Really, when your function contains too many control flows, you may want to refactor it. Because it is tempting to add another `if` or `else` for new requirements. And if you do, and the complexity builds up, it will become a dreadful task to just fix a hidden bug.

# Why does this happen?

This is a common problem faced by old code base that neglects the importance of refactoring and the riddance of code _smells_. By experience, I can identify some reasons why bad code can grow in your codebase.

## Pressing Deadlines

Deadlines may encourage developers to cut corners. When a developer focuses on deadlines, these things could happen:

  * Added stress factor to the developer.
  * Could care less about code quality, when the code runs once, it is considered done.
  * Skips test creation
  * Encourages the developer to work overtime. And when he does, the overtime period is often not as effective. Too much time working could add another stress factor too.

A rushed feature can add more debt to the system. Because at one point of time, you will revisit that code. Either for fixing some bugs or adding new feature that involves modification to the existing code. When the code is badly written, it can add complexity to the new feature creation that is unpredictable.
