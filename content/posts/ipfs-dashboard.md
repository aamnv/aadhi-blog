---
title: "IPFS Dashboard"
date: 2020-08-18
summary: Metrics are fun.
tags: ["ipfs", "programming"]
slug: "ipfs-dashboard"
draft: true
---

I've spent much of August sitting around Hanover, NH and waiting for classes to start back up at Tuck. Although fun at first - boredom has taken over. That's why I decided to tackle a side project I've been eyeing for a while now: an [IPFS dashboard](http://ipfsdash.space/).

# What's IPFS?

[IPFS](https://ipfs.io/) is a p2p protocol & network that is actively developed by [Protocol Labs](https://protocol.ai/). In short - it is similar to what HTTP/S does for the web today. It gives users a way to address content based on the actual make-up of the content as opposed to an arbitrary address.

Said another way - think about google.com. What does that address really represent? It's a pointer to a server that hosts the web page files for Google's search engine. It isn't a reflection of the content of the web page itself. This means I could host the exact same web page content at a different address (say: google.app) and the web today would allow it.

In the world of IPFS, since the content of google.com and my hypothetical google.app is the same - they'd share the same address. This address is represented by a hash. This simple shift in addressing has two profound impacts downstream on user experience. For example:

- Users can trust content at a given hash is the same as when they first visited it (changes to content generate new hashes)
- Users can retrieve content from any other nearby user (called 'peer') who has it as opposed to a central server

As the second point alludes, there might be no central server hosting content on the IPFS network. Rather, peers would have either accessed the content recently or are 'pinning' (read: storing) the content locally to serve to other IPFS users looking to access the content. Caveat here being that there are pinning services available for folks who don't want to host their own content on the network, but still want to maintain persistence.

# Why IPFS Dashboard?

For quite some time I've wondered what the actual breadth of the IPFS network is. As a p2p network, there are certain metrics that would determine network health. Things like:

- Number of Unique Peers
- Number of Active Peers
- Uptime of Peers 
- Latency Amongst Peers

Luckily the [IPFS HTTP API](https://docs.ipfs.io/reference/http/api/) provides a way to query for most of these stats. 

Moreover, I've been looking for ways to extend my personal programming knowledge. I've spent a lot of time working on my back-end skills, but not much time on my front-end skills. This project would bring to the fore both skillsets and would be a great way to push the extent of my knowledge. On top of that - I'm mindful that I'll likely be trying to recruit into a tech firm in a product-related during my final year in my MBA program and this could be a good 'show-off' project.

Oh and I'm bored.

# Build Process

The build process started with some planning. I came up with three required functions to make this project work:

- Crawling the network for unique peers
- Pinging found peers for latency / uptime
- Live updating dashboard

As I put pen to paper, I came up with the following sketch of the high-level architecture:

![IPFS-Dashboard Architecture](/ipfs-dashboard/architecture_diagram.png) 

Let's walk through each component.

## Backend Server

In the backend server I run IPFS as well as the crawler & pinger modules. I wanted to separate the backend from the frontend to improve performance. IPFS is a memory & CPU hungry daemon process that would variably affect frontend load times, which seemed unacceptable to me in terms of UX. Moreover, I wanted the option to scale up my backend independently over time. 

For example - the pinger module can currently process 6,000 pings / day. That means once I find > 6,000 unique peers, it'll take > 1 day to ping all the peers for activity. This has some implications for metrics like active peers / day, since I'd need the ability to ping the entire universe of known peers in a day. Hence the need to scale up the backend.

Ultimately this backend server just ended up being a Raspberry Pi 3B+ that I had laying around. With 1GB RAM, it has just enough memory and decent enough CPU to support these operations. Obviously it won't be easy to scale it outside of its current specs, but it has enough space to 'grow' for the time being. If the project ends up getting any real traction, I'd likely migrate the backend to an AWS EC2 instance.

## Database

For a database I initially toyed with the idea of using something lightweight like SQlite. But the lack of concurrency and complications with deploying in production led me to the familiar PostgreSQL (PSQL) well. I used the AWS RDS service to host the database for simplicity.

The database contains two tables: `peers` & `uptime`. The `peers` table tracks unique peer IDs found by the crawler and the date they were found. The `uptime` table tracks the results (is node up + latency to node) of pings from the pinger module by unique peer ID and the date the ping occurred.

## Frontend Server

In terms of the frontend, I decided to use the [Dash library](https://dash.plotly.com/) to create a live updating dashboard. I'm most comfortable in Python and Dash + [Dash Bootstrap](https://dash-bootstrap-components.opensource.faculty.ai/) make it quite easy to develop a nice looking live-updating dashboard that is expressed in Python itself.

For hosting I went with [Heroku](https://www.heroku.com/home). Using the GitHub deployment method, I was able to link a git repo to my heroku dyno and the deployment process was and will continue to be relatively painless. As I push changes to my git repo, I can run `git push heroku master` and it's done!

# Final Result

So without further ado - I present my take on an [IPFS dashboard](http://ipfsdash.space/). The project came out much better than I expected it to and seems to be *mostly* done. I think I'd like to continue to monitor the data as it comes in and maybe add more interactivity to the dashboard (example: date ranges for the line graph) and perhaps improve page performance. But otherwise the project will be self-sustaining going forward. 

Or at least until I reach the limits on my PSQL database :)


