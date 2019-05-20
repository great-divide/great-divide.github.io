---
layout: post
title:      "Authenticate This"
date:       2019-05-20 03:58:07 +0000
permalink:  authenticate_this
---


Lately I've been revisiting an old React/Rails project. It's essentially a simple flashcard app. For the next upgrade, I want to use a spaced repetition algorithm to power the "flashcard engine" so that the user will learn what they most need to learn.

Naturally, in order to do this, the user needs a unique identity, so I need to whip up an authentication system. Since I had relatively easy success using OAuth2 gems for Google and Facebook logins for a couple of Rails and Sinatra projects, I figured that would be the simplest way to go with the React/Rails stack.

But I did not have an easy go with it at all! There was a lot of discussion regarding the relative merits and security of JWT tokens vs cookies and I am not opinionated in this regard. I picked a couple of gems recommended in a few blog posts and gave them a try, but I found that they were both deprecated and not making current updates. Couple this with the fact that I had decided to use Rails 6 "just for kicks"... and I was getting nowhere fast with Authentication.

My next attempt will be to use a SaaS Authentication provider. I like the idea of a package solution where i don't have to worry about gems becoming deprecated and I can count on a certain level of security without having to sweat the details. I'm going to try using Auth0 and see how it goes. Plus it's free up to 7,000 users, so for side projects and hobby sites like mine, why not?

Next post, I'll check in about my progress.
