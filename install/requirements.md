---
title: Requirements
description: 
published: true
date: 2020-03-02T03:57:37.856Z
tags: 
editor: markdown
dateCreated: 2020-02-23T08:01:36.125Z
---

# Server hardware requirements
## OS
Linux is recommended, but Insight will work on Windows. Official support for Windows is limited.
## CPU
Insight requires a **single CPU**. Due to the nature of Python and the asynchronous design of the software, Insight will never utilize more than one CPU core.
## RAM
At least **256MB of RAM** dedicated to Insight. More ram may be required to support other system resources depending on your environment.
## Storage
At least **2GB** of storage for the Insight database. Insight saves a history of all mails pulled and the storage will slowly increase over time. A SSD is recommended.
## Internet/Firewall 
> Only a single service under the same IP address may interact with the zKillboard API.
{.is-danger}

It is recommended to have at least **5Mbps** and a connection with reasonbally low ping. No inbound ports are required for Insight.

**NOTE:** Ensure Insight is the only service that interacts with zKillboard. Insight interacts with the zKillboard.com API service and will conflict with other services that make use of the zKillboard API under the same IP address. The zKillboard API will automatically ban your IP address if multiple services make a request to zKillboard originating from the same IP.

# Dependencies
## Python
- Python 3.6 (64 bit)
> Only python 3.6 is supported at this time. Python 3.7+ breaks some packages.
{.is-warning}
## Python Packages
Installable through pip and the included requirements.txt
- aiohttp
- configparser
- cryptography
- discord py
- GitPython
- janus
- networkx
- python-dateutil
- psutil
- Pympler
- requests
- SQLAlchemy
- SQLAlchemy-Utils
- swagger-client
- urllib3

# Third Party Applications
Insight requires the creation of a Discord and an EVE Online developer application. 
## Discord Application
> Required for posting mails.
{.is-success}

- See [Making a Discord application for use with Insight](/install/requirements/thirdpartydev#discord-developer)

## EVE Online Application
> Requires an Omega account
{.is-warning}

Insight will function without this, but contact streaming for use in radar and proximity feeds will be unavailable.

- See [Making an EVE Online application for use with Insight](/install/requirements/thirdpartydev#ccp-developer)

# Further reading and next steps
> [Installing Insight](/install)

> [Getting support](/insightsupport)