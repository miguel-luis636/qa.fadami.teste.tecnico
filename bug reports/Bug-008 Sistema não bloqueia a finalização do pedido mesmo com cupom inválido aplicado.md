# 🐞 Bug — Sistema não bloqueia a finalização do pedido mesmo com cupom inválido aplicado

> **ID:** BUG-20260728-008
> **Data identificada:** 28/07/2026
> **Tipo:** Funcional / Regra de negócio
> **Severidade:** S2 — Alto
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

Mesmo após o sistema exibir a mensagem "Cupom inválido" para um cupom diferente de DESC10 (RN04), o botão "Finalizar Pedido" permanece habilitado e permite concluir a compra normalmente.

---

## 🔍 Descrição Detalhada

A RN04 estabelece que qualquer cupom diferente de DESC10 deve exibir a mensagem "Cupom inválido". A mensagem de fato é exibida corretamente, porém isso não impede o avanço do fluxo: o usuário consegue clicar em "Finalizar Pedido" e concluir a compra mesmo com o erro de cupom visível na tela, sem ser obrigado a corrigir ou remover o cupom inválido antes de prosseguir.

**Evidência (gravação em vídeo):** https://jam.dev/c/a3b00c91-218c-438f-b67f-bcc40ba1a582

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher os campos obrigatórios com dados válidos
3. Inserir um cupom diferente de DESC10 (ex.: "ABC123")
4. Confirmar que a mensagem "Cupom inválido" é exibida
5. Sem corrigir o cupom, clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Ao detectar um cupom inválido, o sistema deveria impedir a finalização do pedido enquanto o campo de cupom permanecer com um valor inválido — seja bloqueando o botão "Finalizar Pedido", seja exigindo que o usuário remova/corrija o cupom antes de prosseguir.

## 🔎 Comportamento Atual

A mensagem de erro é apenas informativa; o botão "Finalizar Pedido" continua habilitado e a compra é concluída normalmente mesmo com o cupom inválido preenchido.

---

## 🌍 Ambiente

| Campo | Valor |
|-------|-------|
| **Navegador** | Google Chrome (última versão) |
| **Sistema Operacional** | Windows 11 |
| **URL / Tela** | https://desafioqafadami.lovable.app/ — Checkout |
| **Device** | Desktop |

---

## 💡 Hipóteses sobre a origem do problema

1. A validação do cupom (RN04) está desacoplada da lógica que habilita/desabilita o botão de finalização
2. Mensagem de erro tratada apenas como feedback visual, sem impacto no estado do formulário

---

## 📊 Impacto

Gera inconsistência entre o feedback visual (erro exibido) e o resultado real da ação (pedido aceito), podendo confundir o usuário sobre se o cupom foi ou não considerado no valor final.
