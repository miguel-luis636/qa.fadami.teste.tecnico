# 🐞 Bug — Sistema conclui checkout aceitando CPF e E-mail em formatos inválidos

> **ID:** BUG-20260728-003
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

Não há validação de formato para os campos CPF e E-mail: o sistema aceita e finaliza o pedido mesmo quando esses campos são preenchidos com valores que não correspondem a um CPF ou e-mail válidos.

---

## 🔍 Descrição Detalhada

RN02 define os campos CPF e E-mail como obrigatórios, mas não especifica validação de formato. Na prática, o sistema trata a obrigatoriedade apenas como "não vazio" — qualquer sequência de caracteres é aceita nesses campos, sem checagem de dígito verificador de CPF ou de estrutura de e-mail (usuário@dominio).

**Evidência (gravação em vídeo):** https://jam.dev/c/2d3a2200-e919-40f7-acf8-939c72a9b0cd

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher o campo CPF com um número que não corresponde a um CPF válido (ex.: sequência aleatória de 11 dígitos)
3. Preencher o campo E-mail com um valor sem estrutura de e-mail válida
4. Preencher os demais campos normalmente
5. Clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

O sistema deveria validar o formato do CPF (11 dígitos + dígito verificador válido) e do E-mail (estrutura `usuario@dominio.tld`), bloqueando o envio e sinalizando o campo específico em caso de formato inválido.

## 🔎 Comportamento Atual

O pedido é aceito e finalizado normalmente, independentemente do CPF ou E-mail informados serem válidos ou não.

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

1. Validação de formato de CPF e e-mail não implementada, apenas checagem de campo "not empty"
2. Ausência de máscara/pattern de input para o campo CPF

---

## 📊 Impacto

Permite o registro de pedidos com dados de contato inutilizáveis, o que pode comprometer o envio de confirmação, nota fiscal e suporte pós-venda em um cenário real.
