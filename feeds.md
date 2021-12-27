---
title: Feeds
description: An overview of the feed types available with Insight.
published: true
date: 2020-03-01T07:19:30.516Z
tags: feed, types
editor: markdown
dateCreated: 2020-02-24T02:48:39.371Z
---

# Feed Services
Insight provides live killmail feeds streamed from zKillboard. Feeds can be created in any Discord text channel through the ```!create``` command and can be fully customized using the ```!settings``` command. Each Discord text channel can have a maximum of 1 feed service. Feed services cannot be created in group conversations or direct messages.

Each feed's configuration is seperate from other feeds on the same server. Feeds can only be configured by users in the feed channel. Feeds can be locked from modification through the ```!lock``` and ```!unlock``` commands.

# Feed main categories
These are the main feed categories provided by Insight. Other feeds can derive features and similarities from these main feeds. See [preconfigured feeds](#preconfigured-feeds). Click a link to learn more.
> [Entity](/feeds/entity)

> [Radar](/feeds/radar)

> [Proximity](/feeds/proximity)

# Preconfigured Feeds
Preconfigured feeds are derived from [base/main feeds](#feed-main-categories) and offer a custom spin on features/settings. Preconfigured feeds often require no initial option setup and are mostly static/unchangeable. New preconfigured are added all the time!

## Super losses
* Derived from: Entity feed
* This feed exclusively displays titan or supercarrier losses.
* Available configuration modifications: None

## Capital losses
* Derived from: Entity feed
* Displays titan, supercarrier, carrier, dread, FAX, JF, and Rorqual losses. 
* Available configuration modifications: None

## Big Kills
* Derived from: Entity feed
* Displays expensive kills above a customized minimum ISK value.  
* Available configuration modifications: Minimum ISK value.

## Freighter Ganks
* Derived from: Entity feed
* This feed displays all freighters and jump freighters destroyed in high-security space.
* Available configuration modifications: None

## Excavator losses 
* Derived from: Entity feed
* This feed displays all excavator mining drone losses.
* Available configuration modifications: None

## Abyssal losses
* Derived from: Entity feed
* This feed displays all losses occurring in Abyssal space.
* Available configuration modifications: None

## Abyssal PvP
* Derived from: Entity feed
* Displays PvP losses in Abyssal space.
* Available configuration modifications: None

## Angry NPCs
* Derived from: Entity feed
* Displays pilot losses soloed by NPC ships.
* Available configuration modifications: Minimum ISK value.

## Alliance Tournament system stream
> Available only during the tournament
{.is-info}
* Derived from: Entity feed
* This feed displays all losses occurring in the region UUA-F4 for the alliance tournament.
* Available configuration modifications: None

## Officer Hunter
> This feed was a standalone feed at one point. The functionality of this feed was merged into the radar feed. Create a blank radar feed and then run ```!settings``` -> ```NPC Officer Tracking``` to enable this service.
{.is-warning}
* This feed displays universal officer activity when an npc officer is involved in a killmail.
* Available configuration modifications: All radar feed options.

## Alliance Tournament Ship Radar
> This feed was a standalone feed at one point. The functionality of this feed was merged into the radar feed. Create a blank radar feed and then run ```!settings``` -> ```Alliance Tournament ship tracking``` to enable this service.
{.is-warning}
* Displays universal alliance tournament ship activity regardless of system.
* Available configuration modifications: Synchronized standings through the ```!sync``` command.

## Universal supers
* Derived from: Capital radar
* Displays universal supercarrier/titan activity regardless of system or standings.
* Available configuration modifications: None
