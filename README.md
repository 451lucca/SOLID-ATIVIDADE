# Agenda de Laboratórios

Sistema full stack para CRUD de usuários, laboratórios e reservas, com fluxo de solicitação de troca que precisa da aprovação do usuário alvo.

## Estrutura

- `backend/` - Spring Boot + JPA + MySQL
- `frontend/` - React + Vite
- `docker-compose.yml` - banco MySQL pronto para subir localmente

## O que o sistema faz

- CRUD de usuários
- CRUD de laboratórios
- CRUD de reservas
- validação de conflito de horário no mesmo laboratório
- solicitação de troca de reserva entre usuários
- aprovação ou rejeição da troca pelo usuário alvo

## Como rodar

### 1. Subir o MySQL

```bash
docker compose up -d
```

### 2. Rodar o backend

Entre na pasta `backend` e execute:

```bash
mvn spring-boot:run
```

O backend sobe em `http://localhost:8080`.

### 3. Rodar o frontend

Entre na pasta `frontend` e execute:

```bash
npm install
npm run dev
```

O frontend sobe em `http://localhost:5173`.

## Observação sobre autorização

Este projeto usa um seletor de **usuário ativo** na interface para simular quem está operando o sistema.
Na troca de reserva, o backend valida que apenas o **usuário alvo** pode aprovar ou rejeitar a solicitação.
Se quiser, depois eu posso evoluir isso para autenticação real com JWT e Spring Security.

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

- SRP: criacao, persistencia e exibicao de pedidos em classes separadas
- OCP: pagamento por cartao, PIX e dinheiro via interface extensivel
- LSP: hierarquia de produtos com `Pizza`, `Hamburguer` e `Bebida`
- ISP: interfaces pequenas para notificacoes, relatorios, pedidos e entregas
- DIP: servico de notificacao dependente de abstracao de canal
