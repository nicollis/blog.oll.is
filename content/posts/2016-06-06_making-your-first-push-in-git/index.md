---
title: "Making your first push in git"
author: "Nic Ollis"
date: 2016-06-06T06:00:16.000Z
lastmod: 2023-01-19T07:12:06-06:00

description: ""

subtitle: ""




aliases:
    - "/making-your-first-push-in-git-cbb453d40018"

---

Making your first push to a project can be a daunting task if you are new to git. Today we are going to review how I do my checks before pushing and what you can do to avoid making mistakes prevalent to newbies.

For me my first step is always running a `git status`. I do this so I can get a quick list of files that have been added/modified/deleted. When I code I might put a `binding.pry` in a file I made no other edits to for troubleshooting and if I see the file in the list it&#39;s a good reminder to open the file and remove my changes.

Next we jump into a more detail view `git diff`, will show you all the changes git has registered. Review each line in detail. Make sure you don&#39;t have any commented out code that needs removed, or anything like `binding.pry` that needs removed. What you see in git diff is what will show on your pull request so make sure you won&#39;t be embarrassed by anything on it.

Now that we have all out changes staged and looking good I like to run `git add .` and `git commit -am &#34;&lt;message&gt;&#34;` the -a on git commit will make sure you remove any deleted files.

Don’t do your push just yet, we need to make sure nothing has changed on the master branch that could break our code. For this I take a multistep approach, although it could be narrowed down a bit to be more efficient. First I jump back to my local master branch `git checkout master` then I pull down the remote master `git pull`.

If changes were pulled down follow this next step otherwise jump to the next paragraph. I then jump back over to my working branch `git checkout nic/working-branch` and then run a `git merge master`. The merge will let you know of any conflicts, open any conflicted files and handle the issues as they come up. To leave the commit message screen that opens in vim by default hit `:wq` and enter on your keyboard. Now our run your test one more time to make sure no changes broke your code.

At this point we have all our changes committed locally and our branch is up to date with everything on the master branch. Next we just need to push the code up to the repository. Best practice it to push the code using your branch so project controllers can test your code easily. `git push origin nic/working-branch` will push our working branch up to the origin. From here we can log into github and build our pull request!

So to summarize with a quick list.

*   git status and git diff
*   git add . and git commit -am ‘message’
*   git checkout master and git pull
*   git checkout nic/working-branch and git merge (if needed)
*   git push origin nic/working-branch
*   login to github and make pull request

As always thanks for reading, and follow me on [twitter](https://twitter.com/nic_ollis) for more daily updates, live stream alerts, and post on my journey from Senior IT Admin to Junior Developer. Subscribe to the Program Practical channel on [YouTube](https://www.youtube.com/c/Programpracticaltv). Feel free to ask any questions in the comments below, and don’t forget it’s always a good time to start to #LearnToCode
