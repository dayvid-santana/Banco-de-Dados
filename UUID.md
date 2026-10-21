**UUID** (*Universally Unique Identifier*) é um identificador criado para que sistemas consigam nomear registros sem depender de uma sequência central.

Um exemplo:

```text
550e8400-e29b-41d4-a716-446655440000
```

Ele representa um valor de **128 bits**, escrito normalmente em grupos de letras e números separados por hífens. Uma versão comum, a **UUID v4**, é gerada aleatoriamente. A chance de dois sistemas produzirem o mesmo valor é extremamente pequena, embora não seja matematicamente impossível.

### UUID como identificador no banco

Em vez de dar a um pedido o ID `1042`, você poderia usar um UUID:

| ID | Pedido |
|---|---|
| `550e8400-e29b-41d4-a716-446655440000` | Pedido de Ana |

Isso permite que diferentes serviços criem identificadores sem combinar quem vai usar o próximo número. É útil em sistemas distribuídos, integrações e APIs.

Em Python, por exemplo:

```python
from uuid import uuid4

pedido_id = uuid4()
print(pedido_id)
```

Um **inteiro sequencial** costuma ser menor e mais legível. Um UUID reduz a dependência de uma sequência compartilhada, mas ocupa mais espaço e é menos fácil de ler. UUID também **não deve ser tratado como senha ou prova de autorização**: conhecer um identificador não deve dar acesso ao registro.
