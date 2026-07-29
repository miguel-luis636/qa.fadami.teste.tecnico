# 🐞 Bug — Sistema aceita valores absurdos/fora do padrão nos campos do formulário

> **ID:** BUG-20260728-007
> **Data identificada:** 28/07/2026
> **Tipo:** Funcional / Validação de campos
> **Severidade:** S2 — Alto
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

Os campos do formulário de checkout não possuem limite de tamanho/tipo de caractere, aceitando valores absurdos (ex.: textos extremamente longos, caracteres especiais ou números fora de qualquer padrão esperado) sem qualquer bloqueio ou sanitização.

---

## 🔍 Descrição Detalhada

Durante a exploração dos campos do formulário, foi possível inserir valores muito além do que seria esperado para cada tipo de dado (ex.: nome com centenas de caracteres, caracteres especiais em campos que deveriam aceitar apenas texto/número), sem que o sistema aplicasse nenhum limite de tamanho (`maxlength`), tipo de caractere permitido, ou mensagem de alerta.

**Evidência (gravação em vídeo):** https://jam.dev/c/164c37c1-876e-4334-bf0e-22eb2c2ccb5d

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher os campos do formulário (Nome, CPF, E-mail, Quantidade) com valores excessivamente longos e/ou com caracteres especiais fora do padrão esperado para cada campo
3. Clicar em "Finalizar Pedido"

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Cada campo deveria ter um limite de tamanho e um conjunto de caracteres permitidos coerente com o tipo de dado esperado (ex.: nome apenas com letras e espaços dentro de um limite razoável de caracteres), rejeitando ou sanitizando entradas fora do padrão.

## 🔎 Comportamento Atual

O sistema aceita qualquer valor, de qualquer tamanho e composição de caracteres, sem nenhuma restrição perceptível.

---

## 🌍 Ambiente

| Campo | Valor |
|-------|-------|
| **Navegador** | Google Chrome/Brave (última versão) || **Sistema Operacional** | Windows 11 |
| **URL / Tela** | https://desafioqafadami.lovable.app/ — Checkout |
| **Device** | Desktop |

---

## 💡 Hipóteses sobre a origem do problema

1. Ausência de atributos `maxlength` e `pattern` nos inputs do formulário
2. Ausência de validação/sanitização no lado do servidor (se houver backend por trás do formulário)

---

## 📊 Impacto

Além do risco de dados inconsistentes, entradas sem sanitização podem representar um vetor de risco de segurança (ex.: XSS) caso os dados sejam renderizados sem tratamento em outra tela do sistema.
