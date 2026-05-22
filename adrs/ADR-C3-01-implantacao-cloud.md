# ADR-C3-01 — Estratégia de Implantação Cloud

## Projeto: HealthSync

## Status: Proposto

---

## Contexto
O HealthSync é uma plataforma de telemedicina baseada em microsserviços, responsável por integrar consultas online, monitoramento de pacientes via dispositivos IoT e recomendações médicas utilizando Inteligência Artificial.

O sistema possui requisitos críticos de segurança, disponibilidade e escalabilidade, pois lida com dados sensíveis de saúde e múltiplos acessos simultâneos.

As principais restrições identificadas são:
- Time reduzido para operações de infraestrutura complexa
- Necessidade de alta disponibilidade (>99%)
- Crescimento esperado no volume de usuários e dispositivos conectados
- Necessidade de conformidade com a LGPD
- Integração contínua com serviços externos de IA e IoT
- Necessidade de monitoramento e observabilidade em tempo real
Além disso, o projeto precisa equilibrar escalabilidade e segurança sem aumentar excessivamente a complexidade operacional.

---

## Decisão

Foi adotada uma estratégia híbrida de cloud utilizando a AWS como provedora principal.

Modelo escolhido:
- IaaS + PaaS + Containers

Serviços principais:
- Amazon EKS para orquestração Kubernetes
- Amazon RDS PostgreSQL para banco gerenciado
- API Gateway para gerenciamento das APIs
- Serviços de mensageria para comunicação assíncrona
- Amazon CloudWatch para monitoramento e observabilidade
- Containers Docker para execução dos microsserviços
A arquitetura utilizará auto-scaling horizontal para os serviços críticos, principalmente módulos de IA, teleconsulta e processamento IoT.

---

## Trade-off Aceito

Ganhamos:
- escalabilidade automática
- alta disponibilidade
- isolamento entre serviços
- flexibilidade tecnológica
- maior resiliência
- e facilidade de evolução futura

Abrindo mão de:
- menor complexidade operacional
- simplicidade de infraestrutura
- e redução imediata de custos

Esse trade-off é aceitável porque o contexto do HealthSync prioriza segurança, disponibilidade e capacidade de crescimento contínuo. Como o sistema manipula dados médicos sensíveis e serviços críticos de atendimento remoto, a arquitetura precisa suportar falhas, expansão e integração com novas tecnologias sem comprometer o núcleo do domínio.

---

## Consequências

A adoção dessa estratégia impacta diretamente a arquitetura do sistema:
- necessidade de pipeline CI/CD automatizado
- maior investimento em observabilidade e monitoramento
- adoção de práticas DevOps
- implementação de políticas de segurança cloud
- necessidade de gerenciamento de containers e Kubernetes

Além disso, essa decisão força futuras definições arquiteturais relacionadas a:
- estratégia multi-região para disaster recovery
- otimização de custos cloud
- governança de microsserviços
- políticas de versionamento de APIs
- e evolução da comunicação assíncrona entre serviços
A longo prazo, a arquitetura ficará mais preparada para crescimento escalável e integração com novos serviços de IA e dispositivos médicos inteligentes.
