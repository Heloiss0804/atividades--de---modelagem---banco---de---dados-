# Comandos para operações CRUD no BANCO de DADOS

## Resumo

- **C**reate -> **INSERT**: inserir dados/registros na tabela
- **R**ead -> **SELECT**: consultar/ler dados/ registros na tabela
- **U**pdate -> **UPDATE**: atualiza dados/exclui dados/registros na tabela
- **D**elete -> **DELETE**: excluir dados/ registros na tabela

---

### Insert (Fabricantes)

```sql
  INSERT INTO fabricantes (nome) VALUES('Asus');
  INSERT INTO fabricantes (nome) VALUES('Dell');
  INSERT INTO fabricantes (nome) VALUES('Apple');

  INSERT INTO fabricantes (nome) VALUE('LG'),('Samsumg'),('Brastemp');
```

## Select (Fabricantes)

```sql
  SELECT * FROM fabricantes;
```

## Insert (Produtos)

```sql
   INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id)
 VALUES(
    'Ultrabook', 
    'Equipamento de ultima gereçãp cheio de recursos,e etc e tal...',
     3999.45,
     7,
     2 -- id do fabricante Dell

 );

   INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES(
    'Tablet Android',
    'Tablet com a versão 16 do sistema operacional Android, possui tela  de 10 polegadas e armazenamento de 128 GB. Estou sem ideias do que escrever aqui.',
    900,
    12,
    5 --Samsung
);

   INSERT INTO produtos(nome, descricao, preco, quantidade, fabricante_id)
VALUES ( 
    'Geladeira',
    'Refrigerador fros-free com acesso à Internet',
    5000,
    12,
    6 --Brastemp

), 
(
    'iphone 18 Pro Max Ferradão',
    'Smartphone Apple cheio de frescura e caro pra caramba...coisas de rico...',
    9666.66,
    3,
    3 --Apple
),
(
    'Ipad Mini',
    'Tablet Apple com tela retina display e bla bla bla e mó bunitinha',
    4999.12,
    5,
    3 --Apple
);
```

---

### Exercício 03

```sql
   INSERT INTO fabricantes (nome) VALUE('Positivo'),('Microsoft');

   INSERT INTO produtos (nome, preco, quantidade, , descricao, fabricante_id )
   VALUES (
    'Xbox Series S', 
    1997, 
    5,
   8,
   'velocidade e desempenho de ultima geração'
   ),
    (
    'Notebook Motion', 
    8, 
    1213.65,
   7,
   'Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas'
   );
```


----

## SELECT (Produtos)

```sql
-- Lendo TODAS as colunas de TODOS os registros
SELECT * FROM produtos;

-- Lendo somente nome e preço de todos os registros
SELECT nome, preco FROM produtos;
SELECT preco,nome FROM produtos;

-- Mostrar nome, preço e quantidade SOMENTE dos produtos que custam abaixo de 5000
SELECT nome, preco, quantidade FROM produtos
WHERE preco < 5000;

-- Mini Exercício: mostre o nome e descrição somente dos produtos da Apple
SELECT nome, descricao FROM produtos
WHERE fabricante_id = 3;

```

### Operadores Lógicos: E, OU, NÃO

#### E (AND)

```sql
-- Exibir nome e preço dos produtos que custam entre 2000 e 6000
SELECT nome, preco FROM produtos
WHERE preco >= 2000 AND preco <= 6000;

```

#### OU (OR)
```sql
--Mini-exercício: exibir nome, descrição dos produtos da Apple e da Samsung
SELECT nome, descricao FROM produtos
WHERE fabricante_id = 3 OR fabricante_id = 5;

--Versão usando a função SQL IN()
SELECT nome, descricao FROM produtos
WHERE fabricante_id IN(3, 5);
```

#### NÃO (NOT)
```sql
-- Nome,descrição e preço de todos os produtos EXCETO da Positivo
SELECT nome, descricao, preco from produtos
WHERE NOT fabricante_id = 7;

-- Versão usando operador relacional de "diferença/diferente"
SELECT nome, descricao, preco from produtos
WHERE fabricante_id != 7;
```

---

## UPDATE (Fabricantes)

**CUIDADO🚨**

**SEMPRE USE** a cláusula `WHERE` em seu comando `UPDATE` especificando uma ou mais condições para a atualização.

```sql
-- Trocar o nome do fabricante Asus do Brasil
UPDATE fabricantes SET nome = 'Asus do Brasil'
WHERE id = 1;

-- Mini-exericício: alterar a quantidade para 10 dos produtos que custam abaixo de 2000 exceto da Microsoft

UPDATE produtos SET quantidade = 10
WHERE preco <= 2000 AND fabricante_id != 8;

UPDATE produtos SET preco = 1213.65
WHERE id = 7;
```

## UPDATE (Fabricantes)

**CUIDADO🚨**

**SEMPRE USE** a cláusula `WHERE` em seu comando `DELETE` especificando uma ou mais condições para a atualização.

```sql
DELETE FROM fabricantes 
WHERE id = 4;
DELETE FROM fabricantes 
WHERE id = 1;

DELETE FROM produtos WHERE id = 4;

DELETE FROM fabricantes WHERE id = 3;

```


---

## SELECT : outras formas de uso

```sql
-- DESC: ordena em ordem decrescente
-- ASC: ordena em ordem crescente (padrão)
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

SELECT nome, preco,quantidade FROM produtos 
WHERE fabricante_id = 5 ORDER BY quantidade;

```
### Operações e funções de agregação

```sql
SELECT SUM(preco) FROM produtos;
SELECT SUM(preco) AS Total FROM produtos; -- alias /apelido pra coluna
SELECT SUM(preco) AS "Total dos preços dos produtos" FROM produtos;
SELECT nome AS Produto, preco as Preço FROM produtos;
SELECT nome Produto, preco as Preço FROM produtos; -- omitindo o AS

-- Funções de formatação/configuração: FORMAT e REPLACE
SELECT FORMAT (SUM(preco), 2) AS Total FROM produtos;
SELECT REPLACE (FORMAT (SUM(preco), 2), ",",".") AS Total FROM produtos;

-- Função de média: AVG
-- Função de arredondamento: ROUND
SELECT AVG(preco) AS "Média de Preços" FROM produtos;
SELECT ROUND(AVG(preco), 2) AS "Média de Preços" FROM produtos;

-- Função de contagem : COUNT
SELECT COUNT(id) AS "Qtd de produtos" FROM produtos;
SELECT COUNT(DISTINCT fabricante_id) AS "Qtd mde Fabricantes com Produtos" FROM produtos;

-- Operações matemáticas
SELECT nome, preco, quantidade, (preco * quantidade) AS TOTAL
FROM produtos;

--Segmentação/Agrupamento de resultados
SELECT fabricante_id, SUM(preco) AS Total FROM produtos
GROUP BY fabricante_id;

```

## Consultas (QUERIES) em duas ou mais tabelas relacionadas (JUNÇÃO?JOIN)

### Exibir o nome do produto e  nome do fabricante do produto
```sql
-- SELECT nomeDATabela.nomeDaColuna, nomeDaTabela2.nomeDaColuna,
SELECT produtos.nome AS Produto, fabricantes.nome AS Fabricante

--JOIN permite JUNTAR as tabela no momento do SELECT
FROM produtos JOIN fabricantes


-- ON tabela1.chave_estrangeira = tabela2.chave_primaria
ON produtos.fabricante_id = fabricantes.id;

```

### Nome do produtom preço do produto, nome do fabricante ordenados pelo nome do produto e pelo preço

```sql
SELECT 
    produtos.nome AS Produto,
    produtos.preco AS Preço,
    fabricantes.nome AS Fabricante
FROM produtos INNER JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id
ORDER BY Produto ASC, Preço DESC;    
```
### Fabricante, Soma dos Preçoc, Quantidade de produtos POR Fabricantes

```sql
SELECT 
    fabricantes.nome AS Fabricante,
   SUM(produtos.preco) AS Total,
   COUNT(produtos.fabricante_id) AS "Qtd de Produtos"
FROM produtos RIGHT JOIN fabricantes
ON produtos.fabricante_id = fabricantes.id
GROUP BY Fabricante
ORDER BY Total;   
 
```

```sql
SELECT 
    filmes.titulo AS  Filme,
    generos.nome AS Genero,
    FROM filmes INNER JOIN generos
    ON filmes.genero_id = generos.id;

```


```sql
SELECT 
    filmes.titulo AS  Filme,
    detalhes.sinopse AS Detalhes,
    FROM filmes INNER JOIN detalhes
    ON detalhes.filmes_id = filmes.id;

```



```sql
 SELECT 
    filmes.titulo AS  Filme,
    generos.nome AS Genero,
    detalhes.sinopse AS detalhes
    FROM filmes
    JOIN generos ON filmes.genero_id = generos.id
    JOIN detalhes ON detalhes.filme_id = filmes.id;
```




















   