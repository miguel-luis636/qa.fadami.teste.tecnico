# 🐞 Bug — Fechamento rápido do modal permite múltiplos cliques e múltiplos pedidos

> **ID:** BUG-20260728-009
> **Data identificada:** 28/07/2026
> **Tipo:** Funcional / Regra de negócio
> **Severidade:** S2 — Alto
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

Embora o modal de confirmação impeça o duplo clique direto no botão "Finalizar Pedido" enquanto está aberto, é possível fechar o modal rapidamente e clicar novamente no botão de compra, gerando múltiplos pedidos — o que contraria o objetivo central da RN06.

---

## 🔍 Descrição Detalhada

A RN06 exige que, ao clicar em "Finalizar Pedido", o sistema exiba um modal de confirmação **e desabilite o botão imediatamente** para evitar múltiplos envios por duplo clique. Na prática, o modal em si bloqueia cliques repetidos enquanto está aberto — porém o botão "Finalizar Pedido" na tela de fundo não é desabilitado. Isso permite que o usuário feche o modal de confirmação rapidamente (antes de concluir o fluxo) e clique novamente no botão de compra, resultando em múltiplos pedidos sendo processados.

Tecnicamente, o requisito de "modal exibido" é atendido, mas o requisito de "desabilitar o botão imediatamente" (a real proteção contra múltiplos envios) não é cumprido — o modal apenas mascara o problema em vez de resolvê-lo.

**Evidência (gravação em vídeo):** https://jam.dev/c/8e29b378-525c-425d-8555-495d91e5c0ca

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher os campos obrigatórios com dados válidos
3. Clicar em "Finalizar Pedido" — o modal de confirmação é exibido
4. Fechar o modal rapidamente (antes de qualquer ação de confirmação)
5. Clicar novamente em "Finalizar Pedido"
6. Repetir o processo algumas vezes

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Conforme RN06, o botão "Finalizar Pedido" deveria ser desabilitado **imediatamente** ao primeiro clique, independentemente do estado do modal (aberto, fechado ou cancelado), evitando que o usuário consiga disparar múltiplos pedidos mesmo fechando e reabrindo o modal.

## 🔎 Comportamento Atual

O botão "Finalizar Pedido" permanece habilitado por trás do modal. Fechando o modal rapidamente, é possível clicar no botão novamente e gerar múltiplos pedidos.

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

1. O estado de "desabilitado" foi implementado apenas na exibição do modal (via overlay/bloqueio visual), e não no estado real do elemento `button` do formulário
2. Falta de um estado de "processando"/"loading" persistente que sobreviva ao fechamento do modal

---

## 📊 Impacto

Risco direto de pedidos duplicados em um cenário real de produção, com possível cobrança/processamento múltiplo indevido para o mesmo cliente.

## 📝 Notas Adicionais

Reportado como bug (e não apenas como observação) porque o comportamento observado vai contra a intenção central da RN06 — a barreira existe apenas enquanto o modal está aberto, não de forma persistente como o requisito exige.
