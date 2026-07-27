# RN06 - Finalização do Pedido

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-021 — Validar finalização do pedido com sucesso (Happy Path)

| Campo            | Detalhe                                                    |
| ---------------- | ---------------------------------------------------------- |
| **Pré-condição** | Todos os campos obrigatórios preenchidos com dados válidos |
| **Prioridade**   | Alta                                                       |
| **Tipo de Caso** | Positivo (Happy Path)                                      |

**Passos:**

1. Acessar a página de checkout.
2. Preencher todos os campos obrigatórios com dados válidos.
3. Informar uma quantidade válida.
4. Aplicar um cupom válido (opcional).
5. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

* O sistema deve exibir um **modal de confirmação**.
* O modal deve apresentar um **resumo do pedido**, contendo as informações da compra.
* O botão **Finalizar Pedido** deve ser desabilitado imediatamente após o clique.

---

## CT-022 — Validar que não é possível realizar múltiplos envios através de cliques consecutivos (Negativo)

| Campo            | Detalhe                                               |
| ---------------- | ----------------------------------------------------- |
| **Pré-condição** | Todos os campos obrigatórios preenchidos corretamente |
| **Prioridade**   | Alta                                                  |
| **Tipo de Caso** | Negativo (Validação)                                  |

**Passos:**

1. Preencher todos os campos obrigatórios.
2. Clicar rapidamente várias vezes no botão **Finalizar Pedido**.
3. Observar o comportamento da aplicação.

**Resultado esperado:**

* O sistema deve processar apenas **uma única solicitação**.
* O botão deve ser desabilitado imediatamente após o primeiro clique.
* Não devem ser exibidos múltiplos modais nem ocorrer múltiplos envios do pedido.

---

## CT-023 — Validar comportamento ao tentar finalizar o pedido sem atender às condições necessárias (Negativo)

| Campo            | Detalhe                      |
| ---------------- | ---------------------------- |
| **Pré-condição** | Página de checkout carregada |
| **Prioridade**   | Alta                         |
| **Tipo de Caso** | Negativo (Exceção)           |

**Passos:**

1. Deixar um ou mais campos obrigatórios sem preenchimento.
2. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

* O sistema não deve exibir o modal de confirmação.
* O pedido não deve ser enviado.
* O usuário deve ser informado sobre os campos obrigatórios pendentes.

---

## CT-024 — Validar consistência do botão e do modal durante a finalização do pedido (Valor-Limite / Consistência)

| Campo            | Detalhe                                               |
| ---------------- | ----------------------------------------------------- |
| **Pré-condição** | Todos os campos obrigatórios preenchidos corretamente |
| **Prioridade**   | Média                                                 |
| **Tipo de Caso** | Valor-Limite / Consistência                           |

**Passos:**

1. Preencher todos os campos obrigatórios.
2. Clicar em **Finalizar Pedido**.
3. Verificar se o botão é desabilitado imediatamente.
4. Verificar se o modal apresenta corretamente o resumo do pedido.
5. Fechar o modal (caso a funcionalidade exista).
6. Observar o estado do botão e da tela após o fechamento.

**Resultado esperado:**

* O botão deve permanecer com o comportamento esperado durante todo o processo de finalização.
* O modal deve exibir corretamente as informações do pedido.
* O sistema não deve permitir estados inconsistentes, como reenvio indevido do pedido ou múltiplos modais.

---

## Pontos de atenção para bug (foco de investigação)
 
- Botão não desabilita a tempo, permitindo duplo envio em cliques muito rápidos (race condition)
- Modal de confirmação abre múltiplas vezes sobrepostas em caso de duplo clique
- Resumo do modal não reflete o cupom aplicado ou mostra o total sem desconto
- Botão volta a ficar habilitado indevidamente após fechar o modal, sem reset do formulário
 
