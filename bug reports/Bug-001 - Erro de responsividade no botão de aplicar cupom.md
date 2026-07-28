# 🐞 Bug — Erro de responsividade no botão de aplicar cupom

> **ID:** BUG-20260728-001
> 
> **Data identificada:** 28/07/2026
> 
> **Tipo:** Usabilidade / UI / Responsividade
> 
> **Severidade:** S4 — Baixo
> 
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

O botão de aplicar cupom apresenta um problema de margem/espaçamento, quebrando o alinhamento visual do componente na tela de checkout.

---

## 🔍 Descrição Detalhada

Durante a exploração da tela de checkout, foi identificado que o botão responsável por aplicar o cupom de desconto (RN04) não respeita o espaçamento esperado em relação aos elementos vizinhos (campo de input do cupom e demais elementos do formulário), resultando em uma margem incorreta e quebra do alinhamento visual.

**Evidência (gravação em vídeo):** https://jam.dev/c/aef4f39b-e3a8-4824-ab0f-47385c021b81

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Rolar até o campo de cupom de desconto na tela de checkout
3. Observar o espaçamento/margem do botão de aplicar cupom em relação ao campo de input e demais elementos

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

O botão de aplicar cupom deveria manter alinhamento e espaçamento consistentes com os demais elementos do formulário, sem quebra de margem, mantendo a hierarquia visual do layout.

## 🔎 Comportamento Atual

O botão exibe uma margem incorreta, gerando uma quebra visual no alinhamento do componente, conforme evidenciado na gravação.

---

## 🌍 Ambiente

| Campo | Valor |
|-------|-------|
| **Navegador** | Google Chrome/Brave (última versão) |
| **Sistema Operacional** | Windows 11 |
| **URL / Tela** | https://desafioqafadami.lovable.app/ — Checkout, seção de cupom |
| **Device** | Desktop |

---

## 💡 Hipóteses sobre a origem do problema

1. CSS de margin/padding não ajustado para o container do botão
2. Possível ausência de teste de responsividade em diferentes resoluções durante o desenvolvimento

---

## 📝 Notas Adicionais

Bug de baixo impacto funcional (não bloqueia o fluxo de compra), mas afeta a percepção de qualidade e profissionalismo da interface.
