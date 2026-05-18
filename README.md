

## API principal

- `GET /api/users`
- `POST /api/users`
- `GET /api/laboratories`
- `POST /api/laboratories`
- `GET /api/reservations`
- `POST /api/reservations`
- `GET /api/transfers`
- `POST /api/transfers`
- `POST /api/transfers/{id}/approve`
- `POST /api/transfers/{id}/reject`

## Atividade SOLID

Foi adicionada uma implementacao separada em `backend/src/main/java/com/labagenda/delivery/` para demonstrar os principios SOLID em um contexto de delivery.

Testes correspondentes ficam em `backend/src/test/java/com/labagenda/delivery/`.

### Principios cobertos

- SRP:  persistencia e exibicao de pedidos em classes separadas
- OCP: pagamento por cartao, PIX e dinheiro
- LSP: hierarquia de produtos com `Pizza`, `Hamburguer` e `Bebida`
- DIP: servico de notificacao dependente de abstracao de canal
