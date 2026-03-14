# Playbook Comercial Íntegros — Lead Magnet Interativo

## O que é

Lead magnet interativo em formato de "playbook comercial" para o negócio Íntegros. É uma página HTML single-file que combina conteúdo educacional sobre vendas com ferramentas interativas: autoavaliação de 8 disciplinas comerciais, calculadora de pipeline e tracker semanal de prospecção. Captura email via ConvertKit antes de liberar o conteúdo.

## Stack

- **Frontend:** HTML + CSS + JS vanilla (arquivo único: `playbook-comercial.html`, ~72k linhas)
- **PDF:** jsPDF 2.5.2 (CDN) para download de resultados
- **Integração:** Kit/ConvertKit API pública (client-side)
- **Deploy:** Vercel (estático)
- **Domínio:** playbook.integros.org

## Deploy

Deploy automático via Vercel. `vercel.json` faz rewrite de `/` para `/playbook-comercial.html`.

```bash
# Deploy manual
vercel --prod

# O push na main faz deploy automático se conectado ao Vercel
```

## Comandos

```bash
# Servir localmente
python3 -m http.server 8000
# Acessar: http://localhost:8000/playbook-comercial.html
```

## Variáveis de Ambiente

Nenhuma no servidor. As credenciais do ConvertKit são **públicas por design** (chave pública da API):

| Chave | Valor | Nota |
|-------|-------|------|
| ConvertKit Public Key | `ACToNRKxQcIk8S6Brww_QA` | Pública por design da API |
| ConvertKit Form ID | `9067445` | ID do formulário |

Referência em `.env.example`.

## Estrutura de Pastas

```
playbook-comercial/
├── playbook-comercial.html  ← Arquivo principal (TUDO aqui: HTML + CSS + JS)
├── vercel.json              ← Rewrite "/" → "/playbook-comercial.html"
├── .env.example             ← Referência das credenciais (públicas)
├── .gitignore               ← .env, node_modules, .vercel
└── CLAUDE.md                ← Este arquivo
```

## Funcionalidades Interativas

### 1. Gate de Email (Lead Capture)
- Modal de captura de nome + email antes de acessar o conteúdo
- Integra com ConvertKit Form API (`/v3/forms/{id}/subscribe`)
- Após submit, libera acesso e esconde o modal

### 2. Autoavaliação de 8 Disciplinas
As 8 disciplinas comerciais avaliadas (nota 1-5):
1. Prospecção
2. Qualificação
3. Apresentação
4. Objeções
5. Fechamento
6. Follow-up
7. Pipeline
8. Mindset

Gera resultado automático com diagnóstico por disciplina e score total.

### 3. Calculadora de Pipeline
Inputs do usuário geram cálculos em tempo real:
- Meta de faturamento
- Ticket médio
- Taxa de conversão
- Ciclo de vendas
- Resultado: quantas oportunidades precisa, quantos contatos/dia

### 4. Download PDF
Usa jsPDF para gerar PDF com os resultados da autoavaliação e calculadora.

### 5. Tracker Semanal
Tabela interativa para registrar atividades de prospecção por dia da semana.

### 6. Navegação Ativa
IntersectionObserver destaca seção atual na navegação lateral.

## Design System

- **Fontes:** DM Serif Display (títulos) + DM Sans (corpo)
- **Cores Íntegros:**
  - Verde: `#28514D` (--green)
  - Verde escuro: `#1C3B38` (--green-deep)
  - Bege: `#E0DBC6` (--beige)
  - Dourado: `#BAA36C` (--gold)
  - Oliva: `#968659` (--olive)
- **CSS vars:** `--green`, `--green-deep`, `--beige`, `--beige-light`, `--gold`, `--gold-light`, `--olive`, `--dark`, `--white`
- **Visual:** Clean, editorial, sem firula. Cards com bordas sutis, tipografia elegante.

## Regras de Desenvolvimento

### Fazer
- Manter TUDO em um único arquivo HTML (é single-file por design)
- Usar as CSS vars do design system Íntegros
- Testar interatividade (calculadora, autoavaliação) após qualquer mudança
- Verificar PDF gerado após alterações no layout

### Não fazer
- Não separar em múltiplos arquivos — é single-file de propósito
- Não alterar credenciais do ConvertKit (são públicas por design)
- Não adicionar frameworks/bundlers
- Não alterar as 8 disciplinas sem contexto de negócio
- Não remover o gate de email — é a razão de ser do lead magnet

## Contexto de Negócio

O Playbook Comercial é um lead magnet que captura emails de empresários interessados em melhorar suas vendas. Faz parte do topo do funil de aquisição da Íntegros. Após preencher o email, o lead entra no ConvertKit e recebe sequência de nurturing. O conteúdo do playbook posiciona o Kevin como autoridade em vendas para prestadores de serviço.

## Git

- **Branch:** `main` (push direto OK — é estático)
- **Commits:** conventional commits em inglês
