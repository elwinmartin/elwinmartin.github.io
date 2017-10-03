---
layout: post
title:  "Socal Python @ Microsoft"
date:   2017-08-29 00:10:00 -0700
categories: python pythonic 
---

So this meeting is something I have been looking forward to since it was announced. The two talks today
are titled "I (can't stop killing my plants) oT" 
and "Python 3.5 - Arms weak, I/O's heavy,  save me async, threads are spaghetti".
I would be hard pressed to miss any talk with a Lose Yourself reference and I'm curious what sort
of practical things people are doing with IoT outside of AC and light controllers.

The meeting opening was very inviting and there was a call for talks, even from less experienced members
which I greatly appreciate. I'm looking forward to tackling something messy or interesting enough to give
a talk.

IoT Talk:
Sensors + Raspberry PI + Node + React + Cosmos DB?

Requires ADCs because RPI does not accept analog inputs; the ADC has a python library

Can you change gain per channel?

Azure IOT for python? MQTT - lightweight, publishes / subscribes [low power, low bandwidth, high latency]
Azure-Samples 

Device twinning copies data in JSON to another place via the IOT cxn.

She killed her plants in the process of developing the IoT system T_T I'm dead

Speaker was super bubbly and exciting, great talk. 

github/jocchi for the slides

ARMS SPAGHETTI TALK:

So I was about half disappointed that the actual slides said "Concurrent snakes for for the masses", but
it's a solid replacement for the dope title I was expecting.

Works at Riot, oh no.

DANK MEMES

await and async keywords

Did he just make a Derrick's comedy reference??

Threading, lightweight but naive approach...limited by number of threads and memory, race conditions and locks.

Internet much slower than CPU in most cases.

PEP 492?

Note to self; for slides, make font large [decent chunk of screen size].

Concurrency is explicit

Good for web servers, streams, reckless driving of HTTP???
^is this actually an issue?

import asyncio

async def main():
    print("thing)

print(main())

never awaits

async def main():
    await print("thing?")

loop = asyncio.get_event_loop()
loop.run_until_complete

coroutines comes in as an array? How do we do the stream?

------------
import aiohttp

"it doesn't work cus it's a demo"

"my computer sepuku'd"


"now we're launching an attack on Google from Microsoft's servers..."

concurrency slightly faster at larger numbers; threads are faster at lower async counts.

works well in production, supposedly ;)

Sanic looks like Flask..."gotta go fast"

15k request / second on a laptop

issues?
  need to be rewritten...
  asyncio needs simplification
  no good async request?
  what's an ORM? object relational manager?

uvloop?
	rivals Node and Go

pypy 3.5?
	JIT, gets fast after it warms up O:
	funded by Mozilla

https://github.com/channelcat/sanic

Channels in Go are dope