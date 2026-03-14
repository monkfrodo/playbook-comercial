# Playbook Comercial Íntegros

Lead magnet interativo para o negócio Íntegros — autoavaliação comercial + calculadora de pipeline com captura de e-mail via Kit (ConvertKit).

## Stack

- HTML/CSS/JS vanilla (arquivo único)
- jsPDF 2.5.2 (CDN) para download de resultados
- Kit (ConvertKit) API para captura de leads
- Deploy: Vercel (estático)
- Domínio: playbook.integros.org

## Estrutura

```
playbook-comercial.html  ← arquivo principal (tudo aqui)
vercel.json              ← config de deploy (rewrite)
CLAUDE.md                ← instruções para agentes
```

## Funcionalidades

1. Gate de e-mail (captura nome/email antes de liberar conteúdo)
2. Autoavaliação de 8 disciplinas comerciais (notas 1-5)
3. Calculadora de pipeline (inputs → resultados em tempo real)
4. Download PDF dos resultados
5. Tracker semanal de prospecção
6. Navegação ativa via IntersectionObserver

## Como rodar localmente

Abrir `playbook-comercial.html` no navegador. Não precisa de servidor.
