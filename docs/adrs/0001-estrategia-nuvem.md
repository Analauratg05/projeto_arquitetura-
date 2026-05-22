# ADR 0001 — Estratégia de Nuvem e Escalabilidade

## Status
Aceito

---

## Contexto
O HealthSync precisa suportar crescimento contínuo de usuários, alta disponibilidade e processamento de dados médicos sensíveis.
Além disso, o sistema integra:
- Inteligência Artificial
- Dispositivos IoT
- Teleconsultas simultâneas
A arquitetura necessita de escalabilidade horizontal, monitoramento contínuo e resiliência.

---

## Decisão

Foi adotada a AWS como provedora cloud principal.
Serviços utilizados:
- Amazon EKS
- Amazon RDS PostgreSQL
- API Gateway
- CloudWatch
A aplicação será implantada utilizando containers Docker e Kubernetes.

---

## Alternativas Consideradas

### PaaS simples
Rejeitado por limitar flexibilidade e escalabilidade avançada.

### Infraestrutura monolítica
Rejeitada devido à baixa capacidade de expansão e alta indisponibilidade.

---

## Trade-off
Ganhamos:
- escalabilidade,
- alta disponibilidade,
- flexibilidade,
- resiliência.

Abrindo mão de:
- simplicidade operacional,
- menor custo inicial.
O trade-off é aceitável porque o contexto prioriza crescimento contínuo, segurança e disponibilidade.

---

## Consequências
- Necessidade de Kubernetes
- Maior complexidade DevOps
- Necessidade de observabilidade avançada
- Evolução futura para multi-região
