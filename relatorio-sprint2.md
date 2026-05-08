# 📊 Relatório Estruturado da Entrega — Backend, AWS e Mobile

**Projeto:** PortSafe 2.0 – Ecossistema Inteligente de Entregas com IoT e Nuvem
**Sprint:** Evolução da Implementação Técnica

---

# 1. Visão Geral da Sprint

Nesta sprint, o projeto evoluiu da fase de planejamento para a implementação prática dos principais módulos do sistema.

As entregas realizadas envolveram:

* Desenvolvimento da API backend integrada ao banco de dados
* Implementação da arquitetura IoT utilizando AWS
* Evolução do aplicativo mobile com telas funcionais executando via Expo

O foco principal foi validar a arquitetura proposta e iniciar a integração entre os componentes do ecossistema.

---

# 2. Implementação do Backend

Foi desenvolvida a estrutura principal da API do sistema, incluindo:

* Rotas da aplicação
* Organização de controllers e serviços
* Regras de negócio
* Integração funcional com banco de dados

O backend foi estruturado de forma modular, preparado para integração futura com o mobile e os dispositivos IoT.

---

# 3. Implementação da Arquitetura IoT em AWS

A comunicação IoT foi implementada utilizando o AWS IoT Core.

Durante esta etapa:

* Foi criada uma Thing representando o dispositivo IoT
* Foram configurados certificados digitais e policies de segurança
* Foi utilizada comunicação MQTT para troca de mensagens em tempo real

Para testes, foi utilizado um simulador em Node.js chamado `mqtt-sim.js`, responsável por publicar mensagens automaticamente em tópicos MQTT.

As mensagens foram monitoradas em tempo real através do MQTT Test Client da AWS, validando o funcionamento da comunicação entre dispositivo e nuvem.

---

# 4. Evolução do Aplicativo Mobile

Na sprint anterior, o projeto possuía apenas protótipos no Figma.

Nesta sprint, o aplicativo evoluiu para telas funcionais executando diretamente no celular através do Expo.

O aplicativo já possui:

* Navegação entre telas
* Componentização das interfaces
* Estrutura preparada para chamadas de API
* Organização dos serviços da aplicação

Atualmente, os dados ainda são mockados, permitindo o desenvolvimento paralelo entre frontend e backend até a integração completa.

---

# 5. Decisões Técnicas

Algumas decisões importantes tomadas nesta sprint:

* Uso do Expo para acelerar desenvolvimento mobile
* Utilização de MQTT para comunicação IoT
* Estrutura modular da API backend
* Uso de dados mockados para evolução paralela das equipes

Essas escolhas garantem maior escalabilidade, organização e facilidade de manutenção do sistema.

---

# 6. Resultados Obtidos

Ao final da sprint, o projeto já apresenta:

* Backend funcional integrado ao banco de dados
* Comunicação IoT validada na AWS
* Aplicativo mobile funcionando em dispositivos reais
* Estrutura pronta para futuras integrações

---

# 7. Conclusão

Com esta entrega, o PortSafe 2.0 evolui de um protótipo conceitual para um sistema funcional em desenvolvimento.

A sprint permitiu validar a arquitetura técnica proposta e consolidar a base para as próximas integrações entre mobile, backend e IoT.
