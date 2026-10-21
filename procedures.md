<img width="1942" height="809" alt="d2937f48-dff2-44ae-9d08-9024d4583fac" src="https://github.com/user-attachments/assets/07c44053-b578-4b1c-b20d-8d97d68cf207" />


Imagine uma central de pedidos: em vez de a aplicação enviar cada passo separadamente — criar pedido, registrar itens e atualizar o estoque — ela chama uma procedure que reúne essas operações.

```sql
CREATE PROCEDURE RegistrarPedido
    @ClienteId INT,
    @Valor DECIMAL(10, 2)
AS
BEGIN
    INSERT INTO Pedidos (ClienteId, Valor)
    VALUES (@ClienteId, @Valor);
END;
```

A aplicação pode chamá-la assim:

```sql
EXEC RegistrarPedido @ClienteId = 42, @Valor = 150.00;
```

Os comandos acima usam a sintaxe do SQL Server; outros bancos têm diferenças de sintaxe.

### Para que servem?

- Reunir operações que costumam ser executadas juntas.
- Padronizar regras que precisam ser aplicadas no banco.
- Reduzir a quantidade de comandos que a aplicação envia.
- Controlar permissões: a aplicação pode ter permissão para executar a procedure sem acesso direto a todas as tabelas.

### O que considerar

Uma procedure pode ser útil para operações de banco bem definidas. Porém, se muitas regras da aplicação forem colocadas nela, parte importante do sistema pode ficar espalhada entre o código da aplicação e o banco. Isso pode dificultar testes, manutenção e a troca de banco de dados.

**Em resumo:** a procedure é como uma operação pronta dentro do banco, que a aplicação chama pelo nome.
