# RN04 - Cupons de Desconto

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-013 — Validar aplicação do cupom de desconto válido (Happy Path)

| Campo            | Detalhe                                             |
| ---------------- | --------------------------------------------------- |
| **Pré-condição** | Aplicação disponível e página de checkout carregada |
| **Prioridade**   | Alta                                                |
| **Tipo de Caso** | Positivo                               |

**Passos:**

1. Acessar a página de checkout.
2. Preencher todos os campos obrigatórios com dados válidos.
3. Informar uma quantidade válida (ex.: **2**).
4. Digitar o cupom **DESC10**.
5. Aplicar o cupom.

**Resultado esperado:**

* O sistema deve aceitar o cupom **DESC10**.
* Deve ser aplicado **10% de desconto** sobre o valor total do carrinho.
* O valor final deve ser atualizado corretamente.

---

## CT-014 — Validar rejeição de cupom inválido (Negativo)

| Campo            | Detalhe              |
| ---------------- | -------------------- |
| **Pré-condição** | Checkout carregado   |
| **Prioridade**   | Alta                 |
| **Tipo de Caso** | Negativo (Validação) |

**Passos:**

1. Acessar a página de checkout.
2. Informar um cupom inexistente (ex.: **TESTE10**).
3. Clicar em **Aplicar Cupom**.

**Resultado esperado:**

* O sistema não deve aplicar desconto.
* Deve ser exibida a mensagem:

> **"Cupom inválido"**

---

## CT-015 — Validar tratamento de variações do cupom válido (Negativo)

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Média              |
| **Tipo de Caso** | Negativo (Exceção) |

**Passos:**

1. Acessar a página de checkout.
2. Informar variações do cupom, por exemplo:

   * `desc10`
   * `Desc10`
   * `DESC10`
3. Aplicar cada uma das variações.

**Resultado esperado:**

Caso a regra de negócio exija correspondência exata com **DESC10**, o sistema deve rejeitar as variações e exibir a mensagem:

> **"Cupom inválido"**

> **Observação:** Se o sistema aceitar letras minúsculas ou espaços, esse comportamento deve ser validado junto ao requisito, pois a especificação não define sensibilidade a maiúsculas/minúsculas nem tratamento de espaços.

---

## CT-016 — Validar consistência da aplicação do desconto (Valor-Limite / Consistência)

| Campo            | Detalhe                     |
| ---------------- | --------------------------- |
| **Pré-condição** | Checkout carregado          |
| **Prioridade**   | Média                       |
| **Tipo de Caso** | Valor-Limite / Consistência |

**Passos:**

1. Informar a quantidade **1**.
2. Aplicar o cupom **DESC10**.
3. Verificar o valor total.
4. Alterar a quantidade para **5**.
5. Verificar novamente o valor total.
6. Alterar a quantidade para **10**.
7. Confirmar o valor apresentado após cada alteração.

**Resultado esperado:**

* O desconto de **10%** deve permanecer aplicado após a alteração da quantidade.

## Pontos de atenção para bug (foco de investigação)
 
- Desconto calculado incorretamente (ex.: 10% sobre valor unitário em vez do total do carrinho)
- Cupom sensível a caixa (case-sensitive) sem padronização, gerando inconsistência de UX
- Cupom aplicado múltiplas vezes acumula desconto (>10%)
- Arredondamento incorreto de centavos no cálculo do desconto
* O valor total deve ser recalculado corretamente sempre que a quantidade for modificada.
* O sistema não deve aplicar o desconto mais de uma vez nem removê-lo indevidamente.

---

## Distribuição dos casos

| Caso   | Categoria                      | Objetivo                                                               |
| ------ | ------------------------------ | ---------------------------------------------------------------------- |
| CT-013 | ✅ Positivo                     | Validar a aplicação correta do cupom **DESC10**                        |
| CT-014 | ❌ Negativo (Validação)         | Validar a rejeição de um cupom inexistente                             |
| CT-015 | ❌ Negativo (Exceção)           | Validar o tratamento de variações do cupom válido                      |
| CT-016 | ⚠️ Valor-Limite / Consistência | Validar que o desconto permanece correto após alterações na quantidade |

## Pontos de atenção para bug (foco de investigação)
 
- Desconto calculado incorretamente (ex.: 10% sobre valor unitário em vez do total do carrinho)
- Cupom sensível a caixa (case-sensitive) sem padronização, gerando inconsistência de UX
- Cupom aplicado múltiplas vezes acumula desconto (>10%)
- Arredondamento incorreto de centavos no cálculo do desconto

## Pontos de atenção para bug (foco de investigação)
 
- Mensagem de erro com texto diferente do especificado na RN04 (ex.: "Cupom não encontrado", "Erro")
- Sistema aplica desconto parcial ou zera o total por engano ao tentar validar cupom inválido
- Cupom vazio sendo tratado como cupom válido (sem mensagem nenhuma)
- Erro de cupom não é limpo da tela ao corrigir e digitar um cupom válido em seguida
 
  
