# RN03 - Limites de Quantidade

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-009 — Validar seleção de quantidade dentro do limite permitido

| Campo            | Detalhe                                             |
| ---------------- | --------------------------------------------------- |
| **Pré-condição** | Aplicação disponível e página de checkout carregada |
| **Prioridade**   | Alta                                                |
| **Tipo de Caso** | Positivo                           |

**Passos:**

1. Acessar a página de checkout.
2. Informar uma quantidade válida (ex.: **5**).
3. Preencher os demais campos obrigatórios com dados válidos.
4. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

O sistema deve aceitar a quantidade informada e permitir o prosseguimento da compra.

---

## CT-010 — Validar tentativa de informar quantidade inferior ao mínimo permitido (Negativo)

| Campo            | Detalhe              |
| ---------------- | -------------------- |
| **Pré-condição** | Checkout carregado   |
| **Prioridade**   | Alta                 |
| **Tipo de Caso** | Negativo (Validação) |

**Passos:**

1. Acessar a página de checkout.
2. Informar a quantidade **0**.
3. Preencher os demais campos obrigatórios.
4. Tentar finalizar o pedido.

**Resultado esperado:**

O sistema deve impedir a continuidade da compra e informar que a quantidade mínima permitida é **1**.

---

## CT-011 — Validar tentativa de informar quantidade superior ao máximo permitido (Negativo)

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Alta               |
| **Tipo de Caso** | Negativo (Exceção) |

**Passos:**

1. Acessar a página de checkout.
2. Informar a quantidade **11**.
3. Preencher os demais campos obrigatórios.
4. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

O sistema deve impedir a continuidade da compra e informar que a quantidade máxima permitida é **10**.

---

## CT-012 — Validar os valores-limite da quantidade 

| Campo            | Detalhe                     |
| ---------------- | --------------------------- |
| **Pré-condição** | Checkout carregado          |
| **Prioridade**   | Média                       |
| **Tipo de Caso** | Valor-Limite / Consistência |

**Passos:**

1. Informar a quantidade **1** e verificar o comportamento do sistema.
2. Informar a quantidade **10** e verificar o comportamento do sistema.
3. Confirmar que ambas as quantidades são aceitas.
4. Verificar se o cálculo do total é atualizado corretamente em ambos os casos.

**Resultado esperado:**

O sistema deve aceitar as quantidades **1** e **10**, respeitando os limites definidos pela regra de negócio e atualizando corretamente o valor total da compra.

---

# Pontos de atenção para bug (foco de investigação)
 
- Sistema aceita Quantidade = 0 e calcula total R$ 0,00 (falha de validação de limite)
- Sistema aceita valores negativos e gera total negativo
- Campo de quantidade aceita números decimais (ex.: 1,5) sem tratamento
- Botão "-" (decrementar), se existir, permite ir abaixo de 1
