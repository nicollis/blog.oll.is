---
title: "JavaScript Lesson Learned Thanks to Ruby"
author: "Nic Ollis"
date: 2016-02-05T10:30:19.000Z
lastmod: 2023-01-19T07:11:48-06:00

description: ""

subtitle: ""




aliases:
    - "/javascript-lesson-learned-thanks-to-ruby-b2800efc0207"

---

I have started working on a very small side project while I am learning Ruby. It’s just a simple time tracker that helps me with my current IT admin job. I have been trying some different time trackers like Toggle. While I find them awesome, in fact I’m using Toggle right now to track my time writing, they are just not suited for fast paced, high risk world of IT. Okay, maybe just fast paced sometimes, with no risk. Mainly I just needed something that could track time, I could give it a title, and then a few different text fields. One for private notes, and one for notes that would be up in the labor report.

Thanks to my time at [Free Code Camp](https://medium.com/u/8b318225c16a), not only did I have the knowledge that I could accomplish this, but I could even estimate how long parts of the project would take. During the creation of this application I am also studying Ruby with Chris Pine’s Learn To Program. One of the odd things about ruby is how it handles integers in strings.

I am very used to JavaScript where almost anything goes when putting things into strings. However, in Ruby you have to tell it “Hello, Player “ + my_number.to_s. This is especially true when adding single characters that are numbers to integers. Chris points out that by doing this how is the computer suppose to know what you want? If you had 2 + ‘5’, are you asking for 25 or 7?

In my program you can have multiple timers running at any given time. To simply running them all, I don’t store a list of all the timers time, I just get time time off the timer every second, update, and display the new time. I was doing something along the lines of the code below.

//Get time stamp, and split into minutes and seconds  
var timer = ($(event).html()).split(“:”);  
//Add turn time into seconds and add 1  
timer = (timer[0] * 60) + timer[1] + 1;  
/** Do turn back into string and update display **/

While this is legal JavaScript I was really shocked when after the timer hit a minute I was getting results like, 59, 1:01, 100:02, 10000:03. I was really confused on what was going on here. Luckily I had just read the chapter in learn to program that I mentioned before. The compiler really isn’t sure what I was waning so it just joined the stings as it saw proper. I updated my code with what you see below.

//Get time stamp, and split into minutes and seconds  
var timer = ($(event).html()).split(“:”);  
//Add turn time into seconds and add 1  
timer = Number(timer[0] * 60) + Number(timer[1]) + 1;  
/** Do turn back into string and update display **/

This time I specified that the string objects “timer” are to be treated as numbers and not strings. I was shocked to already start seeing some benefits to Ruby, but mostly that even now as someone new to the Ruby language I can see why people push that its a good language to learn. At first I was really thinking to have to call “.to_s” would just be tedious, it’s there for a good reason, and for newer programmers learning JavaScript the error I ran into might not be such an easy one to solve, that would have just been avoided by using a language that is a little more locked down.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates and post on my journey from Senior IT Admin to Junior Developer.
