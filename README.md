-- Exercício 1: Liste todos os livros vendidos e seus respectivos autores.

SELECT A.NOME AS AUTORES, 
       L.TITULO AS LIVROS_VENDIDOS  
FROM cap08.livros_vendidos LV
INNER JOIN cap08.autores A
ON LV.ID_AUTOR = A.ID_AUTOR
INNER JOIN cap08.livros L
ON LV.ID_LIVRO = L.ID_LIVRO
WHERE LV.ID_LIVRO IS NOT NULL
ORDER BY NOME

-- Exercício 2: Liste todos os autores e seus respectivos livros, incluindo autores que não têm livros cadastrados

SELECT CASE
   WHEN A.NOME IS NULL THEN 'Sem Autor' 
   ELSE A.NOME END AS NOME,
      CASE
	WHEN L.TITULO IS NULL THEN 'Não publicado'
   ELSE L.TITULO END AS VENDIDOS
FROM cap08.livros_vendidos LV
FULL JOIN cap08.autores A
ON LV.ID_AUTOR = A.ID_AUTOR
FULL JOIN cap08.livros L
ON LV.ID_LIVRO = L.ID_LIVRO
WHERE NOME != 'Sem Autor'
