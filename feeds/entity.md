---
title: Entity Feed
description: An overview of the entity feed type.
published: true
date: 2020-02-24T03:08:28.699Z
tags: 
editor: markdown
dateCreated: 2020-02-24T02:56:11.225Z
---

# Overview
![entity_k.png](/insightimages/entity_k.png){.align-right}

This feed displays PvP activity for a set of tracked entities. Entities are characters, corporations, or alliances. This feed type is ideal for personal, corporate, alliance, or coalition killboard streaming. Multiple entities can be added to the entity feed to track multiple pilots, or corps.

# Configuration Settings
These options are available after feed creation using the ```!settings``` command. Some of these options are defined on initial feed creation but can be changed later.

## Add a new tracked entity
Prompts to search for an entity by name. After searching, Insight will display a list of matched character, corporation, and alliance names to choose from. The user can search again or select an option to add as a tracked entity.

## Remove a tracked entity
Remove tracking of PvP activity for a previously added pilot, corp, or alliance. 

## Set kill/loss mode
Sets the feed to one of three modes based on the tracked entities.
* Shows kills only
* Show losses only 
* Show both kills and losses

## Display POD(capsule) mails
Sets the feed to either ignore or display POD mails.

## Set minimum ISK value
Set the minimum ISK value for killmails. If a killmail value involes selected entities and is below the ISK threshold set by this option the mail will not be posted.

## Set overall mention mode
Select the mention mode for any killmail posted to this feed. Insight can notify ```@here``` or ```@everyone```. This prompt allows users to disable channel notifications if desired.

## Set mention rate
If [Set overall mention mode](#set-overall-mention-mode) is set to ```@here``` or ```@everyone``` this parameter sets the delay, in minutes, between subsequent mentions.

## Change visual appearance
Change the appearance. See [appearance gallery](/appearances/entity) for more information.

## Start feed
Resume feed functions after being paused.

## Pause feed
Stop killmail posting in the channel. Note: while a channel is paused no mails will queue. When a feed is unpaused it will begin filtering and posting from that time. Mails pulled during the time the feed is paused will be lost.

## Delete feed
Delete the feed and the configuration for a channel.

## Lock feed
Lock a feed service from being modified by users without certain Discord channel roles. Requires channel privileged rights.

## Unlock feed
Unlock a previously locked feed service to allow any Discord channel user to modify settings. Requires channel privileged rights.

## Cancel
Cancel the settings command without making any changes.
