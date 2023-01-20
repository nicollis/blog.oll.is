---
title: "Skeleton Ruby Project: Mac Edition"
author: "Nic Ollis"
date: 2016-05-23T16:00:05.000Z
lastmod: 2023-01-19T07:12:04-06:00

description: ""

subtitle: ""

image: "/posts/2016-05-23_skeleton-ruby-project-mac-edition/images/1.png" 
images:
 - "/posts/2016-05-23_skeleton-ruby-project-mac-edition/images/1.png"


aliases:
    - "/skeleton-ruby-project-mac-edition-1c62f401e469"

---

![Screen Shot 2016-05-22 at 3.21.58 PM](http://programpractical.com/wp-content/uploads/2016/05/Screen-Shot-2016-05-22-at-3.21.58-PM.png)


A nice thing to have in your Ruby journey will be a skeleton project so you can quickly get up and running when you need to create a new project. We have done this project in an earlier post for computers running Windows. However, with the upcoming video series on algorithmic challenges in Ruby I wanted to translate the old post for Mac systems. We will be doing all the commands in the terminal, and the Atom editor for writing to the files.

First we will create our skeleton project folder and its sub folders.
`mkdir skeleton``cd skeleton``mkdir bin data doc ext lib tests lib/PROJECT`

Now with our folder structure of project in place we will just need to create the template files. The commands are:
`touch bin/PROJECT``touch lib/PROJECT.rb`

This will create an places we can start putting our new projects code. Next we will want to make a simple gemspec file that will hold the details of our project. We will name this PROJECT.gemspec and it will be located in our root project directory.
`touch PROJECT.gemspec``atom ./PROJECT.gemspec`

PROJECT.gemspec file contents:
`# coding: utf-8  
lib = File.expand_path(&#39;../lib&#39;, __FILE__)  
$LOAD_PATH.unshift(lib) unless $LOAD_PATH.include?(lib)``Gem::Specification.new do |spec|  
  spec.name          = &#34;PROJECT&#34;  
  spec.version       = &#39;1.0&#39;  
  spec.authors       = [&#34;Your Name Here&#34;]  
  spec.email         = [&#34;youremail@yourdomain.com&#34;]  
  spec.summary       = %q{Short summary of your project}  
  spec.description   = %q{Longer description of your project.}  
  spec.homepage      = &#34;http://domainforproject.com/&#34;  
  spec.license       = &#34;MIT&#34;``spec.files         = [&#39;lib/PROJECT.rb&#39;]  
  spec.executables   = [&#39;bin/PROJECT&#39;]  
  spec.test_files    = [&#39;tests/test_PROJECT.rb&#39;]  
  spec.require_paths = [&#34;lib&#34;]  
end`

After the gemspec file is done we will want to create our Rakefile to help us with automating common task when working with Ruby. This Rakefile will be used to help run our test.
`touch Rakefile``atom ./Rakefile`

Rakefile file contents:
`require &#39;rake/testtask&#39;``Rake::TestTask.new do |t|``t.libs &lt;&lt; &#34;tests&#34;``t.test_files = FileList[&#39;test/test*.rb&#39;]``t.verbose = true``end`

Finally we will want to make a simple test file to finish up our skeleton project
`touch tests/test_PROJECT.rb``atom ./tests/test_PROJECT.rb`

test_PROJECT.rb contents:
`require &#34;./lib/PROJECT.rb&#34;``require &#34;test/unit&#34;``class TestName &lt; Test::Unit::TestCase``def test_sample``assert_equal(4, 2+2)``end``end`

Now we should have our test project all finished up. You can test your project by calling “rake test” from your project’s root directory. If setup correctly you should get a passed test without any failures or errors. Below is the file structure you should have now.
`skeleton/``PROJECT.gemspec``Rakefile``data/``ext/``tests/``test_NAME.rb``bin/``PROJECT``lib/``PROJECT``PROJECT.rb`

Now when you want to use this to creating a new project all you will need to do is the following.

*   Copy the skeleton project and rename the root folder to your new project name
*   Rename the lib/PROJECT.rb file and the lib/PROJECT folder to the new project name
*   Edit the Gemspec file to fit the new project
*   rename and tests/test_PROJECT.rb and make sure to edit the ‘require “./lib/PROJECT.rb”’ inside that test file
*   Double check everything is working by calling “rake tests”.
*   Happy Coding!

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates, live stream alerts, and post on my journey from Senior IT Admin to Junior Developer. Subscribe to the Program Practical channel on [YouTube](https://www.youtube.com/c/Programpracticaltv). Feel free to ask any questions in the comments below, and don’t forget it’s always a good time to start to #LearnToCode
