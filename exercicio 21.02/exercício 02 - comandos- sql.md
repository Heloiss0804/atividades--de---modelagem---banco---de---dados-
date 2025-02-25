### Exercício 02

### Cria bancos de dados

```sql
CREATE DATABASE catalogo_de_filmes CHARACTER SET utf8mb4;
```

### CRIAR TABELA Generos

```sql
CREATE TABLE generos (
   id INT NULL  PRIMARY KEY AUTO_INCREMENT,
   nome VARCHAR(45) NOT NULL

);
```
 
 ### Criar tabela filmes

```sql
 CREATE TABLE filmes (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   titulo VARCHAR (200) NOT NULL,
   lancamento DATE NOT NULL,
   genero_id INT NOT NULL
);
```
```sql
 CREATE TABLE filmes2 (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   titulo VARCHAR (200) NOT NULL,
   lancamento DATE NOT NULL,
   genero_id INT NOT NULL,
   CONSTRAINT fk_filmes2_generos FOREIGN kEY (genero_id) REFERENCES generos(id);

);
```
### Cria tabela Detalhes

```sql
 CREATE TABLE detalhes (
   id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
   duracao INT NOT NULL,
   sinopse TEXT(1000) NOT NULL,
   bilheteria DECIMAL(16,2)  NULL,
   orcamento DECIMAL(16,2) NULL,
   filme_id INT NOT NULL
);
```

### Criar relacionamento entre as tabelas e configurar a chave estrangeira

```sql
ALTER TABLE filmes
   ADD CONSTRAINT fk_filme_generos

    FOREIGN KEY (filme_id) REFERENCES generos(id);

```

```sql
ALTER TABLE detalhes
   ADD CONSTRAINT fk_detalhes_filmes

    FOREIGN KEY (filmes_id) REFERENCES filmes(id);

```
