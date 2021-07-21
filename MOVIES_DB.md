## SQL 3 - MOVIES DB

---

### Parte 1

**1) Explique o conceito de normalização e para que é usado.**

É um processo de modelar, padronizar e validar os dados e a forma como eles serão armazenados, visando eliminar ou ao menos minimizar a redundancia no banco de dados.

**2) Adicione um filme à tabela de filmes.**

insert into movies (created_at,updated_at,title,rating,awards,
release_date,length,genre_id) 
values ('1995-04-07', '2021-07-20','Bad Boys',10.0,2,'2009-08-04',119,4); 

**3) Adicione um gênero à tabela de gêneros.**

insert into genres (created_at, name, ranking, active) 
values ('2021-07-20', 'Crime', 13, 1);

**4) Associe o filme do Ex 2. ao gênero criado no Ex. 3.**

update movies set genre_id = 13 where id = 22;

**5) Modifique a tabela de atores para que pelo menos um ator adicione como favorito o filme adicionado no Ex. 2.**

update actors set favorite_movie_id = 22 where id = 4;

**6) Crie uma cópia temporária da tabela de filmes.**

CREATE TEMPORARY TABLE movies_temp 
SELECT * FROM movies;

**7) Elimine desta tabela temporária todos os filmes que ganharam menos de 5 prêmios**

DELETE FROM movies_temp where awards < 5;

**8) Obtenha a lista de todos os gêneros que possuem pelo menos um filme.**

SELECT DISTINCT g.* FROM genres g JOIN movies m on g.id = m.genre_id;

**9) Obtenha a lista de atores cujo filme favorito ganhou mais de 3 prêmios.**

SELECT DISTINCT a.* FROM actors a 
JOIN movies m 
on a.favorite_movie_id = m.id 
WHERE m.awards > 3;

**10) Use o plano de explicação para analisar a consulta no Ex. 7.**

EXPLAIN DELETE FROM movies_temp where awards < 5;

**11) O que são os índices? Para que servem?**

São uma referencia associada a uma chave, que é utilizada para otimizar e agilizar uma consulta.

**12) Crie um índice sobre o nome na tabela de filmes**

ALTER TABLE movies ADD INDEX (title);

**13) Verifique se o índice foi criado corretamente.**

SHOW INDEX FROM movies;

