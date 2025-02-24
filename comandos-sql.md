# Comandos SQL - Documentação

Neste arquivo está a referência de comandos visando a estruturação do banco de dados MySQL/MariaDB

### Criar banco de dados

```sql
 CREATE DATABASE vendas CHARACTER SET utf8mb4;
```

### Criar tabela de Fabricantes

```sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL
);
```

### Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
```

### Criar tabelas Produtos

```sql
## Isso também é comentario válido SQL
CREATE TABLE PRODUTOS (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   nome VARCHAR (45) NOT NULL,
   descricao TEXT(500) NULL,
   preco DECIMAL(6,2) NOT NULL,
   fabricante_id INT NOT NULL --será chave estrangeira

);
```

### Criar relacionamento entre as tabelas e configurar a chave estrangeira

```sql
-- Adicionando uma restrição indicando o nome do relacionamento
ALTER TABLE produtos
   ADD CONSTRAINT fk_produtos_fabricantes

   --Criando a chave-estrangeira (fabricantes_id) que 
   --aponta para chave primária (id) de OUTRA TABELA (fabricantes)
   FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);
```

### Exemplos de alterações estruturais em tabela

#### Adiciona coluna

```sql
ALTER TABLE produtos ADD quantidade INT NULL AFTER preco;
```

#### Renomear 

```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
ALTER TABLE fornecedores RENAME TO fabricantes;
```

#### Renomear coluna

```sql
ALTER TABLE produtos CHANGE descricao detalhes TEXT(500)NULL;
ALTER TABLE produtos CHANGE detalhes descricao TEXT(500)NULL;
```













