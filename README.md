# ServiceNow + GitHub Actions Automation

Este projeto implementa uma automação que integra **ServiceNow** com **GitHub Actions** para criar **Change Requests (CRs)** automaticamente durante o fluxo de CI/CD.  
A automação garante que cada mudança passe por um processo de aprovação no ServiceNow antes de avançar para o próximo passo do pipeline.

---

## Objetivo

- Criar **Change Requests** automaticamente no ServiceNow sempre que um workflow do GitHub Actions for disparado.
- Deixar o CR em estado **pendente de aprovação**.
- Após aprovação pelo usuário responsável no ServiceNow, o pipeline continua para o próximo estágio (deploy, release, etc).
- Garantir maior **governança e rastreabilidade** em mudanças de produção.

---

## Como funciona

1. Um workflow do **GitHub Actions** é iniciado (ex: push para `main` ou abertura de PR).
2. O workflow chama a automação que:
   - Conecta-se ao ServiceNow via API.
   - Cria um **Change Request** com os detalhes da mudança.
   - Marca o CR como **pendente de aprovação**.
3. O pipeline **aguarda** até que o CR seja aprovado no ServiceNow.
4. Após aprovação, uma custom rule do GitHub Actions é validada e o workflow continua para o próximo job (ex: deploy).

---
