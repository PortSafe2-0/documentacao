# Documentação da API — PortSafe 2.0

## Visão Geral

Esta documentação descreve os principais endpoints da API RESTful do sistema **PortSafe 2.0**. O backend foi desenvolvido em ASP.NET Core 8, com autenticação JWT, seguindo boas práticas de arquitetura, DTOs e camadas de serviço.

---

## Autenticação

- **JWT Bearer Token** obrigatório para endpoints protegidos.
- Obtenha o token via `/api/Auth/login` e utilize o botão "Authorize" no Swagger para autenticar.

### Endpoints

#### `POST /api/Auth/login`
- **Descrição:** Realiza login e retorna o token JWT.
- **Body:**
  ```json
  {
    "email": "usuario@email.com",
    "password": "suaSenha"
  }
  ```
- **Response:**
  ```json
  {
    "token": "<jwt-token>"
  }
  ```

#### `POST /api/Auth/register`
- **Descrição:** Registra um novo usuário.
- **Body:**
  ```json
  {
    "name": "Nome",
    "email": "usuario@email.com",
    "password": "suaSenha",
    "role": "Admin|Porteiro|Morador"
  }
  ```

---

## Usuários

#### `GET /api/Users`
- Lista todos os usuários (apenas Admin).

#### `GET /api/Users/{id}`
- Busca usuário por ID.

#### `POST /api/Users`
- Cria novo usuário.

#### `PUT /api/Users/{id}`
- Atualiza usuário.

#### `DELETE /api/Users/{id}`
- Remove usuário.

---

## Lockers

#### `GET /api/Lockers`
- Lista todos os lockers.

#### `GET /api/Lockers/{id}`
- Busca locker por ID.

#### `POST /api/Lockers`
- Cria novo locker (apenas Admin).
- **Body:**
  ```json
  {
    "code": "A01",
    "location": "Bloco A"
  }
  ```

#### `PUT /api/Lockers/{id}`
- Atualiza locker.

#### `DELETE /api/Lockers/{id}`
- Remove locker.

---

## Entregas (Deliveries)

#### `GET /api/Deliveries`
- Lista todas as entregas.

#### `GET /api/Deliveries/{id}`
- Busca entrega por ID.

#### `POST /api/Deliveries`
- Cria nova entrega.
- **Body:**
  ```json
  {
    "userId": "<guid>",
    "lockerId": "<guid>",
    "recipientName": "Nome do destinatário",
    "trackingCode": "ABC123456"
  }
  ```

#### `PUT /api/Deliveries/{id}`
- Atualiza entrega.

#### `DELETE /api/Deliveries/{id}`
- Remove entrega.

#### `POST /api/Deliveries/{id}/withdraw`
- Marca entrega como retirada e libera o locker.

---

## Observações

- Todos os endpoints retornam respostas padronizadas:
  ```json
  {
    "success": true|false,
    "data": {},
    "message": "mensagem opcional"
  }
  ```
- Utilize o Swagger em `/swagger` para explorar e testar todos os endpoints.
- Roles suportadas: `Admin`, `Porteiro`, `Morador`.
- Para endpoints protegidos, inclua o token JWT no header `Authorization: Bearer <token>`.


