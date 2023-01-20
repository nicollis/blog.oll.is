---
title: "Developing Ruby on Windows"
author: "Nic Ollis"
date: 2016-02-24T16:13:43.000Z
lastmod: 2023-01-19T07:11:55-06:00

description: ""

subtitle: ""




aliases:
    - "/developing-ruby-on-windows-1439e693f760"

---

So far I have stuck to my guns and continued to develop with Ruby on Rails on a Windows machine. I am overall quite happy with my experience although I have ran into some fun roadblocks.

One of the biggest issues I have found with developing on Windows has been Ruby Gems not fully supporting it. The first Gem I encountered with issues was “ReRun” a nice little gem that would auto reload my Sinatra app when it noticed files had been changed. While this gem isn’t needed now that I’m on Rails, it completely fails to run on Windows. Further investigation shows a developer who is quick to throw in the towel saying that he has no access to a windows machine so he will not be fixing it. This bothers me for a few reasons but mainly I run a MacBook Air. Even that small laptop runs a windows 7 VM on top of OS X without issues. However, the Gem is open sourced, so I feel the real reason it lacks support is because it lacks interest. However, it’s important to note for Windows developers that not all gems play nice.

I also wonder as time goes on if gem problems isn’t a good thing. For many new developers one of the challenges I find my friends face is learning to search for solutions. While you can make the argument that it could make new developers shy away from learning to program, I argue that it can help make them better programmers over time.

One of the Rubiest from our Indy meetup had mentioned he isn’t against developing on Windows. However, when you are making the money software developers made the cost difference is really minimal to be more productive. After all once you have learned enough to land a job it might be best not to spend 1/2 of your continued learning time troubleshooting windows only gem bugs.

However, I feel that the paywall of learning ruby shouldn’t hang on developers pushing would-be developers to by a who new computer. I’ll be releasing a video series soon for setting up Ruby on Rails on a Windows machine and some of the house cleaning things to make the setup easy. However, for now if you are looking into becoming a Ruby developer and don’t have the cash for a hot new Mac, or don’t want to spend the money on it I have three recommendations.

1.  Go for it, you will run into many issues on a Mac as well, while it might not be as much it’ll take the same skills to resolve so might as well get some good experience.
2.  Go used. I live near a University, its common for them to have outlet stores to sell old equipment. You can pick up 2–3 year old Mac Mini’s for $300 there.
3.  Go cloud. Using a service like Cloud9 is amazing because you get a full Ubuntu virtual machine and IDE in the browser. I use this now for some projects to make it easy to go back and forth between my desktop and laptop without having to worry about if I pushed code to GitHub.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates and post on my journey from Senior IT Admin to Junior Developer. Feel free to ask any questions in the comments below.
