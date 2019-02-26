---
layout: post
title:      "Reacting to React"
date:       2019-02-26 19:58:26 +0000
permalink:  reacting_to_react
---


Moving from Rails-based apps with a little JS functionality to a full-blown React frontend connected to a Rails API was a huge step for me in terms of complexity and project organization. In that way, it was a great assignment.

I decided to make a simple flashcard app for locating acupuncture points. Acupuncture points are organized by Channels to which they belong, so this led to a natural structure for both my db and my React frontend:
```
Channel has_many Points
Point belongs_to Channel

App
-- ChannelsContainer
---- PointsContainer
-------PointFront
-------PointBack
```

One unexpected challenge I faced was attaching an image to each Point, to be used for the back of each "flaschard", so I had to make my first foray into the world of ActiveStorage. It took me awhile to grok that I would be attaching a url of the image to my Point objects rather than attaching the image directly, but once I understood the basic structure, properly seeding my db was  a snap.

In future updates to the app, I may add the ability for the User to add their own custom image to the flashcard, which will afford me the opportunity to get acquainted with ActiveStorage's uploading protocols.

All in all, I've enjoyed working through the mental puzzle that is Redux/React, but i can't say I see an immediate need for it in the projects I'm currently working on. A couple of Ajax requests and a little JS script seem to work just fine for the immediate uses I have in mind. React seems a little overkill for the (admittedly quite basic) apps I'm kicking around the ole project garage. 

I do imagine it will come in handy when I make my first attempt at a mobile app using React Native -- that will be the next frontier in my continuing code education...
