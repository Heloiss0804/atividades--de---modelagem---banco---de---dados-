## Exercício 04

### Sugestões

1. insira 4 generos: terror, suspense, fantasia e ação.
2. insira 3 filmes, contendo título,data de lançamenti (YYY-MM-DD) e o Gênero de acordo com a chave estrangeira.
3. Insira pelo menos 3 detalhes (ou seja, um para cada filme) contendo: duração, sinopse, bilheteria (opcional),orçamento(opcional) e o Filme ao qual o detalhe pertence de acordo com a chave estrangeira.

```sql
    INSERT INTO generos(nome) VALUES('Terror'),('Suspense'),('Fantasia'),('Ação');

    INSERT INTO filmes(titulo,lancamento,genero_id) 
    VALUES (
    'O massacre da serra elétrica',
    '1989-02-03',
    1
    );
    INSERT INTO filmes(titulo,lancamento,genero_id) 
    VALUES (
    'Ilha do Medo',
    '1995-05-10',
    2
    );
       INSERT INTO filmes(titulo,lancamento,genero_id) 
       VALUES (
    'Historia sem fim',
    '19885-06-03',
    3
    );

    
     
 
 


```