---
date: 2022-04-15 16:56:40
layout: post
title: DBATOOLS BLOG ONE
subtitle: First official blog on the dbatools PowerShell module
description: This blog site is all about dbatools and using it within PowerShell to try and make your life easier
image: /dbatools/assets/img/business.jpg
optimized_image: /dbatools/assets/img/business.jpg
category: Project
tags:
  - personal
  - projects
  - developement
  - dbatools
author: psdevuk
---

## Welcome

Thank you for taking the time to click the link and land on this blog page. Hopefully after reading this blog you will learn something new and feel totally awesome. Well maybe just the first bit, but maybe the second too, depending on how many times you have had to do this particular task.

To fill this out a bit I am just going to go on a little ramble on life and well what brought me to make this site. If you just want to skip to the actual problem and solution, just keep on scrolling.

So life has been pretty crazy for just about everybody, and that craziness rubbed off and I just stopped blogging on a site that I had been doing for a good few years. Having four daughters, three cats, two dogs keeps both myself and my Mrs very busy. Like today I had an awesome 2 hour walk with my family and dogs at the beach, time just flies when you having fun.  Feeling so blessed in life to have a family and being able to enjoy moments like today with them.

I recently started a new job which has re-ignited that drive I had when I was previously blogging. It just makes such a difference to my life, working with people who work as a team and are genuinely nice people. Like I got told about having team huddles every morning, and this was all new to me, but it just makes you feel involved in what your doing so much more. I am very happy working where I am, and being able to have the opportunity to use my PowerShell skills I have to automate various tasks or issues that might occur. It's been so awesome so far as I have got to explore modules I have not used before, or got the time to script the solution and host it on my on git repositories at work. I really do enjoy solving issues using code I wrote myself, or reading up on how someone else solved a similar or the same issue and re-use or adapt the code to fit your needs, but mostly writing my own solutions after inspiration arrives. As I find it better to write something yourself to understand the whole process line-by-line.

As mentioned in one team huddle there was an alert on an SQL job which had failed. So I was quick to volunteer to look into this alert, as I was hoping it would give me a good opportunity to finally explore the dbatools module which I had read the book on. Ultimately this kind of lead to this site being made. Ramble over.

> These blogs will show how I used PowerShell DBATools to find the problem, that I had been alerted about or brought to my attention to fix, and showing the underlying issue was found using dbatools


## SQL JOB FAILING

So my mission was to get to the bottom of this alert which had been automatically flagged on a particular server that a particular job had failed. Yes you may be thinking that's easy you remote onto the SQL server, open up SQL Server Management Studio, Expand the jobs and do it that way. The traditional tried and tested point and click way. Yes I could have gone this route, but as I believe this problem will eventually happen again given the fact there are a lot of SQL jobs running on lots of various servers, I could potentially see a lot of repetition happening. Where there is repetition to me it screams write me a script to do it automatically, this time, next time, and so on. As I believe computers should do the work 
that's why they were invented right?

![placeholder](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse3.mm.bing.net%2Fth%3Fid%3DOIP.Y-m-e4sZzAXRF8T4FzmUvgHaET%26pid%3DApi&f=1?raw=true "SQL Jobs")

What did I do? Well my first step was to get **dbatools** installed for me on my work machine, as I was feeling so pumped that I could do this all from the comfort of my own PowerShell session running on my computer. So I typed:-
```
Install-Module -Name dbatools -Scope CurrentUser
```
 I used this approach as unless I am running my PowerShell session as Administrator (which I wasn't at the time) you might get some red text polluting your screen. After installing the module was next to find the command and the syntax needed to look at this issue from the comfort of my own terminal window. So I then issued the following command:-

```
Find-DbaCommand "agentjob"
```

So from typing the above command saved me using my traditional approach which would of been something like:-

```
Get-Command -Module dbatools -Verb "Get" -Noun "*agentjob*"
```

 To me just using the top code seemed a lot less typing, and as some people say less is more. It was a awesome feature function for this module which I have mentioned previously. 
 From the list of commands returned, two looked very promising to me.  These were **Get-DbaAgentJob** and **Get-DbaAgentJobHistory** so using **help** on these commands with an **-examples** parameter helped me confirm these looked like the commands I needed to accomplish the job. 
 As also mentioned [there is a wealth of documentation for dbatools already here](https://docs.dbatools.io/) as I wanted to verify I was on the right tracks with using these commands. I then came up with the following:-

```
Get-DbaAgentJob -SqlInstance SQL_SERVER_INSTANCE -Job "JOB NAME HERE" |
Get-DbaAgentJobHistory | Format-Table -Wrap
```

So using the above command which was a one-liner in my terminal window managed to show me the listing of this job, and this particular job ran frequently so I was able to see that since it did fail, it had run successfully for the rest of the day, it only failed once, but was enough to trigger the alert. 

Although I was now armed with the information that the job was now running okay, to me it still didn't uncover why the job actually failed.

## Digging Deeper

So what caused this job to fail? Sadly I cannot reveal that information due to being a professional and not revealing server names or database tables, but if you are following along with this blog on a failed SQL job, then you should see in the message is where you will see the reason on why the job failed. 
 To me this is awesome just to be able to run commands from a shell terminal and get back the information you need, without opening remoting software, then finding the server, then opening SSMS then logging in, then expanding various menus to get to what you need to get to.
  It only takes one-line in Powershell to do all of the mentioned last paragraph. Saving time makes sense to me. 

## Credit where credit is due

I personally bought the meap copy of the [offical book](https://www.manning.com/books/learn-dbatools-in-a-month-of-lunches). This book I can personally recommend and I believe if you like the blog site or it's useful then buy yourself a copy of the book. Thank you.


## Conclusion

It was great to finally have a valid excuse to use this dbatools module. I was honeslty excited to use this, as from reading the book it just showed how much could be accomplished using this module. 