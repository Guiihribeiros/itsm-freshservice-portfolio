# Estrutura ITSM no Freshservice — estudo de caso

Implementação, do zero, de um ambiente completo de ITSM na plataforma **Freshservice**, substituindo o TOPdesk como
ferramenta de Service Desk de uma holding do setor financeiro. Este repositório documenta o projeto real que conduzi
como responsável técnico, com nome da empresa, domínios e nomes de terceiros fictícios por confidencialidade — a
estrutura, as decisões e as configurações são as que de fato implementei.

**[Ver o documento completo (GitHub Pages)](#)** — atualize este link após habilitar o Pages (veja "Como publicar" abaixo).

## Escopo do projeto

Substituição total da ferramenta de Service Desk, cobrindo quatro módulos:

- **Service Desk / Gestão de Incidentes** — categorização, matriz de priorização, SLAs e roteamento automático de tickets
- **Catálogo de Serviços** — 34 itens em 11 categorias, com SLA e grupo operador por subcategoria
- **CMDB / Gestão de Ativos** — inventário completo migrado de uma base legada (86 ativos)
- **Change & Problem Management** — modelo de tipos de mudança e aprovação

## Destaques técnicos

- **Modelagem de categorização de ticket**: taxonomia de 2 níveis (categoria/subcategoria) espelhando o catálogo de
  serviços real, descobrindo e contornando um bug da ferramenta nativa de edição em massa que corrompia a
  associação categoria↔subcategoria.
- **Motor de SLA em duas camadas**: SLA fixo por subcategoria para Solicitações de Serviço (previsíveis) e SLA
  calculado por matriz de Impacto × Urgência para Incidentes (variáveis), documentando a limitação da plataforma
  de não permitir automação por subcategoria (só por categoria).
- **SSO com Microsoft Entra ID (SAML)**: configuração e troubleshooting de dois erros reais de integração
  (identificador de entidade divergente, resposta SAML não assinada) até login funcional com MFA.
- **Migração de dados via importação em massa**: mapeamento de campos entre a ferramenta legada e o Freshservice,
  incluindo conversão de valores de status para os identificadores internos exigidos pela importação.
- **Pesquisa de satisfação (CSAT)**: localização completa para português, redesenho de perguntas e integração com
  o fluxo de resolução de ticket.
- **Alternador de tema claro/escuro**: a própria documentação (este `index.html`) é interativa, com preferência de
  tema salva no navegador de quem acessa.

## Sobre a documentação

O arquivo [`index.html`](index.html) é a documentação viva do projeto, escrita como um dashboard navegável (com
sumário lateral, registro de configuração campo a campo e log cronológico de decisões) em vez de um documento
estático — pensado para servir como fonte única de verdade durante a implementação real.

## Como publicar via GitHub Pages

1. Crie o repositório no GitHub e suba este conteúdo (`git init`, `git add .`, `git commit`, `git remote add origin <url>`, `git push -u origin main`).
2. No GitHub, vá em **Settings → Pages** → em "Build and deployment", selecione **Deploy from a branch** → branch `main`, pasta `/ (root)`.
3. O GitHub publica em `https://<seu-usuário>.github.io/<repo>/` em alguns minutos.
4. Atualize o link no topo deste README com essa URL.

## Aviso

Nome da empresa, domínios de e-mail, subdomínios e nomes de colegas/parceiros neste repositório são fictícios.
Nenhum dado real de clientes, colaboradores ou sistemas é exibido.
