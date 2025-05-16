# Adabot

Adabot is a Node.js Discord bot that monitors a DayZ game server using the CFTools Cloud API and updates a Discord voice channel's name to display the server's current player count and status.

This bot is currently designed to monitor only a **single server**.

## Features

*   Connects to Discord using a bot token.
*   Polls a specified DayZ server via the CFTools API at regular intervals.
*   Updates a designated Discord voice channel name with the server's status (e.g., "ServerName: online/slots" or "ServerName: offline").
*   Displays the number of players in the queue, if any.
*   Sets a custom presence for the bot in Discord.

## Prerequisites

*   Node.js (v16.x or newer recommended)
*   A Discord Bot Token
*   CFTools API access (your server needs to be registered with CFTools Cloud)
*   The Channel ID of the Discord voice channel you want the bot to update.

## Setup

1.  **Clone the repository (or download the files):**

    For now, ensure you have `main.js`, `package.json`, `Dockerfile`, and the upcoming `config.json.sample` and `docker-compose.yml`.

2.  **Install Dependencies:**
    ```bash
    npm install
    ```

3.  **Configure the Bot:**
    *   Rename `config.json.sample` to `config.json`.
    *   Edit `config.json` with your specific details:
        *   `BOT_TOKEN`: Your Discord bot token.
        *   `PRESENCE_NAME`: The game/activity name you want the bot to display (e.g., "DayZ Server Status").
        *   `PRESENCE_TYPE`: The type of activity (e.g., "WATCHING", "PLAYING"). See Discord.js documentation for options.
        *   `POLLING_INTERVAL`: How often to check the server status, in seconds (e.g., 300 for 5 minutes).
        *   `SERVER.NAME`: A display name for your server.
        *   `SERVER.CHANNEL_ID`: The ID of the Discord voice channel to update.
        *   `SERVER.CFTOOLS_HOSTNAME`: The IP address or hostname of your DayZ server as registered in CFTools.
        *   `SERVER.CFTOOLS_PORT`: The game port of your DayZ server as registered in CFTools.

## Running the Bot

### Using Node.js

```bash
npm start
```
(This assumes you have `"start": "node main.js"` in your `package.json`'s `scripts` section. If not, use `node main.js`)


### Using Docker Compose

1.  Ensure you have `docker-compose.yml` in your project directory (this will be created next).
2.  Make sure your `config.json` is present and correctly configured.
3.  Run:
    ```bash
    docker compose up --build [-d]
    ```
    To stop:
    ```bash
    docker-compose down
    ```

## Files

*   `main.js`: The main application code for the bot.
*   `package.json`: Project metadata and dependencies.
*   `package-lock.json`: Records exact versions of dependencies.
*   `config.json`: Configuration file for bot token, server details, etc. (You create this from `config.json.sample`).
*   `config.json.sample`: An example configuration file.
*   `Dockerfile`: Instructions for building the Docker image.
*   `.gitignore`: Specifies intentionally untracked files that Git should ignore.
*   `docker-compose.yml`: Defines how to run the application using Docker Compose.
*   `README.md`: This file. 