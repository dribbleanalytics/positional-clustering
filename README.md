# METHODOLOGY: Defining NBA players by role with k-means clustering

[Link to blog post.](https://dribbleanalytics.blog/2019/04/positional-clustering)

## Data collection

First, I created a database of all players who played at least 50 games and 1,000 minutes as of the end of the 2018-19 regular season. This resulted a data set of 256 players.

The following stats were recorded for all these players:

|Shooting (raw)|Shooting (percentages)|Rebounding|Passing|Defense|Advanced efficiency stats|Other|
:--|:--|:--|:--|:--|:--|:--|
|FG|FG%|ORB|AST|STL|PER|POS*|
|FGA|3P%|DRB|TOV|BLK|OWS|USG%|
|3P|2P%|TRB|AST%|PF|DWS||
|3PA|eFG%|ORB%|TOV%|STL%|WS||
|2P|FT%|DRB%||BLK%|WS/48||
|2PA|TS%|TRB%||TOV%|OBPM||
|FT|3PAr||||DBPM||
|FTA|FTr||||BPM||
|PPG|||||VORP||


*POS = position as a number; 1 = guard, 2 = wing, 3 = big

All data was taken from [Basketball Reference](http://basketball-reference.com/).

## Dimensionality reduction

A principal components analysis with n_components = 6 was performed on the features. These 6 components explained 85.85% of the data set's variance.

n_components = 6 was used by examining the dy/dx between different n_components values and choosing the one with the biggest change.

## Clustering

By examining silhouette scores, we chose to use n_clusters = 12 for our k-means algorithm. The algorithm separated the data set into 12 groups (clsuters), each with a clear theme. We then labeled these groups with a role, thereby defining every NBA player into a set of roles.

The roles, example players, and average stats are below.

|Role|Notable players|PTS/REB/AST|STL/BLK|FG/3P/FT/USG|
:--|:--|:--|:--|:--|
|3&D forward|P.J. Tucker, OG Anunoby|7.5/4.4/1.3|0.7/0.5|46%/33%/74%/15%|
|3&D guard|Danny Green, Wesley Matthews|8.9/2.4/1.6|0.6/0.2|44%/39%/83%/16%|
|???|Collin Sexton, Josh Jackson|9.2/3.1/2.5|0.8/0.3|42%/32%/75%/19%|
|Do it all big|Al Horford, Paul Millsap|12.9/6.9/2.2|1/1.2|51%/37%/74%/19%|
|Floor general|Ricky Rubio, Kyle Lowry|11.2/4.2/5.3|1.3/0.4|44%/35%/78%/18%|
|Inside big|Julius Randle, LaMarcus Aldridge|17.3/9.3/2.4|0.7/0.9|56%/25%/75%/24%|
|Perimiter scorer|Tobias Harris, Jayson Tatum|14.7/5.9/2.1|0.8/0.5|46%/35%/77%/22%|
|Rim runner|Clint Capela, Jarrett Allen|9.6/7.5/1.3|0.7/1.2|61%/9%/65%/17%|
|Shooter|Klay Thompson, Buddy Hield|16.7/3.7/3.2|0.8/0.3|45%/38%/85%/23%|
|Star ball handler|James Harden, Damian Lillard|27.3/6.6/5.9|1.4/0.5|47%/38%/84%/31%|
|Star big|Giannis Antetokounmpo, Joel Embiid|21.9/12.2/5|1.3/1.5|53%/24%/73%/27%|
|Team-leading guard|Trae Young, Jrue Holiday|21.9/4.6/6.1|1.3/0.4|45%/34%/81%/29%|

Each player's roles can be viewed in an interactive table in the bottom of the blog post [here](https://dribbleanalytics.blog/2019/04/positional-clustering).
