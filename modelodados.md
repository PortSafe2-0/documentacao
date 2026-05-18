# Documentação dos Modelos de Dados

Este documento descreve os modelos de dados utilizados no sistema PortSafe.

---

## User

Representa um usuário do sistema.

| Propriedade     | Tipo      | Descrição                |
|-----------------|-----------|--------------------------|
| Id              | Guid      | Identificador único      |
| Name            | string    | Nome do usuário          |
| Email           | string    | E-mail do usuário        |
| PasswordHash    | string    | Hash da senha            |
| Role            | Role      | Papel do usuário         |
| CreatedAt       | DateTime  | Data de criação          |

---

## Role (Enum)

Define os papéis possíveis para um usuário.

- **Admin**
- **Porteiro**
- **Morador**
- **User**

---

## Locker

Representa um armário inteligente para entregas.

| Propriedade     | Tipo          | Descrição                        |
|-----------------|---------------|----------------------------------|
| Id              | Guid          | Identificador único              |
| Code            | string        | Código do armário                |
| Location        | string        | Localização física               |
| Status          | LockerStatus  | Status do armário                |
| IsActive        | bool          | Se o armário está ativo          |
| CreatedAt       | DateTime      | Data de criação                  |

### LockerStatus (Enum)
- **Available**
- **Occupied**
- **Maintenance**

---

## Delivery

Representa uma entrega realizada no sistema.

| Propriedade     | Tipo            | Descrição                        |
|-----------------|-----------------|----------------------------------|
| Id              | Guid            | Identificador único              |
| UserId          | Guid            | Id do usuário destinatário       |
| LockerId        | Guid            | Id do armário                    |
| RecipientName   | string          | Nome do destinatário             |
| TrackingCode    | string          | Código de rastreamento           |
| Status          | DeliveryStatus  | Status da entrega                |
| CreatedAt       | DateTime        | Data de criação                  |
| DeliveredAt     | DateTime?       | Data de entrega (opcional)       |
| WithdrawnAt     | DateTime?       | Data de retirada (opcional)      |
| User            | User?           | Navegação para o usuário         |
| Locker          | Locker?         | Navegação para o armário         |

### DeliveryStatus (Enum)
- **Pending**
- **Delivered**
- **Withdrawn**
- **Cancelled**

---

> **Observação:** Os relacionamentos de navegação (User, Locker) em `Delivery` são opcionais e facilitam o acesso aos dados relacionados.
