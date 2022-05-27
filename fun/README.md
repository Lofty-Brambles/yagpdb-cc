# Fun

## Wordle

The well known game of [wordle](https://www.nytimes.com/games/wordle/index.html), playable entirely in discord!  

The only CCs required for gameplay is [main.gotmpl](./wordle/main.gotmpl) and the 3 word lists for first time setup.  

### Instructions For Setup:  
- Copy each word list, in order, into a temporary CC, then run it **once**!  
- The setup is done when the last list CC is ran, and should output a message indicating so.  
- Lastly, add the [main CC](./wordle/main.gotmpl), and either (or both) optional ones!  

### Overview:  
- Main CC: Allows you to play wordle!  
- Config CC: Allows specified roles to edit the word list, change users' stats, and delete all the saved data.  
- Pagination CC: Enables pagination for the leaderboard (Note: to initialise pagination, you must add one of the chosen reactions to a leaderboard message)!  

## Minesweeper

A simple, minimalistic minesweeper game with plenty of customisability.  
Choose your own custom minefield size, number of bombs, and more.  

Easy to understand user interface, simply type coordinates to dig or flag a tile!  
No setup is required, the game is fully playable out of the box.  

Credit to <https://github.com/kying18/minesweeper/blob/main/minesweeper.py>, this is largely based on this script!  
