# 🐞 Bug — Sistema aceita finalização de pedido com Quantidade = 0, CPF inválido e E-mail vazio

> **ID:** BUG-20260728-002
> 
> **Data identificada:** 28/07/2026
> 
> **Tipo:** Funcional / Validação de campos
> 
> **Severidade:** S1 — Crítico
> 
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

O sistema permite finalizar um pedido mesmo com a Quantidade definida como 0, o CPF preenchido incorretamente e o campo E-mail deixado em branco, violando diretamente as RN02 (campos obrigatórios) e RN03 (quantidade mínima de 1).

---

## 🔍 Descrição Detalhada

Ao preencher o formulário de checkout com Quantidade = 0, um CPF em formato/valor inválido e deixando o campo E-mail vazio, o sistema não bloqueou o envio do pedido nem exibiu mensagens de validação para nenhum dos três campos, permitindo que o fluxo prosseguisse até a finalização.

**Dados utilizados no teste (fictícios):**
- Nome: `Maria testando qa`
- CPF: `928.054.200-12` (formato inválido / não corresponde a um CPF válido)
- E-mail: *(campo vazio)*
- Quantidade: `0`

**Evidência (gravação em vídeo):** https://jam.dev/c/2d3a2200-e919-40f7-acf8-939c72a9b0cd

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher o campo Nome Completo normalmente
3. Preencher o campo CPF com um valor inválido
4. Deixar o campo E-mail em branco
5. Definir a Quantidade como 0
6. Clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Conforme RN02, os campos Nome Completo, CPF, E-mail e Quantidade são obrigatórios — o sistema deveria bloquear o envio e sinalizar visualmente os campos pendentes/inválidos. Conforme RN03, a quantidade mínima permitida é 1; Quantidade = 0 deveria ser rejeitada.

## 🔎 Comportamento Atual

O sistema aceita o pedido e permite prosseguir com a finalização mesmo com E-mail vazio, CPF inválido e Quantidade zerada.

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

1. Ausência de validação de obrigatoriedade no frontend antes do submit
2. Validação de quantidade mínima (RN03) não implementada ou não aplicada no momento do clique em "Finalizar Pedido"
3. Falta de validação de formato/existência de CPF

---

## 📊 Impacto

Compromete diretamente a integridade dos dados do pedido e a confiabilidade das regras de negócio RN02 e RN03, podendo gerar pedidos inconsistentes em produção.
