SELECT company.name, SUBSTRING(users.email, (LOCATE('@', users.email))+1) AS `domen`, COUNT(*) AS `count of users` FROM company 
JOIN users ON company.id = users.company GROUP BY `domen`, company.name ORDER BY company.name
