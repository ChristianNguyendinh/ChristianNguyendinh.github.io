---
layout: post
title:  "Git Squashing"
date:   2017-02-09 16:52:06 -0400
categories: uncategorized
---

Sometimes you are working on a dev branch and make a billion commits because you have no idea what you are doing and are too paranoid to leave any potential solution out of your history to revert back to.

But then you figure out the problem, people praise you as a deity on the code reviews, and all is right in the world. But unfortunately no one wants to see your trillion commits when they view the commit log.

<!--more-->

So, before merging, you probably want to get rid of those useless commits to clean up your history so you don't clog the main/production branch with your poorly written testing commit messages.

Turning multiple consecutive commits into one is called <strong>squashing</strong>. <span style="color: #ff0000;">You should not squash or edit history with branches / commits that you have already shared with others.</span>

The easiest way I find to squash is the following: say I want to squash the most recent 3 commits into one.

<img class="alignnone size-full wp-image-496" src="https://nineteenthbestfoxinbrookevillemd.files.wordpress.com/2017/02/initiallog.png" alt="initiallog" width="552" height="386" />

So, the top three commits are pretty useless on their own and contain minimal changes. So I want to squash them into one. I run the command:
<blockquote>git rebase -i HEAD~3</blockquote>
rebase is for reapplying commits

-i is flag for 'interactive'

HEAD~3 mean we want to edit the the first three commits away from where HEAD is currently at (including HEAD).

Now a similar document will open in your default text editor (usually vim)

<img class="alignnone size-full wp-image-504" src="https://nineteenthbestfoxinbrookevillemd.files.wordpress.com/2017/02/headrebase.png" alt="headrebase" width="722" height="436" />

You can see the first three commits from the current HEAD location, including their SHA1 and beginning commit messages.

Usually squash is done from top to bottom, so we are going to want to pick to keep the oldest commit (2979) and squash the other 2

<img class="alignnone size-full wp-image-510" src="https://nineteenthbestfoxinbrookevillemd.files.wordpress.com/2017/02/squash.png" alt="squash.png" width="432" height="56" />

Now save and exit, and another document will open where you can create a combined commit message for the three. Save and exit after you finish and you are done.<img class="alignnone size-full wp-image-513" src="https://nineteenthbestfoxinbrookevillemd.files.wordpress.com/2017/02/newlog.png" alt="newlog.png" width="455" height="283" />

The three commits have been successfully merged into one, and you have rewritten your commit history.

 

You can also do
<blockquote>git rebase -i <after-this-commit></blockquote>
This will let you squash or pick as many commits as you want AFTER the commit you choose. To choose a commit replace '<after-this-commit>' with the SHA1 of the commit you want. This may be more useful if you want to squash commits that you have not recently worked on.
