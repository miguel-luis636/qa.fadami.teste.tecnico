# RN01 - Produto e Valor

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-001 — Validar exibição correta do produto e do valor unitário 

| Campo            | Detalhe                                             |
| ---------------- | --------------------------------------------------- |
| **Pré-condição** | Aplicação disponível e página de checkout carregada |
| **Prioridade**   | Alta                                                |
| **Tipo de Caso** | Positivo                                |

**Passos:**

1. Acessar a aplicação.
2. Navegar até a página de checkout.
3. Verificar o produto apresentado.
4. Verificar o valor unitário exibido.

**Resultado esperado:**

* O checkout deve apresentar apenas o produto **"Curso de Teste de Software"**.
* O valor unitário deve ser **R$ 50,00**.

---

## CT-002 — Validar que o valor unitário não é alterado ao modificar a quantidade

| Campo            | Detalhe              |
| ---------------- | -------------------- |
| **Pré-condição** | Checkout carregado   |
| **Prioridade**   | Alta                 |
| **Tipo de Caso** | Negativo  |

**Passos:**

1. Acessar o checkout.
2. Alterar a quantidade para 2.
3. Alterar para 5.
4. Alterar para 10.
5. Observar o valor unitário apresentado.

**Resultado esperado:**

O sistema **não deve alterar o valor unitário** ao modificar a quantidade.

O valor unitário deve permanecer **R$ 50,00** em todas as alterações.

---

## CT-003 — Validar que não é possível adicionar outro produto ao checkout 

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Média              |
| **Tipo de Caso** | Negativo  |

**Passos:**

1. Acessar o checkout.
2. Verificar os produtos disponíveis.
3. Procurar botão, link ou opção para adicionar outro produto ao carrinho.
4. Caso exista alguma opção, tentar adicionar um novo produto.

**Resultado esperado:**

O sistema **não deve permitir adicionar outro produto**, mantendo apenas o produto **"Curso de Teste de Software"** durante todo o fluxo de checkout.

---

## CT-004 — Validar consistência do valor unitário durante todo o fluxo de compra

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Média              |
| **Tipo de Caso** | Consistência       |

**Passos:**

1. Preencher todos os campos obrigatórios.
2. Alterar a quantidade.
3. Aplicar um cupom válido.
4. Remover o cupom.
5. Alterar novamente a quantidade.
6. Observar o valor unitário durante todo o processo.

**Resultado esperado:**

O valor unitário deve permanecer **R$ 50,00** durante todo o fluxo de compra, independentemente da alteração da quantidade, aplicação ou remoção de cupom ou preenchimento dos campos do formulário.

## Pontos de atenção para bug (foco de investigação)
 
- Formatação incorreta do valor (ex.: "50", "R$50.00", "R$ 50" sem casas decimais)
- Nome do produto divergente do especificado na RN01
- Valor unitário hardcoded incorretamente no front-end (ex.: R$ 500,00 por erro de casa decimal)
