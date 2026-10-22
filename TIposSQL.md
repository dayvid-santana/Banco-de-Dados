Em SQL, **tipagem** é o tipo de dado que uma coluna pode guardar. Não existe uma lista única que funcione em todos os bancos: PostgreSQL, MySQL e SQL Server, por exemplo, têm tipos próprios e diferenças de suporte. [postgresql.org](https://www.postgresql.org/docs/18/datatype.html?utm_source=chatgpt.com)

### Tipos mais comuns

| Categoria | Tipos | Para que servem |
|---|---|---|
| **Números inteiros** | `SMALLINT`, `INTEGER` ou `INT`, `BIGINT` | Números sem casas decimais, como quantidade ou idade |
| **Números exatos** | `DECIMAL(p,s)`, `NUMERIC(p,s)` | Valores com casas decimais que precisam de precisão, como dinheiro |
| **Números aproximados** | `REAL`, `FLOAT`, `DOUBLE PRECISION` | Valores decimais em que pequenas aproximações são aceitáveis, como medições científicas |
| **Texto** | `CHAR(n)`, `VARCHAR(n)`, `CHARACTER VARYING(n)`, `TEXT` | Letras e outros caracteres; `CHAR` tem tamanho fixo e `VARCHAR` varia |
| **Data e hora** | `DATE`, `TIME`, `TIMESTAMP`, `INTERVAL` | Datas, horários, data e hora, ou períodos de tempo |
| **Booleano** | `BOOLEAN` ou `BOOL` | Valores verdadeiro/falso; alguns bancos usam `BIT` |
| **Bits** | `BIT(n)`, `BIT VARYING(n)` | Sequências de bits |
| **Dados binários** | `BINARY`, `VARBINARY`, `BLOB` | Arquivos ou outros dados em formato binário |
| **Dados estruturados** | `JSON`, `XML` | Documentos JSON ou XML, quando o banco oferece suporte |

`p` e `s` definem a precisão de um número. Por exemplo, `DECIMAL(8,2)` permite até 8 dígitos no total, sendo 2 depois da vírgula.

### Exemplos que dependem do banco

- **MySQL:** `TINYINT`, `MEDIUMINT`, `DATETIME`, `YEAR`, `ENUM`, `SET` e tipos espaciais.
- **PostgreSQL:** `UUID`, `JSONB`, `BYTEA`, arrays, intervalos e tipos geométricos.
- **SQL Server:** `UNIQUEIDENTIFIER`, `DATETIME2`, `DATETIMEOFFSET`, `MONEY`, `GEOGRAPHY` e `GEOMETRY`. [dev.mysql.com](https://dev.mysql.com/doc/refman/26.10/en/data-types.html?utm_source=chatgpt.com)

Exemplo de uso:

```sql
CREATE TABLE produtos (
    id          BIGINT,
    nome        VARCHAR(100),
    preco       DECIMAL(10, 2),
    disponivel  BOOLEAN,
    criado_em   TIMESTAMP
);
```

Nesse exemplo, `id` guarda um número inteiro grande, `nome` guarda texto, `preco` guarda um valor decimal exato, `disponivel` guarda verdadeiro ou falso e `criado_em` guarda data e hora.

`PRIMARY KEY`, `NOT NULL` e `AUTO_INCREMENT` **não são tipagens**: são regras ou propriedades aplicadas às colunas. O suporte e alguns nomes variam conforme o banco.
