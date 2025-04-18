![Logo](admin/steam.png)

# ioBroker.steam

[![NPM version](https://img.shields.io/npm/v/iobroker.steam.svg)](https://www.npmjs.com/package/iobroker.steam)
[![Downloads](https://img.shields.io/npm/dm/iobroker.steam.svg)](https://www.npmjs.com/package/iobroker.steam)
![Number of Installations](https://iobroker.live/badges/steam-installed.svg)
![Current version in stable repository](https://iobroker.live/badges/steam-stable.svg)

[![NPM](https://nodei.co/npm/iobroker.steam.png?downloads=true)](https://nodei.co/npm/iobroker.steam/)

## ioBroker.steam

This adapter allows you to integrate information from the Steam API into your ioBroker system. 

## Features

*   **Steam Profile Information:**
    *   **Player Name:** Displays the current Steam name of the player.
    *   **Profile URL:** Provides the URL to the Steam profile.
    *   **Avatar URL:** Displays the URL to the player's avatar.
    *   **Player State:** Displays the current state of the player (e.g., Online, Ingame, Away).
    *   **Game Extra Info:** Displays information about the currently played game (if available).
    *   **Steam ID64:** The unique 64-bit Steam ID of the user.

*   **Game Monitoring:**
    *   **Games to Monitor:** Configure a list of games to monitor.
    *   **Game App ID:** Stores the Steam App ID for each monitored game.
    *   **Game News:** Fetches and updates the latest news for each monitored game every 6 hours (4 times a day).
    *   **Game Name Suggestions:** If a game cannot be found (e.g., due to a typo), the adapter logs a warning and suggests up to 5 similar game names from the Steam app list.
    *   **Auto-completion:** When adding games, the adapter automatically completes missing information - if you provide a game name, it finds the AppID, and vice versa.
    *   **Owned Games Import:** Imports all your owned games from your Steam library with a single click.
    *   **Enhanced Game Info:** Displays game icons, logos, community stats URLs, playtime statistics, and more.
    *   **Automatic Game Detection:** Automatically detects and creates states for games as they are played.

*   **Recently Played Games:**
    *   **Fetches recently played games** every 15 minutes (configurable in the code).
    *   **recentlyPlayed** is also updated immediately whenever the `currentGame` changes.
    *   **Playtime Statistics:** Tracks playtime for last 2 weeks and total playtime for each game.

*   **API Request Management:**
    *   **GetPlayerSummaries:** Requests player summaries at a configurable interval (minimum 15 seconds, default 60 seconds).
    *   **Daily Request Count:** Monitors the number of GetPlayerSummaries API requests to avoid exceeding the limit of 10,000 requests per day.
    *   **Automatic Reset:** Automatically resets the daily request count at 0:00 (midnight).
    *   **Optimized API Usage:** Prevents duplicate API calls and adds proper cooldowns between requests.
    *   **Steam AppList Caching:** Efficiently caches the Steam application list to reduce API calls.

## Configuration

1.  **Steam Name:** Enter your Steam username.
2.  **Steam API Key:** Enter your Steam API key. You can generate an API key [here](https://steamcommunity.com/dev/apikey).
3.  **Player summary interval:** Set how often to request player summaries (minimum 15 seconds).
4.  **Enable game suggestions:** Toggle whether similar game names should be suggested when a game can't be found.
5.  **Enable owned games:** Import all your owned games from Steam into your configuration (requires adapter restart).
6.  **Games to Monitor:** Add games to monitor. You can provide either the name or AppID - the adapter will automatically fill in the missing information.

## Usage

After installing and configuring the adapter, the Steam profile information, game news, recently played games, and API request statistics will be available as states in ioBroker.

The adapter creates several state folders:
- **steam.0** - Contains general profile information and connection status
- **steam.0.games** - Contains monitored games with their AppIDs, news, and statistics
- **steam.0.recentlyPlayed** - Contains information about recently played games

When a game is being played, its `isPlaying` state will be set to true, and all data for that game will be automatically updated.

## Changelog

### WORKING ON
* (bloop16) set IsPlaying in Game folder when currentGame and / or currentGameAppId is changing.

### 0.3.0 (2025-04-18)
* (bloop16)
    * Added auto-completion for game names and AppIDs
    * Added import of all owned games from Steam library
    * Enhanced game information with icons, logos, and community stats
    * Fixed adapter termination issues
    * Added automatic game detection when player starts playing
    * Optimized API usage with reduced duplicate calls
    * Added proper cooldowns between API requests
    * Added game image URLs and additional statistics
    * Fixed configuration issues with owned games

### 0.2.3 (2025-04-18)
* (bloop16)
    * Fix APIRequest

### 0.2.1 (2025-04-16)
* (bloop16)
    * Fix APIRequest

### 0.2.0 (2025-04-16)
* (bloop16)
    * Added function to suggest up to 5 similar game names if a game cannot be found (typo-tolerant search and warning in log).

### 0.1.2 (2025-04-15)
* (bloop16)
    * Added configurable interval for GetPlayerSummaries (min 15s, default 60s)
    * Added fetching and updating of game news every 6 hours (4x per day)
    * Added fetching of recently played games every 15 minutes
    * Improved API request management and daily request counter reset
    * Cleaned up code and improved error handling

### 0.0.3 (2025-04-13)
* (bloop16)  
    * fixed state directory

### 0.0.2 (2025-04-13)
* (bloop16) First working Version  
    * Steam profile information integration  
    * API request management with daily limits  
    * Automatic reset of request counter  
    * Secure API key storage

## License
MIT License

Copyright (c) 2025 bloop16 <bloop16@hotmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.