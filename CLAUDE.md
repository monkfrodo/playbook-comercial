# Playbook Comercial Íntegros

## O que é
Lead magnet em HTML single-page para o negócio Íntegros (mentoria comercial do Kevin Eger).
Arquivo auto-contido: HTML + CSS + JS tudo em `playbook-comercial.html`.

## Stack
- HTML/CSS/JS vanilla (single file)
- jsPDF 2.5.2 (CDN) para download de resultados
- Integração Kit (ConvertKit) via API pública (client-side)
- Deploy: Vercel (estático)
- Domínio: playbook.integros.org

## Estrutura
```
playbook-comercial.html   ← arquivo principal (tudo aqui)
vercel.json               ← config de deploy (rewrite index)
CLAUDE.md                 ← este arquivo
```

## Design System
- Fontes: DM Serif Display (títulos) + DM Sans (corpo)
- Cores: GREEN #28514D, GREEN_DEEP #1C3B38, BEIGE #E0DBC6, GOLD #BAA36C, OLIVE #968659
- CSS vars: --green, --green-deep, --beige, --beige-light, --gold, --gold-light, --olive, --dark, --white

## Funcionalidades interativas
1. Gate de email (captura nome/email antes de liberar conteúdo)
2. Autoavaliação de 8 disciplinas (notas 1-5, resultado automático)
3. Calculadora de pipeline (inputs → resultados em tempo real)
4. Download PDF dos resultados (jsPDF)
5. Tracker semanal de prospecção
6. Nav ativa via IntersectionObserver

## Kit (ConvertKit)
- Form ID: 9067445
- API Key pública: ACToNRKxQcIk8S6Brww_QA
- Chave pública por design da API — não é secret

## Git
- Branch: main (estático, push direto OK)
- Commits: conventional commits em inglês
