# How I Kick-Started Open Source Contribution with OSCC and So Can YOU!

By [Srinitya Kondapally](https://github.com/skonda29)

I can’t express the feeling in words when I received an email that my PR was merged into the pandas repo.

I am Srinitya Kondapally, a graduate student in Computer Engineering at Arizona State University. Prior to pursuing my Master’s degree, I worked as a Software Engineer at Optum, a United Health Group company where my focus was on building UI features and automation scripts.

Open source contribution has always been something that excited me because of its impact in real-world projects. I knew this is something I wanted to do but really didn't know where to start. So, when I saw an email about the Open Source Contribution Club (OSCC), I knew it was something I needed to pursue. My focus was not to solve a complex issue, but to simply start it, knowing that I can ask for help during work sessions if I encountered difficulties.

After doing the basic development setup for pandas using the documentation that OSCC provided, I reached out to the community and asked if I could be guided on selecting an issue, as it was my first open-source contribution. I then joined a work session where I received help in searching for and being assigned my first issue.

I began working on the issue over the weekend by understanding and reproducing the error. After researching, I identified a potential basic solution. I made the necessary code changes, pushed my branch to the repository, and requested feedback from the maintainer. The maintainer's feedback was critical in guiding me towards the correct solution. I understood their feedback and implemented the suggested changes. After another review, the maintainer confirmed the solution was correct. I'm proud to have made an open-source contribution, small but worthwhile.

> For everyone who's interested in the specifics (You know who you are!), here is a more detailed account of how I tackled the issue:  
> After taking a look at the issue, my first thought was, “Okay, ArrowExtensionArray must not have `.max()` or `.min()` methods.” This seemed like an easy fix: just add `max()` and `min()` methods just like numpy arrays and it should work. And yes, it worked with the example in the issue, and I confidently submitted [a PR](https://github.com/pandas-dev/pandas/pull/61924). But the maintainer’s feedback on the solution forced me to step back and think about the design of pandas' `iloc` method. It's meant to work universally, regardless of the underlying data storage. The core problem wasn't just that `ArrowExtensionArray` lacked `max()` and `min()` methods, it was that `_validate_key` was making an assumption about the *type* of array it was receiving when it could be various `ExtensionArray` implementations. It taught me that sometimes, the "right" fix is less about adding a line of code and more about refining the logic to be more general and maintainable.

The issue I worked on really deepened my understanding of pandas internals, especially around how indexing handles different backends. The most fulfilling part was seeing a small fix improve compatibility for PyArrow users, and the feedback from maintainers underscored how valuable continuous learning and mentorship are to growing as a contributor.

If you are an early-career technologist like me, join OSCC for...
* Mentorship and guidance
* Networking opportunities
* Visibility and recognition in the community
* Satisfaction of solving issues that have a huge impact on the software community.

Another contribution run by OSCC is in the works, details TBA. To stay informed, **please fill out [this form](https://forms.gle/L5z9ncVBHTvrefKr9).** Please join the club!
