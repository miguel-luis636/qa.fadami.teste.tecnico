# 🐞 Bug — Temporizador da prova é resetado ao atualizar a página

> **ID:** BUG-20260728-010
> **Data identificada:** 28/07/2026
> **Tipo:** Observação Geral / Ambiente da Prova
> **Severidade:** S3 — Médio
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

O temporizador geral da prova (contagem de tempo da avaliação) é reiniciado sempre que a página é atualizada (F5/refresh), em vez de manter a contagem persistente a partir do início real da prova.

---

## 🔍 Descrição Detalhada

Ao atualizar a página durante a execução da prova, o cronômetro volta a contar do zero (ou do valor total original), em vez de refletir o tempo real já decorrido desde o clique em "Iniciar Prova". Isso não afeta diretamente as regras de negócio do checkout (RN01–RN06), mas é uma inconsistência no controle de tempo da própria avaliação, o que pode ser explorado (intencionalmente ou não) para estender o tempo disponível.

Não há um link de evidência em vídeo para este item — foi identificado durante a navegação geral, e não está associado a uma regra de negócio específica do formulário.

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/ e clicar em "Iniciar Prova"
2. Aguardar alguns instantes com o temporizador em contagem
3. Atualizar a página (F5)
4. Observar o valor exibido no temporizador

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

O temporizador deveria persistir o tempo já decorrido (ex.: via armazenamento local ou timestamp de início vinculado ao servidor), continuando a contagem corretamente após um refresh da página.

## 🔎 Comportamento Atual

O temporizador reinicia a contagem ao atualizar a página, desconsiderando o tempo já utilizado.

---

## 🌍 Ambiente

| Campo | Valor |
|-------|-------|
| **Navegador** | Google Chrome (última versão) |
| **Sistema Operacional** | Windows 11 |
| **URL / Tela** | https://desafioqafadami.lovable.app/ — Tela geral da prova |
| **Device** | Desktop |

---

## 💡 Hipóteses sobre a origem do problema

1. O temporizador provavelmente é controlado apenas em estado local (client-side), sem persistência (ex.: `localStorage`/`sessionStorage`) nem vínculo com um timestamp de início armazenado no servidor

---

## 📝 Notas Adicionais

Este item foi registrado por transparência e boas práticas de QA, ainda que não esteja diretamente ligado às regras de negócio RN01–RN06 avaliadas no desafio. Execução e exploração completa dos testes levou aproximadamente 1h–1h30.
