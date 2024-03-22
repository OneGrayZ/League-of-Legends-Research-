# League of Legends Research： First Blood and Win Rate
Final Project for DSC80 in UCSD

Names: Yihui Zhang
### Introduction
League of Legends is a multiplayer online battle arena video game developed and published by Riot Games in 2009. This game is very popular worldwide. The format of the game is simply two teams play against each other which each team has 5 players. There are 5 roles for each team which are top line, jungle, mid line, bot line, and support. 

I played League of Legends for years, the first blood kill is a big thing for the game because it will give player advatanges in the game. If the player knows how to use his advatanges from the first blood, it will help the team to win much easier. My favorite position is jungle, so I am very curious in which jungle champion gets the first blood will increase team's win rate in the all professional league games. Some coach or players either play in the professional league or play in daily rank will like to know that so they can pick the right champion to help them win.

My dataset is on all of the professional League of Legends games that have taken place in 2024. The dataset contains 12 rows per game, one row per player and 2 rows of summary statistics (one for each team). 

The columns I am interested in to answer, “Which jungle champion gets the first blood kill will increase team's win rate” are: **"result"**, **"position"**, **"champion"**, **"firstbloodkill"**. I chose these columns because they showed me the result of the match, and which champion gets the first blood kill, which position gets the first blood kill. When I cleaned our data to isolate the games where position jungle appeared, I had 640 rows, and 4 columns.
