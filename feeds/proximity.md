---
title: Proximity Feed
description: 
published: true
date: 2020-02-24T04:48:01.023Z
tags: 
editor: markdown
dateCreated: 2020-02-24T03:44:31.838Z
---

# Overview
![pwatch_utility.png](/insightimages/pwatch_utility.png){.align-right}

Proximity feeds track all ship activity within a set gate distance range of systems. The feed can track by system proximity or constellation/region activity. Multiple systems, constellations, and regions can be added to a proximity watch. Proximity feeds are capable of mentioning ```@here``` or ```@everyone``` if desired.

# Configuration Settings
These options are available after feed creation using the ```!settings``` command. Some of these options are defined on initial feed creation but can be changed later.

## Add a new system, constellation, or region watch
- Prompts for a name and returns a list of matched systems, constellations, or regions for the user to choose from.
	- If a system is selected, Insight will prompt for a gate range. Kills that happen within the set number of jumps from the selected system will be posted.
  - If a constellation or region is selected, all kills within the selection will be posted.
  > To track kills only in a specific system, select ```0``` as the gate range.
- If multiple systems are added, Insight will post the killmail if it falls within range of at least one of the systems.
- Re-adding a previously added system allows you to modify the gate range.

## Remove a system, constellation, or region watch
- Remove a previously added watch.  

## Set maximum killmail age
Set the maximum delay for killmails. Fetched mails occurring more than the set minutes ago will be ignored.

## Manage feed sync settings
Set up and manage EVE contact syncing to blacklist allies from appearing as targets.  

## Set overall mention mode
Select the mention mode for any killmail posted to this feed. Insight can notify ```@here``` or ```@everyone```. This prompt allows users to disable channel notifications if desired.

## Set mention rate
If [Set overall mention mode](#set-overall-mention-mode) is set to ```@here``` or ```@everyone``` this parameter sets the delay, in minutes, between subsequent mentions.

## Change visual appearance
Change the appearance. See [appearance gallery](/appearances/proximity) for more information.

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

