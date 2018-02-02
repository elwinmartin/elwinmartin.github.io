---
layout: post
title:  "Life Without (browsing) Facebook"
date:   2017-08-30 00:10:00 -0700
categories: project webdev web development 
---

I had a *great* idea earlier today. What if I could find a way to access the two features I use on Facebook: Events & Messenger (Okay, mayyybe Photos)... 

<!--more-->

but I didn't have to log in with a broswer and ever look at a feed or wall again?

## (Briefly) Joining Facebook for Developers

The first thing to do, naturally, was look at what APIs Facebook had publicly available. An account has to be verified to create an app, but I was willing to sacrifice my phone number for the cause. I dubbed my hopes and dreams "Test App" and got to work. It was just a few clicks to downloading the Android SDK and a few more to reading about the different ways that developers can interact with Facebook. The fundamentals are actually really cool. At it's core, Facebook is really just a gigantic graph.

No, really, I mean this literally. It's what they meant by "Graph Search" and why the main entry point to user/page content is the "Graph API". The data I wanted to access is associated with my user, so I got my user\_id from the /me/ end point (yes, really) and then queried /user\_id/ with my own user\_id.  The node 
that corresponds to any particular user includes edges to nodes for events, so there's route to anyone's events via /user\_id/events. So after a little bit of work, I was able to read my events (up to pagination) with this nice, simple single GET request. One line to cURL or test in the Graph API Explorer and I got back lovely JSON encoded data to play with. 

So far so good.

I started looking a little harder at the /events/ endpoint and near the start there is a note that app created events may be edited by the app. 
Great! A bit further down, however, there was a section titled "Creating" that simple stated 'You can't perform this operation on this endpoint.'

Huge let down.

Some minor sleuthing (aka Googling) brought me to a changelog that announced the deprecation of creation using the /events/ endpoint back in 2015. 
It seems like Facebook got a handle on their more important features and started locking them down as they sunset v1 of the Graph API. 

## Network Hacking Hero

My training and natural instincts had me wondering if there was any portion of the Graph API that surfaces when requests are made to create an event. 
Navigating to my home page, I opened up the Chrome inspection tool and tabbed over to Network data. This is a very, very useful feature for most 
traditional websites if you want to follow where data is going via traditional HTTP requests. I filled out the required form fields, toggled perserve log in the network tab, and pressed "Create Private Event". An avalanche of JS and various garbage tracking data flew into the console and I began skimming the xhr and doc typed entries.

Long story short, I think Facebook creates the event in the background in a slightly less trivial way ^^;...

I had one last ditch effort in mind which brings us to our next chapter!

## Selenium, our savior?

Disclaimer, as of the writing of this on 8-30 I haven't started the Selenium script yet since I don't even have it installed on my home machine.

I came across this solidly-not-bad article when I started looking for resources to automate browsing FB  https://intoli.com/blog/running-selenium-with-headless-chrome/ and I think that the most interesting solution would involve a combination of the reading capabilities of the Graph API with a catiously built Selenium script for posting new event information. This is probably a not an _easy_ thing for me to throw together, especially given my minimal experience with Android, but it would be worth a modest effort since I reducing my Facebook use could be good for my health.

Updates to come, maybe? I'm thinking this my route forward: https://stackoverflow.com/questions/101754/is-there-a-way-to-run-python-on-android

S E L E N I U M