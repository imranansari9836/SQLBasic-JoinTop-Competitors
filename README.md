SELECT H.hacker_id, H.name
FROM Submissions S
LeFT JOIN Challenges C ON S.challenge_id = C.challenge_id
LEFT JOIN Difficulty D ON C.difficulty_level = D.difficulty_level
LEFT JOIN Hackers H on S.hacker_id = H.hacker_id
WHERE D.score = S.score
GROUP BY H.name, H.hacker_id 
HAVING COUNT(H.name) > 1
ORDER BY COUNT(H.name) DESC, H.hacker_id ASC;
