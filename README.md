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
This *groupby()* shows 3 important values. The **'sum'** column describes the counts of getting the first blood and win the game for each champion. The **'count'** column describes the counts of getting the first blood in total for each champion. The **'mean'** column describes the win rate of each champion of getting the first blood and win the game. Now you might find out that the champion with the highest win rate such as 1 has low counts for getting the first blood. In addition, the champion with the lowest win rate such as 0 also has low counts for getting the first blood. 
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
### NMAR Analysis:
I do believe that there are many columns in my data are **Not Missing At Random (NMAR)**. In my data, since there are 10 players in each game, after every other 10 rows, there always are 2 rows which record the each team's data instead of indivdual player's data. Beacuse of this recording format, many columns have missing values in the rows of team. 

In my case, the data of **'firstbloodkill'** is missing under rows which recrod team data, I think this is **NMAR** because the **'firstbloodkill'** refers which champion and position gets the kill instead of the whole team, and there is another column that records which team gets the first blood. However, I realize there is a column called **'firstbloodassist'** which records which champion and position is involved in the first blood but not taking the kill. This columns is missing also under team rows, but there are some missingness under player rows as well. It is not **Missing by Design (MD)** because it cannot infer this column’s missingness exactly from anothers such as **'firstbloodkill'** column. 

### Missingness Dependency:
I observed that some of the games do not record the information of **'firstbloodassist'**, and based on this fact, I think the missingness of **'firstbloodassist'** is dependent on the **'league'** column. Therefore, I will use the total variation distance to determine whether it is **Missing at Random (MAR) or Missing Complete at Random (MCAR)**. 

| League | Assist Missing = False | Assist Missing = True |
|--------|------------------------|-----------------------|
| AL     | 0.019282               | 0.000000              |
| CBLOL  | 0.037493               | 0.000000              |
| CBLOLA | 0.032137               | 0.000000              |
| DCup   | 0.000000               | 0.044118              |
| EBL    | 0.027317               | 0.000000              |
| ESLOL  | 0.028923               | 0.000000              |
| GLL    | 0.025174               | 0.000000              |
| HC     | 0.008570               | 0.000000              |
| HM     | 0.026245               | 0.000000              |
| LCK    | 0.077665               | 0.000000              |
| LCKC   | 0.091055               | 0.000000              |
| LCO    | 0.038029               | 0.000000              |
| LCS    | 0.023567               | 0.000000              |
| LDL    | 0.000000               | 0.455882              |
| LEC    | 0.045528               | 0.000000              |
| LFL    | 0.042849               | 0.000000              |
| LFL2   | 0.008034               | 0.000000              |
| LIT    | 0.027317               | 0.000000              |
| LJL    | 0.039100               | 0.000000              |
| LLA    | 0.050884               | 0.000000              |
| LPL    | 0.000000               | 0.500000              |
| LPLOL  | 0.027317               | 0.000000              |
| LVP SL | 0.042314               | 0.000000              |
| NACL   | 0.049813               | 0.000000              |
| NEXO   | 0.004285               | 0.000000              |
| NLC    | 0.029459               | 0.000000              |
| PCS    | 0.048741               | 0.000000              |
| PRM    | 0.045528               | 0.000000              |
| TCL    | 0.027852               | 0.000000              |
| UL     | 0.029459               | 0.000000              |
| VCS    | 0.046063               | 0.000000              |

<iframe
  src="assets/MD1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The observed statistic was: 1

The p-value was:0.0

The empirical distribution of the test statistic is the graph showed above.

Since the p-value was close to 0, the missingness of 'firstkillassist' depends on 'league' which is MAR.

Now let's check if there is any missing relationshiip between the **'side'** which is the game side (red or blue) of the game that the team picks and **'firstbloodassist'**. 

| Side | Assist Missing = False | Assist Missing = True |
|------|------------------------|-----------------------|
| Blue | 0.5                    | 0.5                   |
| Red  | 0.5                    | 0.5                   |

<iframe
  src="assets/MD2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The observed statistic was: 0

The p-value was: 1.0

The empirical distribution of the test statistic is the graph showed above.

Since the p-value was close to 1, the missingness of 'firstkillassist' not depends on 'league' which is MCAR.

## Hypothesis Testing
In this part, I will use the columns **'position', 'result'**, and **'firstbloodkill'** from the dataset.

**Null Hypothesis**: The win rate of the jungle position gets the firstbloodkill is the same as the win rate of the jungle position not gets the firstbloodkill.

**Alternate Hypothesis**: The win rate of the jungle position gets the firstbloodkill is different to the win rate of the jungle position not gets the firstbloodkill.

Test Statistic: I choose the difference between the jungle position gets the firstbloodkill and won and the jungle position not gets the firstbloodkill and won which is Total Variation Distance (TVD).

Significance Level: I choose 5% which is the most common significance level.

<iframe
  src="assets/HT.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Because the p-value is 1, I fail to reject the null hypothesis that the win rate of the jungle position gets the firstbloodkill is the same as the win rate of the jungle position not gets the firstbloodkill. This answers my questiion because it shows that the relationship between jungle gets the first blood kill and the result of team wnning is not very clear. The jungle gets the first blood might not impact the game result at all. 

## Framing a Prediction Problem
Based on the Hypothesis test, we might conclude that the benefits for jungle taking the first blood kill will not increase the team win rate by a lot. Then it leads to another interesting question. If jungle will not increase the team win rate by taking first blood kill, is there such a position increase the team win rate by taking the first blood? In other words, which position gets the first blood kill, the team is most likely to win the game. 

Therefore, now let's try predict if a team will win or lose a game when different position gets the first blood kill. I will do a multiclass classification since there are 5 different types of position. I will choose predict output of 'result' which indicates the result of the game because most people care about winning while they are playing. I will use accuracy to evaluate my model because the idea of this model is to tell people when a type of position gets the first blood, their team are likely to win or not. If the accuracy is the least thing that I care about, it will be no difference of guessing the result than predicting the result by running the model. I use regession model first. 
