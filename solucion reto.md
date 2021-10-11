# URI-reto-soluci-n-de-problemas1
complex 1
2611
SELECT id,name 
FROM Movies 
WHERE id_genres = (SELECT id 
		   FROM Genres 
		   WHERE description = 'Action'
		  )

2615
SELECT distinct city 
FROM customers 

2622
SELECT name 
FROM customers 
WHERE id IN (SELECT id_customers FROM legal_person)

2623
SELECT p.name, c.name
FROM products p INNER JOIN categories c ON
     p.id_categories = c.id
WHERE p.amount > 100 AND p.id_categories IN(1, 2, 3, 6, 9)

complex4
2988
SELECT 

(
    SELECT name 
    FROM teams t 
    WHERE t.id = team.id
) as name,


(
    SELECT count(team_1) 
    FROM matches 
    WHERE team_1 = team.id
)+(
    SELECT count(team_2) 
    FROM matches WHERE 
    team_2 = team.id
) as matches,


(
    SELECT sum(case when team_2_goals > team_1_goals then 1 else 0 END) as victories 
    FROM teams t INNER JOIN matches m ON t.id = m.team_2 
    WHERE t.id = team.id
)+(
    SELECT sum(case when team_1_goals > team_2_goals then 1 else 0 END) 
    FROM teams t INNER JOIN matches m ON t.id = m.team_1 
    WHERE t.id = team.id
) as victories,

(
    SELECT sum(case when team_2_goals < team_1_goals then 1 else 0 END) as victories 
    FROM teams t INNER JOIN matches m ON t.id = m.team_2 
    WHERE t.id = team.id
)+(
    SELECT sum(case when team_1_goals < team_2_goals then 1 else 0 END) 
    FROM teams t INNER JOIN matches m ON t.id = m.team_1 
    WHERE t.id = team.id
) as defeats,

(
    SELECT sum(case when team_2_goals = team_1_goals then 1 else 0 END) as victories 
    FROM teams t INNER JOIN matches m ON t.id = m.team_2 
    WHERE t.id = team.id
)+(
    SELECT sum(case when team_1_goals = team_2_goals then 1 else 0 END) 
    FROM teams t INNER JOIN matches m ON t.id = m.team_1 
    WHERE t.id = team.id
) as draws,


(
    SELECT sum(case when team_2_goals > team_1_goals then 3 when team_2_goals = team_1_goals then 1 else 0 END) as victories 
    FROM teams t INNER JOIN matches m ON t.id = m.team_2 
    WHERE t.id = team.id
)+(
    SELECT sum(case when team_1_goals > team_2_goals then 3 when team_1_goals = team_2_goals then 1 else 0 END) 
    FROM teams t INNER JOIN matches m ON t.id = m.team_1 
    WHERE t.id = team.id
) as score


FROM teams team
ORDER BY score DESC

2602
SELECT name
FROM customers
WHERE UPPER(state) = 'RS'

complex 5
2616
SELECT id, name
FROM customers c
WHERE NOT EXISTS (SELECT id_customers 
				  FROM locations l
				  WHERE c.id = l.id_customers)

2742
SELECT l.name, round((l.omega * 1.618), 3) AS "Fator N" 
FROM life_registry l JOIN dimensions d ON 
	 l.dimensions_id = d.id 
WHERE d.name in ('C875', 'C774') AND l.name LIKE 'Richard%'
ORDER BY l.omega ASC

complex 6
3001
SELECT name, CASE WHEN type = 'A' THEN 20.0 WHEN type = 'B' THEN 70.0 ELSE 530.5 END AS price
FROM products
ORDER BY price ASC, id DESC

complex 7
2991
