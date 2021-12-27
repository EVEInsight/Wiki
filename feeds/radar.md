---
title: Radar Feed
description: An overview of the radar feed type.
published: true
date: 2020-02-24T04:54:11.957Z
tags: 
editor: markdown
dateCreated: 2020-02-24T03:43:59.030Z
---

# Overview
![radar_utility.png](/insightimages/radar_utility.png){.align-right}
Radar feeds track hostile super, capital, blops, AT ship, or NPC officer activity within a set lightyear proximity of base systems. Radar feeds are ideal for tracking hostile incursions into friendly space, hunting expensive targets within jump range, or detecting capital escalations. Radar feeds feature an ally blacklist to ignore friendly capitals within your range while displaying hostile activity. Radar feeds are capable of mentioning ```@here``` or ```@everyone``` if desired.

# Configuration Settings
These options are available after feed creation using the ```!settings``` command. Some of these options are defined on initial feed creation but can be changed later.

## Add/modify a base system
- Prompts for a name and returns a list of matched systems for the user to choose from. Once selected, Insight will prompt for the lightyear radius integer to track from the system. 
- Only killmails that occur within the lightyear radius will be posted to the channel.  
- Multiple systems with varying lightyear ranges can be added to a single radar feed.
- If multiple base systems exist, Insight will post the killmail if it falls within range of at least one of the systems.
- Re-adding a previously added system allows you to modify the radius range.

## Remove a base system
Remove a selected base system from the feed.

## Ship type and group settings
Each option disables or enables tracking for a selected ship group or type. 
> The notification settings when adding tracking for a ship type or group are unique per selection added and can differ.
### Super tracking
Enable or disable the tracking of supercarrier and titan targets.

### Capital tracking
Enable or disable tracking of capital (dread, carrier, FAX, Rorqual) targets.

### BLOPS tracking
Enable or disable tracking of black ops battleship targets.

### Alliance Tournament ship tracking
Enable or disable tracking of AT ship targets.

### NPC Officer Tracking
Enable or disable tracking of NPC officer targets within range of base systems. Formerly the Officer Hunter preconfigured feed service.  

### Add custom attacker type
Add a custom attacking ship type or group track. Note: npc entities can be added as they are considered ships.  

### Remove tracked ship type/group 
Remove a previously added tracked ship/npc type or group. 
> This option removes individual items. If you wish to remove all supers you should instead select the super track option and then answer **disable**.

## Set maximum killmail age
Set the maximum delay for killmails. Fetched mails occurring more than the set minutes ago will be ignored.

## Manage feed sync settings
Set up and manage EVE contact syncing to blacklist allies from appearing as targets.  

## Set overall mention mode
Select the mention mode for any killmail posted to this feed. Insight can notify ```@here``` or ```@everyone```. This prompt allows users to disable channel notifications if desired.

## Set mention rate
If [Set overall mention mode](#set-overall-mention-mode) is set to ```@here``` or ```@everyone``` this parameter sets the delay, in minutes, between subsequent mentions.

## Change visual appearance
Change the appearance. See [appearance gallery](/appearances/radar) for more information.

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

# How radar filtering works
1. Insight receives a mail and determines the number of minutes ago it occurred. Ignore if delay exceeds the radar set max age.
2. Determine if the system is within the specified lightyear range of at least one of the base systems. Mail is ignored if it's not within range of any system.
3. Filter all attacking ship groups, applying a whitelist of tracked groups. Ignore mail if remainder count is equal to 0.
4. Insight takes the whitelisted attackers from step 3 and applies a blacklist of your allied contacts. Ignore mail if remainder count is equal to 0.
5. Determine attacker flying in the highest valued ship group from the remaining filtered attackers in step 4. This highest attacker and their ship type will make the visual embed.
6. Determine if Insight can mention then match the mention mode of the highest attacking ship group from step 5 with radar settings.
7. Enqueue visual mail for posting.

# Further Reading
> [Proximity Feeds](/feeds/proximity)
{.is-info}
