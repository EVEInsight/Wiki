---
title: Insight Rate Limiting
description: Insight uses rate limits to provide service fairness and priority allocation.
published: true
date: 2020-04-14T05:58:28.315Z
tags: user, rate limits, slow
editor: markdown
dateCreated: 2020-04-14T05:09:30.530Z
---

# Insight rate limits
Insight makes use of rate limits to provide service fairness and was introduced with version [1.6](/releases). The rate limiter is designed to give equal utilization shares to all servers and channels that Insight is a member of. On the public managed bot the ratios are configured to provide each server about 3 feeds of reasonably active streaming. Servers with a large number of feeds with extreme activity and spamming in each will notice significant slowdowns from Insight's posting and response ability in the server.

Rate limits are equally configured for all categories (user, channel, server). Higher rate limits cannot be configured on a per-server basis to give some servers a higher limit. Increasing the rate limits increases it equally for all servers or channels that Insight is a member of.

If you find your server consistently at a 100% utilization ratio of tickets through the ```!limits``` command, please consider reducing the number of feeds or [hosting Insight yourself](/install).

# How Rate Limits Work
## Overview
Insight allocates a set number of tickets for every Discord user, channel, and server. When Insight sends any message through either a command response or a killmail posting then a ticket is consumed. When all allocated tickets are used, Insight will wait for more tickets to be available before posting additional messages or replying to a command. 

Consumed tickets become available after a defined cooldown period in seconds has passed. Allocation amounts are globally defined on a per-server basis and there is no way to give certain channels or servers additional ticket allocations at this time.

## Chaining
Rate limits work in a hierarchy of other rate limiters starting from the lowest level (channel or user) up to the highest level (global). 

Let's walk through an example. A Discord server has multiple feeds running in different channels. Insight attempts to post a message in a particular channel and first obtains a ticket. Once a channel ticket is consumed the channel limiter requests that the server limiter consume a ticket on its behalf. Once the server limiter consumes a ticket the server limiter will then request that its parent limiter (the Global limiter) consumes a ticket on its behalf. The global limiter consumes a ticket on the server's behalf and at this point there are no higher limiters above the global limiter so the message is posted.

### Rate limit chain for Discord channels
| Limiter | Level |
|---|---|
| Channel | Lowest level of hierarchy. |
| Server | Controls all channel limiters below it and consumes its tickets for channels that are using a lower ratio of tickets. |
| Global | Highest level of limiter that controls priorities for all servers and DMs Insight is a member of. |


### Rate limit chain for Discord private messages
| Limiter | Level |
|---|---|
| User | Lowest level of hierarchy. User is allocated a maximum number of messages per interval. |
| Global DM | Limiter for all private messages Insight is participating in. |
| Global | Highest level of limiter that controls priorities for all servers and DMs Insight is a member of. |

## Resource Prioritization
When a child limiter consumes a ticket and requests a parent limiter to consume a ticket on its behalf it sends the ratio of its current ticket utilization to the parent limiter. When the parent limiter has more requests for tickets than currently available tickets it will give priority to child limiters with a lower utilization ratio. Prioritization propagates at all levels of a ticket chain. Channels with less utilization will be given priority by a server limiter and servers will less consumed tickets will have a higher priority in the global scope.

Let's walk through an example. 
Two channel limiters, **A** and **B**, share a parent server limiter **C**. Server limiter **C** has no tickets available at the moment and channel limiter **A** requests a server ticket. Channel limiter **A** has utilized 95% of its channel tickets and tells server limiter **C** about this. Since no server tickets are available, **C** puts the request from **A** in its waiting queue. A few seconds later, channel limiter **B** sends a request to the server limiter requesting a ticket. Channel limiter **B** has not had many messages posted and its ticket utilization ration is 5%. A server ticket becomes free after a cooldown period so in this case, server limiter **C** will consume the ticket for channel limiter **B** as **B** is utilizing less of its own tickets despite being added to the queue after **A**.

# The !limits command
The ```!limits``` command shows your current usage ratio from the lowest / starting level up to the global scope. If you notice a service slowdown on a Discord server, check with ```!limits``` command to see how much utilization your server is consuming. If you are consistently at 100% tickets consumed, consider reducing the number of active feeds or [hosting Insight yourself](/install).

