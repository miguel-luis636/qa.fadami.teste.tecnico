# 🐞 Bug — Quantidade negativa combinada a cupom faz o valor do pedido aumentar em vez de diminuir

> **ID:** BUG-20260728-005
> 
>**Data identificada:** 28/07/2026
> 
> **Tipo:** Funcional / Cálculo de negócio
> 
> **Severidade:** S1 — Crítico
> 
> **Status:** 🔴 Aberto

---

## 📋 Resumo Executivo

Ao combinar uma Quantidade negativa com a aplicação do cupom de desconto DESC10, o valor total do pedido aumenta em vez de diminuir, contrariando diretamente a fórmula definida na RN05.

---

## 🔍 Descrição Detalhada

A RN05 define o cálculo do total como `(Quantidade * 50) - Desconto`. Como o sistema não bloqueia quantidades negativas (ver BUG-20260728-004), o resultado de `Quantidade * 50` se torna um valor negativo; ao subtrair o desconto (também calculado sobre esse valor negativo), o resultado matemático inverte o efeito esperado, fazendo o total exibido aumentar em vez de diminuir com a aplicação do cupom.

**Evidência (gravação em vídeo):** https://jam.dev/c/16b6e66c-1747-42fd-8d87-707dad7d51de

---

## 🔄 Passos para Reproduzir

1. Acessar https://desafioqafadami.lovable.app/
2. Preencher os campos obrigatórios com dados válidos
3. Inserir uma Quantidade negativa (ex.: -2)
4. Aplicar o cupom DESC10
5. Observar o valor total calculado antes e depois da aplicação do cupom

**Reprodutibilidade:** Consistente

---

## ✅ Comportamento Esperado

Independentemente do cupom, a Quantidade negativa já deveria ter sido bloqueada na entrada (RN03). Como salvaguarda adicional, o cálculo do total (RN05) nunca deveria resultar em um valor que aumenta com a aplicação de um desconto — o total pós-cupom deve ser sempre menor ou igual ao total pré-cupom.

## 🔎 Comportamento Atual

O valor total do pedido aumenta ao aplicar o cupom DESC10 quando a Quantidade é negativa, numa clara inversão da lógica de desconto esperada.

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

1. Causa raiz é a ausência de validação de Quantidade mínima (RN03) — este bug é consequência direta do BUG-20260728-004
2. Fórmula de cálculo (RN05) aplicada literalmente sem cláusula de proteção contra valores negativos

---

## 📊 Impacto

Bug de severidade crítica: permite gerar pedidos com valores financeiros incoerentes e potencialmente exploráveis, caso o sistema fosse conectado a um gateway de pagamento real.

## 🔗 Bugs relacionados

- BUG-20260728-004 — Sistema aceita finalização de pedido com Quantidade negativa
