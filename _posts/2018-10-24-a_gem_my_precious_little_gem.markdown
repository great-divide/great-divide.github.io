---
layout: post
title:      "A gem! My precious little gem!"
date:       2018-10-24 22:54:46 +0000
permalink:  a_gem_my_precious_little_gem
---


This was an awesome project for getting my feet wet creating an app (micro-app?). I went about the whole thing completely backwards, really, and so I learned a LOT... I think.  Here's a few of them:
*      Watch Avi's walk-through video *first*
*      Object orientation is a *way of thinking*
*      A solid foundation means everything

By the time I had my first advisory meeting, where I was supposed to float my idea and discuss it with a technical advisor, I had pretty much written all my code. But since I didn't undersand how to organize it into multiple files, the whole thing was one file, one class.

It worked, but as the advisor told me, "This is cool but it's really just one big procedure. We want you to create objects that relate to one another, so think about which parts of your procedure have distinct functions, and make separate object classes out of them, storing your data in those objects rather than in one big 'return'."

Priceless advice. That's what I had been missing the entire time I was building it -- the whole *orientation to objects* part.

I think while I was plowing through the earlier exercises in the curriculum, I was solving the problems and completing the labs, but hadn't quite absorbed the *why* behind what I was learning about classes/objects/modules, etc.

This portfolio project was the perfect opportunity to both utilize the coding chops I've developed and really bring home the *consciousness* of object orientation that is at the heart of the whole system. Good stuff!

I did struggle with the file organization in the gem bundler for awhile... and then I realized that Avi went over *exactly that* in the walkthrough video. Doh! And in that video, he did everything in the reverse order that I did originally. He started with CLI logic (user-focused) and entered fake data to test functionality. Eventually, when that was working, he made the scraper for the data he wanted. 

I made my scraper first and then worked backwards to the CLI logic. This caused many problems for me, including the fact that testing every little change to my CLI logic required re-scraping the site... and so some changes took approximately 600 times longer than they should have. What's it called again? Oh yeah. Trial and ... *error*. Now I know.

Oh, my gem?  It's a nerdy little thing for a very specific function. It scrapes libraries on the Internet Archive for the full text of books in the public domain and then it searches those books for certain vocabulary words and extracts sentences that contain those words. Yay.
