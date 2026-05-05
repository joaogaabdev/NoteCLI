
# Como um banco de dados é estruturado?

```postgresql
Database -> Tabelas -> registros.
```

Um banco de dados **relacional** se organiza por meio de tabelas, as quais contém registros e relacionamentos entre si.
Exemplo:

```postgresql
PostgreSQL:
			Table funcionarios:
			(...)
			
			Table vendas:
			(...)
			
			Table fornecedores:
```

Exemplo de tabela Usuários:

| Nome           | Nascimento | Sexo | País    |
| -------------- | ---------- | ---- | ------- |
| João Pedro     | 07/09/1991 | M    | Brasil  |
| Maria da Silva | 20/12/1997 | F    | Espanha |
| Cleber Duarte  | 08/07/1984 | M    | EUA     |
