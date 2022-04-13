---
date: 2022-04-13 13:56:40
layout: post
title: DBATOOLS BLOG SITE
subtitle: New blogs dedicated to the mighty dbatools PowerShell module
description: This blog site is all about dbatools and using it within PowerShell to try and make your life easier
image: /dbatools/assets/img/post1.png
optimized_image: /dbatools/assets/img/post1.jpg
category: Project
tags:
  - personal
  - projects
  - developement
  - dbatools
author: psdevuk
---

## Why make this site?

Well in a past job, in a galaxy not too far away. I was doing a fair amount of SQL work, and I read about this PowerShell module **dbatools** that had recently been published. Not much later a book was being written and I do enjoy a good technical book for my bed-time stories. So I decided to purchase the **MEAP** copy of **Learn DBATools in a month of lunches**
 Sadly I had to find myself a new job, and there wasn't much SQL going on in my daily activities, so although I had started reading the book, it was kind of just put to one side.
  Fast-forward to the present day and I am now working with hundreds of SQL servers. So I thought I need to get reading this book again! I have recently tweeted a few times how this module has saved my bacon (pun intended) to get me answers that would have taken longer to solve or get that information manually. As always I give thanks where thanks is due, and then the very talented Chrissy Le Maire co author of the book and module said she thought writing a blog on this would be a good idea.  So here I am following through on that tweet and making the site a reality.

> These blogs will show how I used PowerShell DBATools to find the problem, that I had been alerted about or brought to my attention, within the new totally awesome organisation I work for now.


## Hero in a half shell...

![placeholder](https://psdevuk.github.io/adam-blog/assets/img/halfshell.jpg "Original Shell Heroes")
Okay I am clearly getting distracted already, thinking back to my days as a kid way before PowerShell was about and the only shell heroes back in the day were the TMNT. Fast-Forward many years later and it still seems to me that other people do not want to become shell heroes or are happy with the point and click method they have always used. Don't get me wrong there is nothing wrong with that, although it will take longer, and you will most likely repeat that task some-time in the near future, and if you are really unlucky you might even get a repetative strain injury. Now I am not associating PowerShell with TMNT as in I don't go to work with a pair of nunchucks or samurai sword, but I do want to be that hero who is using a shell aka PowerShell to defeat the evils of computer problems aka Shredder, Rocksteady & Bebob...Can you see where I am going with this? Although I am not employed as a PowerShell developer, I see things that could be scripted, even if it's not a difficult task. Why? Because I believe computers were designed to do the brunt of the work, let the computer do the crunching, make your script into a function so you can dynamically change the parameters, make those functions into a module and share with colleagues or github. It's like the circle of life right there, I just think more people could be working smarter and not harder.

## Learning New Commands

As with everything in life, if you decide to open your mind and let this module in, it will involve learning new commands. So this obviously goes without saying, but some people don't like change. However to help you with finding the new commands you can go with the traditional approach I use:-
```
Get-Command -Module dbatools
```
or
```
Get-Command -Module dbatools -verb Get -Noun *something*
```
Well folks this time the developers of this module thought about that and wrote this [super nifty command to find commands](https://docs.dbatools.io/Find-DbaCommand) so [massive thanks going out to the dbatools crew](https://dbatools.io/team/) for dealing with the big issue of using a new module, discovering what is available. Not only that, but the team have put together [a totally awesome site for documentation](https://docs.dbatools.io/) plus there is a book, please see below for more details
![dbatools blog preview](/assets/img/dbatools-logo-1.png)"Super cool module"

## Credit where credit is due

I personally bought the meap copy of the [offical book](https://www.manning.com/books/learn-dbatools-in-a-month-of-lunches). This book I can personally recommend and I believe if you like the blog site or it's useful then buy yourself a copy of the book. Thank you.


