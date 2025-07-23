Given a sql table of soccer matches results, write an SQL query to construct the league standings.  
 
So, from the input table: Table “Matches” 
 
| HomeTeam  | AwayTeam | HomeScore | AwayScore |
|-----------|----------|-----------|-----------|
| Argentina | Nigeria  | 2         | 0         |
| Germany   | Japan    | 1         | 1         |
| Japan     | Argentina| 0         | 1         |
| Germany   | Nigeria  | 2         | 3         |
| Nigeria   | Japan    | 0         | 0         |
| Germany   | Argentina| 1         | 0         |
 
Create the following table: Table “Ranking” 
 
| Team      | Scored | Received | GoalDiff | Points |
|-----------|--------|----------|----------|--------|
| Argentina | 3      | 1        | 2        | 6      |
| Germany   | 4      | 4        | 0        | 4      |
| Nigeria   | 3      | 4        | -1       | 4      |
| Japan     | 1      | 2        | -1       | 2      |
 
Pointing rules: 
•	Team gets 3 points for a win, 1 point for tie, 0 points for loss 
•	Team positions determined by number of points, if tied position is determined by the better “goal difference” meaning Goals Scored minus Goals received.  
