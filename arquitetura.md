# 🏗 Arquitetura do Sistema — PortSafe 2.0

## 1. Visão Arquitetural

O **PortSafe 2.0** é um sistema para gerenciamento seguro de entregas em condomínios utilizando **dispositivos IoT, backend em nuvem, banco de dados, aplicativo mobile e interface de monitoramento**.

A arquitetura do sistema tem como objetivo:

- organizar os componentes do sistema
- garantir comunicação padronizada entre módulos
- permitir escalabilidade e manutenção futura
- servir como base técnica para o desenvolvimento do MVP

---

## 2. Princípios Arquiteturais

A arquitetura segue alguns princípios fundamentais:

**Arquitetura em Camadas**  
- O sistema é dividido em camadas independentes.

**Baixo Acoplamento**  
- Os módulos se comunicam por meio de padrões como **API REST e MQTT**.

**Alta Coesão**  
- Cada componente possui uma responsabilidade específica.

**Escalabilidade**  
- A arquitetura suporta aumento de usuários, dispositivos e volume de dados.

**Interoperabilidade**  
- Uso de padrões abertos como **MQTT, JSON e REST**.

---

## 3. Visão Geral da Arquitetura

Fluxo principal do sistema:

    Lockers IoT
    ↓
    Broker MQTT
    ↓
    Backend (API C#)
    ↓
    Banco de Dados
    ↓
    Cloud
    ↓
    Aplicativo Mobile
    ↓
    Interface de Monitoramento


---

## 4. Camadas do Sistema

## Dispositivos IoT
Responsáveis por registrar eventos físicos dos lockers e enviar dados via MQTT.

Exemplo de payload:

    {
        "deviceId": "locker01",
        "status": "opened",
        "deliveryId": "DEL-1023"
    }


## Comunicação (MQTT)

Gerencia a troca de mensagens entre dispositivos e backend.

Estrutura de tópicos:

    portsafe/locker/{lockerId}/status

    portsafe/locker/{lockerId}/command

    portsafe/delivery/{deliveryId}/event

## Backend

Responsável por:

- processar eventos;
- aplicar regras de negócio;
- armazenar dados;
- fornecer API para o aplicativo;
- Tecnologia prevista:;
- C#;
- ASP.NET Core.

Endpoints principais:

    POST /deliveries

    GET /deliveries

    GET /lockers

    POST /lockers/open

    POST /auth/login

## Banco de Dados

Armazena dados do sistema como:

- usuários;
- lockers;
- entregas;
- eventos.

Banco previsto: **PostgreSQL**

## Aplicativo Mobile

Aplicação desenvolvida com:

- Expo;
- React Native;

Permite ao usuário:
- visualizar entregas;
- receber notificações;
- retirar encomendas.

## 5. Integração do Sistema
Integração Vertical

Fluxo do dado no sistema:

    IoT → Backend → Banco de Dados → Dashboard → Decisão

## Integração Horizontal

A arquitetura permite integração futura com:

- sistemas condominiais;
- plataformas logísticas;
- sistemas administrativos.

## 6. Segurança

Principais medidas:

- autenticação via JWT;
- comunicação segura via HTTPS;
- controle de acesso na API;
- proteção do broker MQTT.

## 7. Modelo de Dados Inicial

### User:
    id
    name
    email
    role

### Delivery:
    id
    userId
    lockerId
    status

### Locker:
    id
    location
    status

### LockerEvent:
    id
    lockerId
    eventType
    timestamp

## 8. Estrutura da API

Principais endpoints:

    POST /auth/login

    POST /deliveries

    GET /deliveries

    GET /lockers

    POST /lockers/open

## 9. Requisitos Não Funcionais

A arquitetura considera:

- disponibilidade;
- escalabilidade;
- performance;
- confiabilidade;
- facilidade de manutenção.