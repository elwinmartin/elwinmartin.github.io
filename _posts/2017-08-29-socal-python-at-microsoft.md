---
layout: post
title:  "Socal Python @ Microsoft"
date:   2017-08-29 00:10:00 -0700
categories: python pythonic 
---

So this meeting was something I had been looking forward to since it was announced. The two talks today
were titled "I (can't stop killing my plants) oT" 
and "Python 3.5 - Arms weak, I/O's heavy,  save me async, threads are spaghetti".
I would be hard pressed to miss any talk with a 'Lose Yourself' reference and I was curious what sort
of practical things people are doing with IoT, outside of AC and light controllers.

The meeting opening was very inviting and there was a call for talks, even from less experienced members
which I greatly appreciate. I'm looking forward to tackling something messy or interesting enough to give
a talk when I have time.


## The IoT Talk:

The technologies involved were, roughly:

Sensors + Raspberry PI + Node + React + Cosmos DB

The speaker needed ADCs because RPI does not accept analog inputs; the ADC has a Python library 
which is part of the pythonic nature of the talk. They also made use of a protocol I'd never heard of:
MQTT. Their choice was based on it being lightweight and built on a publish / subscribe model.
They recommended it for use cases requiring low power, low bandwidth, and allowing for high latency.

Device twinning copies data in JSON to another place via the IOT cxn.

The She killed her plants in the process of developing the IoT system T_T I'm dead

Overall, the speaker was informative, thoroughm and super bubbly. Great talk. 

Insert link to github/jocchi here for the slides.

## ARMS SPAGHETTI TALK:

So I am still half-disappointed that the slides said "Concurrent Snakes for the Masses", but
it's a solid replacement for the dope title we were expecting.

Some of my notes as they came to me with light editing:

* DANK MEMES?!?

* `await` and `async` are the 'key' keywords here

* Sick Derrick's comedy reference.

* "So threading is a lightweight but naive approach...limited by number of threads and memory, race conditions and locks."

* "The internet is much slower than a CPU in most cases." 

* PEP 492?

* Make slideshow fonts large; specifically, they should be a decent chunk of the screen size.

* "Concurrency is explicit, this is good"

* Why are coroutines an array? How does the stream actually work?

* "it doesn't work because it's a demo"

* "My computer sepuku'd"

* Now we're launching an attack on Google from Microsoft's servers."

* Look into aiohttp sometime soon.

* This approach to concurrency is faster at larger numbers; threads are faster at lower async counts.

* Channels in Go are something I'm going to need to look into later.

------------
Some lines that demonstrate roughly how some of the examples looked in code:
```python
import asyncio

async def main():
    await print("thing?")

loop = asyncio.get_event_loop()
loop.run_until_complete
```

He mentioned a handful of issues for asyncio (parets need to be rewritten, it's often messy/complicated, requests not integrated well, etc.) 
but it seems that diving into this might not be straightforward.

Various technologies that came up in closing:
*uvloop
	rivals Node and Go
*pypy 3.5?
	JIT, gets fast after it warms up O:
	funded by Mozilla

Insert link to Sanic here: https://github.com/channelcat/sanic

