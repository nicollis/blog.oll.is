---
title: "Automated Code Review in Ruby"
author: "Nic Ollis"
date: 2016-05-09T16:00:02.000Z
lastmod: 2023-01-19T07:12:02-06:00

description: ""

subtitle: ""

image: "/posts/2016-05-09_automated-code-review-in-ruby/images/1.png" 
images:
 - "/posts/2016-05-09_automated-code-review-in-ruby/images/1.png"


aliases:
    - "/automated-code-review-in-ruby-ec4a2b7b19e3"

---

![rubocop](http://programpractical.com/wp-content/uploads/2016/05/Screen-Shot-2016-05-07-at-7.44.33-PM.png)


Today I wanted to review automating code review inside of ruby.  
Their meeting great open source projects to help make sure you are sticking to an idiomatic way of coding in ruby. The main one I will focus on today is Robocop and Robocop-git.

[Rubocop] (https://github.com/bbatsov/rubocop)is an open source gym for ruby that will review your project and let you know of any “best practices” you are not adhering too. As described on the Rubocop github page. Out of the box it will enforce guidelines set by the [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide).

Best of all, not only will it report problems to you, but using the -a flag it can even auto correct many of the problems it fined.

Rubocop is extremely easy to install just run` gem install rubocop `from there you can easily run rubo cop on your project by just running `rubocop` in your terminal in the root of your project.

Rubocop can be a great tool for you to run on a project to try an help contribute when you are a new comer and still learning your way around ruby. However, don’t just go editing without thought. Sometime we might use `fail` instead of `rescue` because it looks better when reading. However, Rubocop wont know that and still tell you to correct it. This might lead to your efforts of helping out an open sourced project being shot down. Moral of the story, don&#39;t get to trigger happy just because Rubocop says it should be changed.

However, one issue is you might be working in a very large project and you don’t want to run rubocop on the whole project due to the time / complexity of the results. You might also just want to run Rubocop on the code changes you made.

For this project we have the project [Rubocop-git](https://github.com/m4i/rubocop-git) this is just an addition on top of rubocop. However, in this project it will parse your` git diff` data and only show you issues on the code you have changed. This is great for when you are just wanting to run a quick check on the code you contributed to make sure it wont get sent back for something silly as using some outdated method name / convention.

I personally have contributed to the rubocop-git project, although at the time of writing this it has still not been pulled into the master branch. I added the autocorrect flag `-a` found in the normal rubocop project back into the rubocop-git project. If you would like to start using this feature before it gets pulled into the master feel free to download the project on [my repo](https://github.com/nicollis/rubocop-git).

As a new developer I highly recommend using one of these gems while you are still learning the ropes to help you get productive quickly and not get things shot down because they didn’t conform to the style guidelines.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates, live stream alerts, and post on my journey from Senior IT Admin to Junior Developer. Subscribe to the Program Practical channel on [YouTube](https://www.youtube.com/c/Programpracticaltv). Feel free to ask any questions in the comments below, and don’t forget it’s always a good time to start to #LearnToCode
