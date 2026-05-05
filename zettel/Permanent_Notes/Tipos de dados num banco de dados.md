## Tipos de dados no **PostgreSQL**:

| Categoria         | Tipo               | Descrição                                                      | Exemplo                                          |
| ----------------- | ------------------ | -------------------------------------------------------------- | ------------------------------------------------ |
| Inteiros          | `SMALLINT`         | Inteiro pequeno (2 bytes)                                      | 120                                              |
|                   | `INTEGER` ou `INT` | Inteiro padrão (4 bytes)                                       | 5000                                             |
|                   | `BIGINT`           | Inteiro grande (8 bytes)                                       | 9000000000                                       |
|                   | `SERIAL`           | Inteiro auto incrementável                                     | id automático                                    |
|                   | `BIGSERIAL`        | Auto incremento para BIGINT                                    | id grande                                        |
| Decimais          | `NUMERIC(p,s)`     | Número exato com precisão definida                             | 10.25                                            |
|                   | `DECIMAL(p,s)`     | Igual ao NUMERIC                                               | 150.75                                           |
|                   | `REAL`             | Float de precisão simples                                      | 10.5                                             |
|                   | `DOUBLE PRECISION` | Float de dupla precisão                                        | 9999.123                                         |
| Texto             | `CHAR(n)`          | Texto com tamanho fixo, ocupa espaços em branco                | "A"                                              |
|                   | `VARCHAR(n)`       | Texto com limite e não ocupa espaços em branco                 | "João"                                           |
|                   | `TEXT`             | Texto sem limite definido                                      | descrição longa                                  |
| Booleano          | `BOOLEAN`          | True or False, valores para true: 't', 'true', 'y', 'yes', '1' | Valores para false: 'f', 'false', 'n', 'no', '0' |
| Data e hora       | `DATE`             | Apenas data                                                    | 2026-03-17                                       |
|                   | `TIME`             | Apenas hora                                                    | 14:30:00                                         |
|                   | `TIMESTAMP`        | Data + hora                                                    | 2026-03-17 14:30                                 |
|                   | `TIMESTAMPTZ`      | Timestamp com timezone                                         | UTC                                              |
|                   | `INTERVAL`         | Intervalo de tempo                                             | 2 days                                           |
| UUID              | `UUID`             | Identificador universal                                        | uuid gerado                                      |
| JSON              | `JSON`             | Armazena JSON                                                  | {"nome":"João"}                                  |
|                   | `JSONB`            | JSON binário otimizado                                         | consulta rápida                                  |
| Binário           | `BYTEA`            | Dados binários                                                 | arquivos                                         |
| Arrays            | `ARRAY`            | Lista de valores                                               | {1,2,3}                                          |
| Geométrico        | `POINT`            | Ponto geométrico                                               | (10,20)                                          |
|                   | `LINE`             | Linha geométrica                                               | linha                                            |
|                   | `CIRCLE`           | Círculo                                                        | círculo                                          |
| Rede              | `INET`             | Endereço IP                                                    | 192.168.0.1                                      |
|                   | `CIDR`             | Bloco de rede                                                  | 192.168.0.0/24                                   |
|                   | `MACADDR`          | Endereço MAC                                                   | 00:11:22:33:44                                   |
| Texto estruturado | `TSVECTOR`         | Busca textual                                                  | indexação                                        |
|                   | `TSQUERY`          | Query de busca textual                                         | busca                                            |

## Tipos de dados Universais:
| Categoria      | Tipo Universal           | Descrição                 | Exemplos em bancos |
| -------------- | ------------------------ | ------------------------- | ------------------ |
| Inteiro        | `INTEGER`                | Número inteiro            | INT, INTEGER       |
| Inteiro grande | `BIGINT`                 | Inteiro grande            | BIGINT             |
| Decimal        | `DECIMAL`                | Número com precisão       | DECIMAL, NUMERIC   |
| Float          | `FLOAT`                  | Número de ponto flutuante | FLOAT, DOUBLE      |
| Texto curto    | `CHAR`                   | Texto de tamanho fixo     | CHAR               |
| Texto variável | `VARCHAR`                | Texto com limite          | VARCHAR            |
| Texto longo    | `TEXT`                   | Texto grande              | TEXT, CLOB         |
| Booleano       | `BOOLEAN`                | Verdadeiro ou falso       | BOOLEAN            |
| Data           | `DATE`                   | Data                      | DATE               |
| Hora           | `TIME`                   | Hora                      | TIME               |
| Data e hora    | `DATETIME` / `TIMESTAMP` | Data e hora               | TIMESTAMP          |
| Binário        | `BINARY`                 | Dados binários            | BLOB               |
| Identificador  | `UUID`                   | Identificador único       | UUID               |
| JSON           | `JSON`                   | Estrutura JSON            | JSON               |
| Lista          | `ARRAY`                  | Lista de valores          | ARRAY              |