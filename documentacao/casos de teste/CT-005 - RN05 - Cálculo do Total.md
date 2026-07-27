# RN05 - Cálculo do Total

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-017 — Validar cálculo do valor total sem desconto (Happy Path)

| Campo            | Detalhe                                             |
| ---------------- | --------------------------------------------------- |
| **Pré-condição** | Aplicação disponível e página de checkout carregada |
| **Prioridade**   | Alta                                                |
| **Tipo de Caso** | Positivo (Happy Path)                               |

**Passos:**

1. Acessar a página de checkout.
2. Informar uma quantidade igual a **2**.
3. Não aplicar nenhum cupom de desconto.
4. Observar o valor total apresentado.

**Resultado esperado:**

O sistema deve calcular corretamente o valor total da compra.

**Cálculo esperado:**

* Quantidade: **2**
* Valor unitário: **R$ 50,00**
* Desconto: **R$ 0,00**
* **Total esperado: R$ 100,00**

---

## CT-018 — Validar cálculo do total após aplicação do cupom DESC10 (Negativo)

| Campo            | Detalhe              |
| ---------------- | -------------------- |
| **Pré-condição** | Checkout carregado   |
| **Prioridade**   | Alta                 |
| **Tipo de Caso** | Negativo (Validação) |

**Passos:**

1. Informar a quantidade **4**.
2. Aplicar o cupom **DESC10**.
3. Observar o valor final apresentado.

**Resultado esperado:**

O sistema deve calcular corretamente o desconto de **10%** sobre o valor total.

**Cálculo esperado:**

* Valor bruto: **R$ 200,00**
* Desconto: **R$ 20,00**
* **Total esperado: R$ 180,00**

Caso o sistema apresente qualquer valor diferente, o comportamento deve ser considerado incorreto.

---

## CT-019 — Validar que o sistema não aplica desconto para cupom inválido (Negativo)

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Alta               |
| **Tipo de Caso** | Negativo (Exceção) |

**Passos:**

1. Informar a quantidade **3**.
2. Aplicar o cupom **TESTE10**.
3. Observar o valor final apresentado.

**Resultado esperado:**

O sistema não deve aplicar qualquer desconto.

**Cálculo esperado:**

* Valor bruto: **R$ 150,00**
* Desconto: **R$ 0,00**
* **Total esperado: R$ 150,00**

Além disso, deve ser exibida a mensagem:

> **"Cupom inválido"**

---

## CT-020 — Validar consistência do cálculo do total após alterações na quantidade e no cupom (Valor-Limite / Consistência)

| Campo            | Detalhe                     |
| ---------------- | --------------------------- |
| **Pré-condição** | Checkout carregado          |
| **Prioridade**   | Média                       |
| **Tipo de Caso** | Valor-Limite / Consistência |

**Passos:**

1. Informar a quantidade **1**.
2. Aplicar o cupom **DESC10**.
3. Verificar o valor total.
4. Alterar a quantidade para **10**.
5. Verificar novamente o valor total.
6. Remover o cupom, caso a aplicação permita.
7. Confirmar que o valor total é recalculado corretamente após cada alteração.

**Resultado esperado:**

O sistema deve recalcular corretamente o valor total sempre que houver alteração na quantidade ou na aplicação/remoção do cupom, mantendo consistência em todas as operações.

Exemplos esperados:

| Quantidade | Cupom     | Total Esperado |
| ---------- | --------- | -------------- |
| 1          | DESC10    | **R$ 45,00**   |
| 10         | DESC10    | **R$ 450,00**  |
| 10         | Sem cupom | **R$ 500,00**  |

---

## Pontos de atenção para bug (foco de investigação)
 
- Total não recalcula automaticamente ao alterar a quantidade depois de aplicar o cupom (fica com valor "preso")
- Erro de ponto flutuante gerando centavos incorretos (ex.: R$ 179,99 em vez de R$ 180,00)
- Desconto aplicado sobre o valor errado (unitário em vez do total, ou vice-versa)
- Total exibido não reflete o valor realmente enviado no resumo do modal de confirmação (RN06)
