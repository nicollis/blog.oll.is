---
title: "Blocks, Procs, Lambdas, oh my!"
author: "Nic Ollis"
date: 2016-05-30T18:55:43.000Z
lastmod: 2023-01-19T07:12:05-06:00

description: ""

subtitle: ""




aliases:
    - "/blocks-procs-lambdas-oh-my-8c636a54757c"

---

Today I wanted to go over Blocks, Procs, and Lambdas in Ruby via a easy and short over view. There are a lot of post on the subjects already so I am hoping to just give a high level overview to get your interest peaked on some of the most interesting parts of the Ruby language.

Above is my last video going over Blocks and how to use them so I will keep my blocks in here short.

To overly simply what these are in a way that will probably upset more senior developers:

*   **Blocks:** Chunks of code that will be ran in the parent method that dynamically changes the logic and results of the method.
*   **Procs:** Much like Blocks but stored as a variable, and can be passed into functions like a variable
*   **Lambdas:** A step closer to being full on functions than Procs, but are anonymous in their naming.

Ranking them in likely to be used:

*   **Blocks:** Used all the time; Good luck avoiding them
*   **Procs:** Not used as much, but can be helpful in a when using shared logic
*   **Lambdas:** Rarely used

So jumping into some examples Blocks in conjunction with the yield keyword give you an ability to dynamically change logic happening in the middle of a function. One I’m sure you have come across even if your highly new to programming is the .each function used with arrays or ranges.

What happens here is the .each is managing your loop for you and in each iteration is giving you the current variable its on in the loop and allowing you to do what you want to it. Then when control is handed back to the .each method it continues on with the loop.

Again see the video above if you would like to see Blocks in action.

I like to think of Procs as pointers to a function, although pointers are seem more in languages like C++ I believe it fits because of how they are used. Procs are great ways to pass commonly used blocks around in keeping in line with DRY logic. For example if I wanted to have a Proc that prints out the instance variable I would do something like below.

`my_new_proc = Proc.new { |x| puts x }`

I can easily use this now in any method that takes a block.

`(0..9).each(&amp;my_new_proc)`

Take note of the ampersand before the variable name. In C++ this would be how you call the address of a variable in memory. This would be why I say this reminded me of a pointer to a function in C++ as it would be used in a very similar manner. All you need to remember though is when using a Proc use an ampersand.

Finally we will do a quick look into Lambdas. I like to think of Lambdas as anonymous functions much like you see in JavaScript but they are a bit more strict. Two things to know about Lambdas is you can return variables from them, something you can’t do in Procs but can in functions. Next, they are very strict about the number of arguments you pass in. Procs don’t care if you pass in more than you should have, but Lambdas will throw an error if the number of arguments are off.

`a = lambda do |x,y|  
puts x + y  
return x - y  
end.call(3,5)  
console output: 8  
a = -2`

So here we define a lambda by using the keyword lambda and giving it a block of code. To we told it to expect two variables and to output to the console and return a number to a variable. Note we had to chain the method .call to the end of the block to fire the method off. As well we passed in the variables in the call method. This would be because our lambda is not method association and we have no way to call the lambda after its defined so we had to call it after we ended its block of code.

As you should be able to see Lambdas are interesting but don’t have much of a place in most the code you will write.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates, live stream alerts, and post on my journey from Senior IT Admin to Junior Developer. Subscribe to the Program Practical channel on [YouTube](https://www.youtube.com/c/Programpracticaltv). Feel free to ask any questions in the comments below, and don’t forget it’s always a good time to start to #LearnToCode
