# 🐞 Bug — Sistema aceita finalização de pedido com Quantidade negativa

> **ID:** BUG-20260728-004
> 
> **Data identificada:** 28/07/2026
> 
> **Tipo:** Funcional / Regra de negócio
> 
> **Severidade:** S1 — Crítico
> 
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

O campo Quantidade aceita valores negativos e permite a finalização do pedido, violando diretamente a RN03 (quantidade mínima permitida é 1).

---

## 🔍 Descrição Detalhada

Ao inserir um valor negativo (ex.: -1) no campo Quantidade, o sistema não bloqueia a ação nem exibe mensagem de erro, permitindo que o pedido seja finalizado com uma quantidade que não faz sentido de negócio.

**Evidência (gravação em vídeo):** https://jam.dev/c/590e699a-59f7-46e6-b2c8-8f33c2ad8ea8

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher os campos obrigatórios com dados válidos
3. No campo Quantidade, inserir um valor negativo (ex.: -1)
4. Clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Conforme RN03, a quantidade mínima permitida é 1. O sistema deveria bloquear valores negativos no campo Quantidade, seja impedindo a digitação, seja validando no submit.

## 🔎 Comportamento Atual

O sistema aceita a quantidade negativa e permite a finalização do pedido normalmente.

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

1. Campo de input do tipo numérico sem atributo `min="1"` ou validação equivalente
2. Ausência de validação de regra de negócio (RN03) no momento do cálculo/submit

---

## 📊 Impacto

Quantidade negativa combinada ao cálculo do total (RN05) pode gerar valores incorretos ou incoerentes (ver BUG-20260728-005), representando risco direto à integridade financeira do pedido.
