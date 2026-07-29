# 🐞 Bug — Sistema finaliza pedido mesmo com Nome, CPF, E-mail e Quantidade todos inválidos simultaneamente

> **ID:** BUG-20260728-006
> **Data identificada:** 28/07/2026
> **Tipo:** Funcional / Validação de campos
> **Severidade:** S1 — Crítico
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

O sistema permite concluir o pedido mesmo quando todos os campos obrigatórios (Nome Completo, CPF, E-mail e Quantidade) são preenchidos com valores inválidos ao mesmo tempo, evidenciando a ausência total de uma camada de validação antes do submit.

---

## 🔍 Descrição Detalhada

Este cenário consolida a falha observada de forma isolada em outros bugs (BUG-20260728-002, 003 e 004): ao invalidar simultaneamente os quatro campos obrigatórios da RN02, nenhuma trava impede o avanço do fluxo. Isso indica que a validação, quando existe, não está centralizada nem é aplicada de forma consistente no momento da finalização.

**Evidência (gravação em vídeo):** https://jam.dev/c/837751d6-4dcb-45b6-ae9a-c62ca1b2878a

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher Nome Completo com um valor inválido/sem sentido
3. Preencher CPF com um valor inválido
4. Preencher E-mail com um valor sem estrutura válida
5. Preencher Quantidade com um valor fora dos limites da RN03 (ex.: 0 ou negativo)
6. Clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

O sistema deveria validar todos os campos obrigatórios (RN02) e a quantidade (RN03) antes de permitir a finalização, bloqueando o envio e sinalizando cada campo com problema.

## 🔎 Comportamento Atual

O pedido é finalizado normalmente, com o modal de confirmação sendo exibido mesmo com todos os campos inválidos.

---

## 🌍 Ambiente

| Campo | Valor |
|-------|-------|
| **Navegador** | Google Chrome/Brave (última versão) |
| **Sistema Operacional** | Windows 11 |
| **URL / Tela** | https://desafioqafadami.lovable.app/ — Checkout |
| **Device** | Desktop |

---

## 💡 Hipóteses sobre a origem do problema

1. Não existe uma camada única e centralizada de validação de formulário antes do clique em "Finalizar Pedido"
2. As poucas validações existentes (se houver) parecem checar apenas se o campo está vazio, não o formato/valor do dado

---

## 📊 Impacto

Evidência mais forte de que a validação de RN02 e RN03 é inexistente ou insuficiente em toda a jornada de checkout, não apenas em casos isolados.

## 🔗 Bugs relacionados

- BUG-20260728-002, BUG-20260728-003, BUG-20260728-004
