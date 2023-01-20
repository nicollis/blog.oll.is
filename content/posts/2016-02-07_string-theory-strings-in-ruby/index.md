---
title: "String Theory: Strings in Ruby"
author: "Nic Ollis"
date: 2016-02-07T10:30:36.000Z
lastmod: 2023-01-19T07:11:50-06:00

description: ""

subtitle: ""




aliases:
    - "/string-theory-strings-in-ruby-7377c5b8103"

---

Working with strings in Ruby has been interesting. As the  
re is far more to pay attention to and what you can do then when dealing with just JavaScript.

One of my favorite things is the ability to put a variable right in the middle of a string without having to first break out of it and then add it in.

#### JavaScript
> var my_var = “day”;  
> console.log(“Isn’t to”+my_var+” just lovely?”);

#### Ruby
> my_var = “day”  
> puts “Isn’t to#{my_var} just lovely?”

For me this is just a more clean and optimal way of writing code, we aren’t breaking out of the string to add a variable and it just looks cleaner. However, you have to be careful as not all quotes are created equal. Double quotes (“) tells Ruby to replace variables it finds with an #{}, but if you used just a single quote (‘) Ruby would leave the string alone and ignore any variables in it.
> my_var = “day”  
> puts “Isn’t to#{my_var} just lovely?”  
> _output:_ Isn’t today just lovely?> my_var = “day”  
> puts ‘Isn’t to#{my_var} just lovely?’  
> _output:_ Isn’t to#{my_var} just lovely?

As you can see we get quite a different results. Although this could be great for debugging as you can pass over the un-formatted string to the console for review.

Another great formatting option in Ruby is using %{} instead of the #{}. With %{} you get the ability to apply the same format to multiple values, which can be great for templementing.
> formatter = “Although its %{temp} I’m really enjoying the %{like}”  
> puts formatter % {temp : “cold”, like: “snow”}  
> puts formatter % {temp : “raining”, like: “thunder”}  
> _output:_ Although its cold I’m really enjoying the snow  
> _output:_ Although its raining I’m really enjoying the thunder

The last example I will show is something I really wish JavaScript could do although I really wish I could do the two things mentioned above in it. Using three double quotation marks in a row indicates a multiline string. While you can do these in JavaScript, Ruby once again just as a cleaner way of doing it as I don’t have to put (\) after the end of each line.

#### JavaScript
> var my_var = “ This \  
> is \  
> my \  
> stirng”;

#### Ruby
> my_var = “””  
> This  
> is  
> my  
> string  
> “””

While this might not be groundbreaking I love the cleanness and power Ruby provides to string control in its language. As well I hope if you are just getting into Ruby you have found something here helpful in you ability to control and manipulate strings.

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates and post on my journey from Senior IT Admin to Junior Developer.
