+++
title = "Never Stop Running"
authors = ["ludo"]
description = ""
tags = []
date = "2011-10-14T10:00:00"
+++

**From the moment you are born until the moment you die your body works hard to survive, but eventually the parts wear out and maintenance becomes too hard. In some way software is just like a human body. It is born, will be patched up numerous times during its lifetime and it becomes obsolete and is then cleaned up.**

Humans visit hospitals and doctors to have their health checked periodically, the health of software can be checked by running its accompanying test suite. But how often should we run these tests? And when can we "pull the plug"?

![](jenkins.png)

Six months have passed... Will it still build?

When the first customer starts using your software it magically enters the realm of legacy. Being legacy doesn't mean it is suddenly bad software, nor does it mean that it is no longer useful. It *does* mean that you will probably be maintaining it for an extended period of time. Other than that you will probably want to improve the product, extend it and build upon it. So, you can be pretty confident that your product will continue to grow – I have yet to see a product where in any given release more features were removed than new features had been added. To facilitate all this, monitor quality and be able to fearlessly improve on your product you have an extensive suite of tests. To make sure that your product keeps working as inteded over time you have a continuous integration server that runs all your tests whenever code is pushed to your source repository.

But, times change, seasons come and go and your product becomes stale and less and less work has to be done on it. Less changes and less builds mean that your test suite runs less often. Eventually you may even disable the job in your continuous integration server as part of your yearly spring cleaning.

> An abandoned test suite is a loss of a valuable asset and an effective way to destroy capital.

This is where you should stop and think for a moment. By removing a test suite from your build server you lose control over the suite. Now, if someone fixes a bug in the codebase you do not know if the tests pass. You might not even know that anything was done to the codebase. If this goes on for some time your test suite and the production code will diverge until they reach a point where it seems no longer feasible to look at the tests at all. At this point your test suite is abandoned.

You don't want this to happen, do you? An abandoned test suite is a loss of a valuable asset and an effective way to destroy capital.

## Tips From the Trenches

Next time you look at your project's continuous integration configuration I want to encourage you to schedule your jobs to not only run when someone pushes a commit to your source repository but to also have it run on regular intervals. It might be feasible to run a test suite less frequently after a product is no longer actively supported, but removing it from the build server is a solid guarantee that your test suite will rot. It might even lead to the test suite being thrown out, leaving your product exposed and vulnerable.

![](jenkins_build_triggers.png)

Sample build schedule in [Jenkins](http://jenkins-ci.org)

In our case we are working with a lot of different projects, all in different stages of their lifetime. Most of our actively being developed projects are scheduled to build several times a day. An interesting time to test software is at midnight. I would have made a small fortune if I got a dime for every time tests fail – seemingly random – at midnight only to find out that there was an actual edge case that was unaccounted for because healthy developers tend to sleep at night. Builds for projects that see less active development are brought back to weekly and eventually monthly builds. I certainly wouldn't do anything longer than a monthly build because that would leave a too long period to track down whoever broke a build. It also notifies you of incompatible third-party software and libraries if you keep your integration server up-to-date. Is development spinning up again? Then you should adjust your build server accordingly [1]</sup>.

The one thing that you should *not* do is stop running your test suite. Ever.

<small>[1] Perhaps some sort of plugin could do this spinning up/winding down by looking at the frequency of commits to a code repository. Anyone know if something like this exists or are there volunteers for creating a Jenkins plugin?</small>