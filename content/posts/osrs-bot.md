---
title: "OSRS Mining Bot"
date: 2020-12-11
summary: Playing a game from the 00s vicariously.
tags: ["programming", "python", "computer vision"]
slug: "osrs-mining-bot"
draft: false
---

I've had a bit more time on my hands recently. Most of the leg work I needed to finish to pursue a search fund is done. Classes are finished till January. Netflix has asked me if I'm still watching one too many times.

All that to say - I've been bored. So I decided to reconnect with my programming hobby. I wanted to pursue a project that taught me something new but still used the skills I've built learning Python. As I mindless browsed the internet, I came across an idea that was inspired by my past experience in gaming.

Back in the 2000s, I used to be OBSESSED with a game called [Runescape](https://en.wikipedia.org/wiki/RuneScape). The game continues to live - dare I say **thrive** - despite clearly looking like it was develeoped in the 00s as well. It is currently branded 'Old School Runescape' or [OSRS](https://en.wikipedia.org/wiki/Old_School_RuneScape).

The thing about Runescape is that it's a grind. You have 'skills' that are trained usually via repetitive tasks. Some can be enjoyable (at least for a while), while others are just straight horrid (shoutout to agility). That's why I thought it might be fun to automate one of these tasks using some basic screen scarping and computer vision via Python. Said another way: I decided to build a bot to mine in OSRS for me.

**NOTE: I built and trained my bot on a private server. OSRS does not condone botting on the public servers.**

# The Specs

For this project I wanted to build a bot that could do the following game loop:

- Detect iron ore
- Mine iron ore
- Empty inventory

I wanted to build this project entirely in Python and ultimately run it on my Raspberry Pi 3B. I'd also only use screen scraping and mouse / keyboard emulation instead of directly sending commands via existing botting APIs.

The resulting tech stack / modules used for the project:

- [Python 3.7](https://www.python.org/downloads/release/python-370/)
- [OpenCV 3.4.12](https://sourceforge.net/projects/opencvlibrary/files/3.4.12/)
- [PyAutoGUI](https://pyautogui.readthedocs.io/en/latest/index.html)
- [PIL / Pillow](https://pillow.readthedocs.io/en/stable/)

# The Loop

As mentioned above, the game loop has three distinct operations. Let's start with detecting the iron ore.

## Detect Iron Ore

To perform detection I used the Haar Cascade Classifier provided by OpenCV. For the model, I decided to focus on training for general ore detection. I figured I could use pixel coloration to do filtering by ore type on the back-end. The rationale for this was purely selfish: I didn't want to train like ~5 different ore models. :)

Training the model was relatively straightforward. I used a script to take screenshots of me at various mining locations in the game and collected about 200 of them. The negatives samples were collected in a similar manner, but with me running around in non-mining locations. Then I used the OpenCV annotations tool (only in V3) to draw bounding boxes around all the instances of ore. I trained the model with the following parameters:

- w 10 h 10
- positive samples: 450
- negative samples: 500

Combined with filters for the size of possible boxes on detection, this churned out a relatively strong ore detector that was also super easy to make!

In terms of figuring out if the ore was **iron**, I sampled the RGB colors of iron ore in the game. The beauty of OSRS is that there's significant similarity in models for things. This is especially so for ore that tend to have distinct coloration. Using this, I was able to add some logic to my script to check if the detected ores had the right pixel coloration. If so, it'd move on to mining. 

If not, then it's possible that the script didn't detect any ore around the bot that was compatible. So I added some logic to move the camera angle, so that perhaps iron ore would fall into the target screenshot region. This is a bit hacky admittedly, but worked pretty well.

## Mine Iron Ore

Mining the iron ore was straightforward with the PyAutoGUI library. It provides functions for moving and clicking the mouse along with parameters on pretty much any variable you'd want to manipulate. However, I wanted to design a bot that'd actually pass the 'sniff' test and feel almost human in its movements. To that end I incorporated significant randomness in:

- Time to move
- Number of clicks
- Interval inbetween clicks

The variables plugged into each of the above was based off of data I collected on how I personally mine. The result was pretty awesome to see. The bot moved almost human-like. I think a close inspection of the mouse movements would still alert folks that it's not human, but it'd definitely pass cursory analysis.

## Empty Inventory

Initially I was going to implement some detection to check when my character's inventory was full...but it seemed like overkill. The initial ore detection was so good that I almost never had a situation where I was ending up with inventories that were usually full after 28 iterations of the script (inventory was 28 slots). Given that, I just included a counter that would run an empty inventory function after 28 runs of the detect / mine loop.

# Outcomes

The outcome was pretty good. I've built a bot that clocks in ~21K experience per hour while mining iron ore. Benchmark for absolute highest experience rate here would be something in the 50K range. The 'cloaking' features also make me think that it'd stand the test of time (i.e. not get banned) if I ran it on the main OSRS servers.

Moreover, this is the first time I've ever played around with computer vision and I'm absolutely blown away by how painless it was. Open source technology has done wonders for the space and made it so simple that even a newbie like me can build valuable models from scratch.

I do think that in the future I'd like to tweak this bot to use even more powerful model types. Haar Cascade's are slightly outdated and it be interesting to use a more recent DNN like YOLO. But that may also be overkill for my usecase. Regardless, this project has definitely piqued my interest in automation via computer vision & AI/ML.
