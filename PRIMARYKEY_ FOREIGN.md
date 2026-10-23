A diferença principal é a função de cada chave:

- **`PRIMARY KEY` (chave primária)** identifica cada linha de uma tabela de forma única. Seus valores não podem se repetir nem ser `NULL`.
- **`FOREIGN KEY` (chave estrangeira)** liga uma tabela a outra. Ela contém valores que correspondem a uma chave da tabela relacionada. Pode haver valores repetidos; isso permite, por exemplo, que vários pedidos pertençam ao mesmo cliente.

Exemplo:

```sql
CREATE TABLE clientes (
    id INTEGER PRIMARY KEY,
    nome TEXT NOT NULL
);

CREATE TABLE pedidos (
    id INTEGER PRIMARY KEY,
    cliente_id INTEGER,
    FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);
```

Aqui, `clientes.id` identifica cada cliente. Já `pedidos.cliente_id` indica a qual cliente cada pedido pertence. A chave estrangeira também ajuda o banco a impedir que um pedido aponte para um cliente que não existe.

Uma forma de lembrar: a **`PRIMARY KEY` identifica** uma linha; a **`FOREIGN KEY` cria uma relação** com outra tabela.
