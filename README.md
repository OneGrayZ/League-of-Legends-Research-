# League of Legends Research： First Blood and Win Rate
Final Project for DSC80 in UCSD

Names: Yihui Zhang
## Introduction
League of Legends is a multiplayer online battle arena video game developed and published by Riot Games in 2009. This game is very popular worldwide. The format of the game is simply two teams play against each other which each team has 5 players. There are 5 roles for each team which are top line, jungle, mid line, bot line, and support. 

I played League of Legends for years, the first blood kill is a big thing for the game because it will give player advatanges in the game. If the player knows how to use his advatanges from the first blood, it will help the team to win much easier. My favorite position is jungle, so I am very curious in which jungle champion gets the first blood will increase team's win rate in the all professional league games. Some coaches or players either play in the professional league or play in daily rank will like to know that so they can have a better understanding of what condition they are in when the first blood kill happens.

My dataset is on all of the professional League of Legends games that have taken place in 2024. The dataset contains 12 rows per game, one row per player and 2 rows of summary statistics (one for each team). 

The columns I am interested in to answer, “Which jungle champion gets the first blood kill will increase team's win rate” are: **"result"**, **"position"**, **"champion"**, **"firstbloodkill"**. I chose these columns because they showed me the result of the match, and which champion gets the first blood kill, which position gets the first blood kill. When I cleaned our data to isolate the games where position jungle appeared, I had 640 rows, and 4 columns.
### Descriptions of Columns
- **position**: the position of game, top means top line, jng means jungle, mid means mid line, bot means bot line, and sup means support
- **champion**: the champion that the player picked 
- **result**: 0 means defeat, 1 means victory
- **firstbooldkill**: 0 means not got first blood kill, 1 means got first blood kill

## Data Cleaning
First of all, I only gets the columns that help to answer my question from the dataset which are **'position', 'champion', 'result',** and **'firstbloodkill'**. In the position columns, other than the 5 roles of the game which are top, jng, mid, bot, sup, there is another value called **'team'** which I do not want. In addition, because I only care about the position, so I only have **'jng'** in my position column. I also need to filter out the firstbloodkill column because I only care about the win rate when the champion got the first blood kill. I also realize that the **'result'** and **'firstbloodkill'** columns should be boolean values instead of integers, so I convert them to the right type. Then I check if there are any missing values now in each columns, and the output shows there is not empty cells in my dataset.

The head of cleaned data shows below: 

| Position | Champion  | Result | Firstbloodkill |
|----------|-----------|--------|----------------|
| jng      | Bel'Veth  | True   | True           |
| jng      | Jarvan IV | True   | True           |
| jng      | Nocturne  | True   | True           |
| jng      | Jarvan IV | True   | True           |
| jng      | Lee Sin   | True   | True           |

## EDA
### Univariate Analysis:
First, let's look at all jungle champions' win rate when by drawing graph. This pie graph shows that the win rate of all jungle champions when they get the firstblood. Based on this graph, when a jungle champion gets the first blood kill, the team will have almost **60%** to win.
<iframe
  src="assets/UA.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Bivariate Analysis:
Now let start exploring the question, "Which jungle champion gets the first blood kill will increase team's win rate". The first graph shows that the counts of each champion when gets the first blood kill and win the game. In this graph, the champion who gets the most win when has the first blood kill is **Xin Zhao**. The second graph shows that the win rate of each champion when gets the first blood. In this graph, there are some champions have the 100% win rate which means if they get the first blood in the game, they must win the game.
<iframe
  src="assets/BA1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
<iframe
  src="assets/BA2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Interesting Aggregates:
This *groupby()* shows 3 important values. The sum column describes the counts of getting the first blood and win the game for each champion. The count column describes the counts of getting the first blood in total for each champion. The mean column describes the win rate of each champion of getting the first blood and win the game. Now you might find out that the champion with the highest win rate such as 1 has low counts for getting the first blood. In addition, the champion with the lowest win rate such as 0 also has low counts for getting the first blood. 
| Champion        | Sum | Count | Mean      |
|-----------------|-----|-------|-----------|
| Amumu           | 0   | 1     | 0.000000  |
| Bel'Veth        | 8   | 12    | 0.666667  |
| Brand           | 12  | 18    | 0.666667  |
| Diana           | 0   | 2     | 0.000000  |
| Fiddlesticks    | 1   | 1     | 1.000000  |
| Gragas          | 2   | 4     | 0.500000  |
| Graves          | 7   | 11    | 0.636364  |
| Ivern           | 4   | 7     | 0.571429  |
| Jarvan IV       | 9   | 16    | 0.562500  |
| Jax             | 10  | 18    | 0.555556  |
| Kayn            | 1   | 1     | 1.000000  |
| Kindred         | 6   | 9     | 0.666667  |
| Lee Sin         | 52  | 72    | 0.722222  |
| Lillia          | 3   | 4     | 0.750000  |
| Maokai          | 27  | 36    | 0.750000  |
| Nidalee         | 1   | 3     | 0.333333  |
| Nocturne        | 27  | 43    | 0.627907  |
| Nunu & Willump  | 1   | 1     | 1.000000  |
| Poppy           | 20  | 33    | 0.606061  |
| Rell            | 19  | 34    | 0.558824  |
| Rengar          | 2   | 2     | 1.000000  |
| Sejuani         | 21  | 40    | 0.525000  |
| Taliyah         | 3   | 7     | 0.428571  |
| Trundle         | 5   | 10    | 0.500000  |
| Vi              | 45  | 80    | 0.562500  |
| Viego           | 28  | 55    | 0.509091  |
| Volibear        | 3   | 7     | 0.428571  |
| Wukong          | 7   | 12    | 0.583333  |
| Xin Zhao        | 56  | 100   | 0.560000  |
| Zac             | 1   | 1     | 1.000000  |

## Assessment of Missingness
