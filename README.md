Os principais conceitos de banco de dados explicam **como os dados são organizados, relacionados, consultados e protegidos**. Um bom jeito de entendê-los é imaginar um sistema de vendas.

## 1. Banco de dados e SGBD

- **Banco de dados:** conjunto organizado de informações, como clientes, produtos e pedidos.
- **SGBD** (Sistema de Gerenciamento de Banco de Dados): programa que armazena e administra essas informações. Exemplos: PostgreSQL, MySQL, SQL Server e SQLite.

## 2. Tabelas, linhas e colunas

Em um banco relacional, os dados ficam em tabelas:

- **Tabela:** representa um tipo de informação, como `clientes`.
- **Linha ou registro:** representa uma ocorrência, como um cliente específico.
- **Coluna ou campo:** representa uma característica, como nome ou e-mail.
- **Tipo de dado:** define que valores uma coluna aceita, como `INTEGER`, `VARCHAR` ou `DATE`.

## 3. Chaves e relacionamentos

As chaves identificam registros e conectam tabelas:

- **Chave primária (`PRIMARY KEY`):** identifica cada linha de forma única.
- **Chave estrangeira (`FOREIGN KEY`):** aponta para uma linha em outra tabela.
- **Relacionamento:** descreve como os registros se associam:
  - **Um para um:** uma pessoa tem um perfil.
  - **Um para muitos:** um cliente pode fazer vários pedidos.
  - **Muitos para muitos:** vários pedidos podem conter vários produtos. Normalmente, cria-se uma tabela intermediária, como `itens_pedido`.

Exemplo simplificado:

```text
clientes
  id (PK)
  nome

pedidos
  id (PK)
  cliente_id (FK)
  data

itens_pedido
  pedido_id (FK)
  produto_id (FK)
  quantidade
```

## 4. Restrições e integridade

Restrições impedem que dados inválidos sejam gravados:

- `NOT NULL`: exige um valor.
- `UNIQUE`: impede duplicatas.
- `CHECK`: valida uma condição, como preço maior que zero.
- `PRIMARY KEY`: exige identificação única.
- `FOREIGN KEY`: exige que a referência exista na tabela relacionada.

Essas regras ajudam a manter a **integridade dos dados**.

## 5. Modelagem e normalização

- **Modelagem de dados:** planejar quais tabelas, colunas e relacionamentos o sistema precisa.
- **Normalização:** organizar os dados para reduzir repetição e evitar inconsistências.

Por exemplo, em vez de repetir o endereço do cliente em cada pedido, o endereço fica registrado no cadastro do cliente e os pedidos se relacionam a ele.

## 6. SQL e operações

SQL é a linguagem usada para definir e manipular dados em bancos relacionais. Suas operações mais comuns são chamadas de **CRUD**:

| Operação | SQL | Ação |
|---|---|---|
| Criar | `INSERT` | Adiciona registros |
| Ler | `SELECT` | Consulta registros |
| Atualizar | `UPDATE` | Altera registros |
| Excluir | `DELETE` | Remove registros |

Também é útil conhecer:

- `CREATE`, `ALTER`, `DROP`: criam ou alteram estruturas.
- `JOIN`: combina dados de tabelas relacionadas.
- `GROUP BY`: agrupa dados para cálculos.
- `ORDER BY`: ordena os resultados.

## 7. Transações e ACID

Uma **transação** agrupa operações que devem ser tratadas como uma unidade. Por exemplo, registrar um pedido e reduzir o estoque.

As propriedades **ACID** descrevem garantias importantes:

- **Atomicidade:** todas as operações acontecem ou nenhuma acontece.
- **Consistência:** as regras do banco continuam válidas.
- **Isolamento:** transações simultâneas não interferem de forma indevida.
- **Durabilidade:** após a confirmação, os dados persistem.

## 8. Índices e desempenho

Um **índice** ajuda o banco a encontrar registros com mais rapidez, parecido com o índice de um livro. Porém, índices ocupam espaço e podem deixar inserções e atualizações mais lentas, pois também precisam ser atualizados.

Consultas lentas podem ser investigadas com ferramentas de análise do plano de execução, como `EXPLAIN`.

## 9. Concorrência e isolamento

Várias pessoas ou processos podem usar o banco ao mesmo tempo. O banco precisa controlar esse acesso para evitar resultados incorretos, como dois processos alterarem o mesmo estoque simultaneamente.

Esse tema envolve **bloqueios**, **níveis de isolamento** e o controle de versões das linhas, como o MVCC usado pelo PostgreSQL.

## 10. Segurança, backup e manutenção

Também fazem parte do trabalho com bancos de dados:

- **Autenticação e permissões:** definir quem pode acessar ou alterar dados.
- **Backup e restauração:** recuperar dados após falhas ou exclusões acidentais.
- **Manutenção:** manter o banco saudável e eficiente. No PostgreSQL, por exemplo, há `VACUUM`; no SQLite, `VACUUM` reconstrói e compacta o arquivo do banco.

## 11. Relacional e NoSQL

- **Banco relacional:** organiza dados em tabelas relacionadas; costuma usar SQL. Exemplos: PostgreSQL e MySQL.
- **NoSQL:** inclui bancos orientados a documentos, chave-valor, grafos e outros modelos. Pode ser adequado a certos formatos de dados ou necessidades de escala, mas não é automaticamente melhor que um banco relacional.

### Uma boa ordem para estudar

1. Tabelas, colunas e tipos de dados  
2. Chaves primárias e estrangeiras  
3. Relacionamentos e modelagem  
4. `SELECT`, filtros e `JOIN`  
5. Restrições e normalização  
6. Transações e ACID  
7. Índices e desempenho  
8. Segurança, backups e manutenção  

Esses conceitos formam a base para projetar e usar bancos de dados com segurança.
