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



















   