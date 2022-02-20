# Wordle

The well known game of [wordle](https://www.nytimes.com/games/wordle/index.html), playable entirely in discord!  

## Version 1

### Instructions For Setup:  
- One by one, copy the `list__.gotmpl` CCs into a temporary custom command and run each **once**.  
- The setup is done when the last list CC is ran, and should output a message indicating so.  
- Lastly, add the [main CC](./v1/main.gotmpl), and any optional ones you wish!  

### Overview:  
- Main       : Allows you to play wordle!  
- Config     : Allows specified roles to edit the word list, change users' stats, and delete all the saved data.  
- Pagination : Enables pagination for the leaderboard (Note: to initialise pagination, you must manually react to any leaderboard message with one of the chosen emojis)!  

### Command Descriptions
The following subcommands should follow the `wordle` command group name, for example `-wordle play` assuming a server prefix of `-`
- `help`  - Displays a help message, listing each of the available commands  
- `play`  - Starts a game of wordle with a random word  
- `stop`  - Ends your current game  
- `lb`    - Shows a leaderboard of 10 users, based on win/loss ratio, with an optional page number  
- `stats` - Displays server wide statistics such as the number of games played, distribution, etc.  

The following subcommands should follow the `wcfg`/`wordleconfig` command group name, for example `-wcfg list all` assuming a server prefix of `-`
- `help`          - Displays a help message, listing each of the available commands  
- `list all`      - Outputs the entire word list in a file  
- `list add`      - Add a word/list of words to the word list -- This will only accept 5 letter words  
- `list rm`       - Remove a word/list of words from the word list -- This, again, only accepts 5 letter words  
- `list search`   - Search the word list for a word/list of words (returns true/false for each query)  
- `list grep`     - Search the word list with regex -- This command is highly prone to regex compilation errors, if you aren't familiar with regex see [this detailed explanation](https://www.regular-expressions.info/)  
- `user reset`    - Reset a target user's wordle stats (fully deletes this user's database entry)  
- `user wins set` - Set a users wins to a given number -- The same command can set a user's losses, replacing "wins" with "losses"  
- `user wins add` - Add a given number of wins to a user's stats -- Same condition applies as previous for setting losses  
- `user wins rem` - Remove a given number of wins from a user's stats -- Same condition applies as previous  
- `wipe save`     - Wipe all of the saved wordle data, specifically user data and serverwide stats, but preserve the word list  
- `wipe all data` - Delete absolutely all saved data, including everything mentioned above and the word list  

## Version 2

### Overview
This version is still in early development, see progress in the [version 2 directory](./v2)  
Note that this new system may not be fully compatible with the previous, I plan on making a single-use conversion CC to preserve past data  