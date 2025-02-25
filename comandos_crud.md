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