# RN02 - Campos Obrigatórios

**Módulo:** Checkout

**Aplicação:** [https://desafioqafadami.lovable.app/](https://desafioqafadami.lovable.app/)

**Tipo de teste:** Manual Funcional

**Ambiente:** Staging

---

## CT-005 — Validar preenchimento dos campos obrigatórios com dados válidos (Happy Path)

| Campo            | Detalhe                                             |
| ---------------- | --------------------------------------------------- |
| **Pré-condição** | Aplicação disponível e página de checkout carregada |
| **Prioridade**   | Alta                                                |
| **Tipo de Caso** | Positivo (Happy Path)                               |

**Passos:**

1. Acessar a página de checkout.
2. Preencher o campo **Nome Completo** com um nome válido.
3. Preencher o campo **CPF** com um CPF válido.
4. Preencher o campo **E-mail** com um e-mail válido.
5. Informar a quantidade igual a **1**.
6. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

O sistema deve aceitar o preenchimento dos campos obrigatórios e permitir o prosseguimento para a confirmação do pedido.

---

## CT-006 — Validar comportamento ao deixar um ou mais campos obrigatórios em branco (Negativo)

| Campo            | Detalhe              |
| ---------------- | -------------------- |
| **Pré-condição** | Checkout carregado   |
| **Prioridade**   | Alta                 |
| **Tipo de Caso** | Negativo (Validação) |

**Passos:**

1. Acessar o checkout.
2. Preencher apenas parte dos campos obrigatórios.
3. Deixar um ou mais dos seguintes campos em branco:

   * Nome Completo;
   * CPF;
   * E-mail;
   * Quantidade.
4. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

O sistema **não deve permitir** a continuidade do processo e deve informar claramente quais campos obrigatórios precisam ser preenchidos.

---

## CT-007 — Validar preenchimento dos campos obrigatórios com dados inválidos (Negativo)

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Alta               |
| **Tipo de Caso** | Negativo (Exceção) |

**Passos:**

1. Acessar o checkout.
2. Informar:

   * Nome contendo apenas espaços em branco;
   * CPF em formato inválido (caso exista validação);
   * E-mail em formato inválido (ex.: `teste@`);
   * Quantidade válida.
3. Clicar em **Finalizar Pedido**.

**Resultado esperado:**

O sistema deve impedir a continuidade da compra e apresentar mensagens de validação para os campos preenchidos com dados inválidos.

> **Observação:** caso a especificação não exija validação de formato para CPF e e-mail, esse teste pode ser utilizado como exploratório para identificar comportamentos inesperados.

---

## CT-008 — Validar consistência da obrigatoriedade dos campos durante o preenchimento (Consistência)

| Campo            | Detalhe            |
| ---------------- | ------------------ |
| **Pré-condição** | Checkout carregado |
| **Prioridade**   | Média              |
| **Tipo de Caso** | Consistência       |

**Passos:**

1. Preencher todos os campos obrigatórios.
2. Apagar o conteúdo do campo **Nome Completo**.
3. Verificar se o sistema identifica novamente o campo como obrigatório.
4. Repetir o procedimento para **CPF**, **E-mail** e **Quantidade**.
5. Tentar finalizar o pedido.

**Resultado esperado:**

Sempre que um campo obrigatório ficar vazio, o sistema deve impedir a finalização do pedido e indicar corretamente o(s) campo(s) pendente(s), mantendo esse comportamento de forma consistente durante todo o fluxo.

---


### Uma observação importante 

Há um detalhe interessante na **RN02**: ela diz apenas que os campos são **obrigatórios**, mas **não especifica regras de formato** para CPF ou e-mail. Em um contexto de testes, isso significa que:

* **CT-006** está diretamente ligado à regra de negócio (campos vazios).
* **CT-007** extrapola a especificação e entra como um teste de **validação exploratória**. Se o sistema aceitar um e-mail como `teste@` ou um CPF inválido, isso **não necessariamente é um bug da RN02**, a menos que exista outra regra ou requisito que exija essa validação. Vale a pena documentar esse tipo de achado como uma melhoria ou discutir com o PO, em vez de classificá-lo automaticamente como defeito. Essa distinção demonstra maturidade na análise de requisitos.


## Pontos de atenção para bug 
 
- Sistema permite finalizar o pedido mesmo com campo obrigatório vazio
- Mensagem de erro genérica ou ausente (usuário não sabe qual campo corrigir)
- Validação ocorre só no backend (delay perceptível) sem feedback visual imediato no campo
- Espaços em branco (" ") sendo aceitos como preenchimento válido
 
