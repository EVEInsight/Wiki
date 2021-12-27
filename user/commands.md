---
title: Commands
description: An overview of commands.
published: true
date: 2021-01-25T00:19:05.136Z
tags: 
editor: markdown
dateCreated: 2020-02-24T01:19:54.223Z
---

# Command Overview
This page describes all available Insight commands and their functions. 

Insight commands are prefixed with either ```!``` or ```?```. Commands have no positional arguments so text prompts are used to provide options. When prompted for a choice, Insight will request the user to enter a number corresponding to an available option.

Commands are case-insensitive. If a user misspells or enters an invalid command, Insight will provide suggested, similar matched commands. If the user enters an unsupported command due to channel type, Insight will alert the user.

When in doubt, the only command you need to remember is ```!help```. The ```!help``` command points you to every possible command, feature, and modifiable option.

# Command Prefixing
A command prefix is the prefix character or phrase before a command. Example: For ```!about```, the prefix is ```!``` while the command is ```about```. 
By default, Insight listens for the prefixes ```!``` or ```?```. Running a command with these prefixes will cause Insight to respond. The prefixes can be modifed and removed on a server scope. Prefixes removed or added through the ```!prefix``` command affect all channels on a Discord server.
> It is recommended to run the ```!prefix``` command to change Insight's listening prefixes to something unique that won't conflict with other bots. 
{.is-warning}

> Insight will always respond to **@Insight command** mentions. Example: **@Insight prefix** will run the prefix command to prevent lockout if all other prefix have been deleted.
{.is-success}



# Commands
## !about
Display Insight credits and support information.

## !admin
Access Insight's admin panel.

## !create
Prompts the user to select a feed type for creation in the channel. For a detailed description of feed types, see [feed service types](/feeds). This command may only be used in server text channels and is unsupported in direct messages and channels that already have a feed. Use the command ```!remove``` to replace a feed service with another.

## !help
Display all available commands for the channel or direct message. If a command is not listed here, then it is unsupported by the channel. Certain commands are only supported in specific feed types or empty channels(channels without a feed). When it doubt, run ```!help```.

## !limits
Display channel / server rate limits and usage stats. Added in [v1.6](/releases#v16) and corresponds with the [Insight limit system](/user/limits).

## !lock
Lock a feed from being modified by unprivileged users. Useful in large servers.

## !unlock
Unlock to allow any Discord user to modify settings.

## !prefix
Modify command prefix settings to avoid command conflicts with other Discord bots. This command allows a Discord server admin to add or remove prefixes on a server-global scope.

## !quit
Shut down the Insight process. Requires Insight admin config IDs to be set.

## !settings
Displays a dialog with all available options for a feed or direct message. This command displays all available modifiable options related to a feed and allows the user to select an option. If an option is not listed, the feed service does not support the option. Example of available options include:
* Start/stop a feed service 
* Delete a feed service
* Add/remove tracked entity 
* Modify tracked ship groups
* Modify mention modes

## !start
Shortcut command to resume the feed if it has been paused. This function is also accessible by ```!settings``` -> ```Start feed```. 

## !stop
Shortcut command to temporarily pause a feed. A paused feed will not display any new killmails or server messages of the day. Pauses persist during bot rebooting cycles. Killmails that occur while a feed is paused will not be posted when the feed is resumed. Also accessible by ```!settings``` -> ```Pause feed```. 

## !remove
Shortcut command to delete a feed in a given channel. All feed configuration settings are deleted for the channel. This command frees the channel for new feed availability. Also accessible by ```!settings``` -> ```Remove feed```. 

## !status
Display information about the currently running feed.

## !sync
Access the SSO token syncing dialog. Token syncing is a radar feed feature to sync ally contacts from EVE. Ally contacts are blacklisted from appearing as potential targets in radar feeds. The SSO token dialog has the following options and differing behavior in direct messages and feed services:
### Direct message !sync options
* Add new token
     * Prompts the user to access the SSO system and authenticate. Upon successful authentication the user will be redirected back to a callback landing page. The user must copy the callback URL from their browser and paste it into the conversation with Insight. Insight will verify and let the user select a subset of character, corporation, and alliance standings to associate with the new token.
          * You can have multiple tokens associated with a Discord user.
          * When given the option, select ```No``` to the entity type you don't want associated with a token. Ex: If you only want to associate alliance standings with a token make sure to answer ```No``` to syncing corporate and personal as the token will sync all 3 contact lists otherwise.
* Delete token
     * Displays all tokens associated with the Discord user and prompts for a token selection to delete. Upon selecting a token to delete, Insight will delete it from the database and send a POST request to ESI to revoke the token.
* Remove a token from Discord channel
     * Lists the user's tokens and the channels/servers currently using them. Prompts the user to select a channel/server to remove their token from. Upon removal, the token will no longer sync contacts for the channel.  
* Force sync
     * Force an API pull of all user tokens. Insight automatically syncs tokens on an interval so this is unnecessary.
* View my tokens
     * View all SSO tokens for the user, number of contacts, and number of channels using the token.

### Discord text channel !sync options
Radar feeds can utilize a SSO token to pull standings from EVE and blacklist allies(blues) from appearing as potential targets.
* Add new token
     * Opens a direct conversation for security with the user and prompts for token selection. Insight will assign an SSO token to the channel upon successful selection. Multiple tokens can be added to sync multiple alliances, corps, 
     * Insight will merge conflicting contacts using the highest standing value to determine ally status. Example: 2 tokens have Alliance A as contact but with levels -10 and +5. Alliance A with standing +5 will be considered an ally and not an enemy by the feed.
     * Multiple tokens can be added per feed.
     * If a token is revoked, Insight will delete all contacts associated with the token for the channel.
     * Ensure Insight can direct message you. Insight opens a direct message with you for security for selecting a token.
* Remove token
     * Display all tokens synced with the channel and prompt for removal of a token. Upon selection, Insight will remove the token and all associated ally contacts from the feed's blacklist.
* Force sync
     * Updates the channel's ally blacklist. This option only updates the cached ally blacklist from contact tokens as it does not force an ESI pull. This task automatically runs in the background so it's unnecessary to run this command.
    * Force sync runs automatically every 1.5 hours. 
    * Insight will alert of changed token settings during automatic syncing:
         * Sync info dialog warning triggers:
              * A contact's standing level was modified, a contact was added, or a contact was deleted in-game.
              * One of the feed tokens was deleted, revoked, or became invalid.


# Utility Commands
## !8ball
Shakes the 8ball and selects a random response.

## !roll
Randomly roll a number between 0 and 100. Added in [v1.6](/releases#v16). Eventually this command will support arguments for setting the upper and lower number bounds.

## !scan
Added in [v1.6](/releases#v16). Perform a local scan. Copy and paste local pilots for a recent ship and affiliation overview.

## !time
Added in [v1.6](/releases#v16). Get the current EVE time. Subcommands provide an overview of various timezones.

