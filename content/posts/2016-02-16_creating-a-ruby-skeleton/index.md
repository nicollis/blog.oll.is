---
title: "Creating a Ruby Skeleton"
author: "Nic Ollis"
date: 2016-02-16T16:20:09.000Z
lastmod: 2023-01-19T07:11:52-06:00

description: ""

subtitle: ""

image: "/posts/2016-02-16_creating-a-ruby-skeleton/images/1.png" 
images:
 - "/posts/2016-02-16_creating-a-ruby-skeleton/images/1.png"


aliases:
    - "/creating-a-ruby-skeleton-9d68bb45d3c8"

---

![powershell](http://programpractical.com/wp-content/uploads/2016/02/powershell.png)


A nice thing to have in your Ruby journey will be a skeleton project so you can quickly get up and running when you need to create a new project. For this we will be setting up in a windows environment using Powershell and Visual Studio’s Code callabled by “code”.

First we will create our skeleton project folder and its sub folders.
`mkdir skeleton``cd skeleton``mkdir bin, data, doc, ext, lib, tests, lib/PROJECT`

Now with our folder structure of project in place we will just need to create the template files. In Powershell the commands are:
`new-item -type file bin/PROJECT``new-item -type file lib/PROJECT.rb`

This will create an places we can start putting our new projects code. Next we will want to make a simple gemspec file that will hold the details of our project. We will name this PROJECT.gemspec and it will be located in our root project directory.
`new-item -type file PROJECT.gemspec``code ./PROJECT.gemspec`

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
`new-item -type file Rakefile``code ./Rakefile`

Rakefile file contents:
`require &#39;rake/testtask&#39;``Rake::TestTask.new do |t|``t.libs &lt;&lt; &#34;tests&#34;``t.test_files = FileList[&#39;test/test*.rb&#39;]``t.verbose = true``end`

Finally we will want to make a simple test file to finish up our skeleton project
`new-item -type file tests/test_PROJECT.rb``code ./tests/test_PROJECT.rb`

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

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates and post on my journey from Senior IT Admin to Junior Developer. Feel free to ask any questions in the comments below.
