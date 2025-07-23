--Table from the perspective of the Home Team 
WITH home AS ( 
SELECT  
  hometeam as Team, SUM(homescore) as scored, SUM(awayscore) AS received, 
  SUM( 
  CASE 
 	WHEN homescore > awayscore THEN 3 
 	when homescore = awayscore THEN 1 
  	ELSE 0 
  END 
  ) AS points 
FROM 
  Matches 
GROUP BY  
  hometeam 
), 
 
--Table from the perspective of the Away Team. In this case, AwayScore counts as goals scored instead of received. 
away as ( 
SELECT  
  awayteam as Team, SUM(awayscore) AS scored, SUM(homescore) AS received, 
  SUM( 
  CASE 
  	WHEN awayscore > homescore THEN 3 
  	when awayscore = homescore THEN 1 
  	ELSE 0 
  END 
  ) as points 
FROM 
  Matches 
GROUP BY  
  awayteam 
) 
 
SELECT  
    COALESCE(home.Team, away.Team) AS Team, 
    COALESCE(home.scored,0) + COALESCE(away.scored,0) AS Scored, 
    COALESCE(home.received,0) + COALESCE(away.received,0) AS Received, 
    (COALESCE(home.scored,0) + COALESCE(away.scored,0)) - (COALESCE(home.received,0) + COALESCE(away.received,0)) AS GoalDiff, 
    COALESCE(home.points,0) + COALESCE(away.points,0) AS Points 
FROM 
home 
FULL OUTER JOIN away ON home.Team = away.Team --Added full outer join in case a country in AwayTeam later appears in the dataset and it does not appear in HomeTeam 
ORDER BY Points DESC, GoalDiff DESC; 

