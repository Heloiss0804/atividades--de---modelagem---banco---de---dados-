### Exercício 02

### Cria bancos de dados

```sql
CREATE DATABASE catalogo_de_filmes CHARACTER SET utf8mb4;
```

### CRIAR TABELA

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
   genero_id INT NOT NULL
);
```
