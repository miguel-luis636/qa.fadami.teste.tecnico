# Relatório de Execução dos Testes

**Projeto:** Desafio Técnico QA Júnior — Checkout (Fadami)

**Aplicação:** https://desafioqafadami.lovable.app/

**Ambiente:** Staging

**Tipo de Teste:** Manual Funcional

**Responsável:** Miguel Luis

**Data:** Julho/2026

---

# Resumo da Execução

| Status           | Quantidade |
| ---------------- | ---------: |
| ✅ Passou         |         15 |
| ❌ Falhou         |          8 |
| ⏸️ Não executado |          1 |
| **Total**        |     **24** |
---

# Resultado da Execução

## RN01 - Produto e Valor

| ID     | Caso de Teste                                                         |      Status      | Observações                                 |
| ------ | --------------------------------------------------------------------- | :--------------: | ------------------------------------------- |
| CT-001 | Validar exibição correta do produto e do valor unitário               |     ✅ Passou     | Produto e valor exibidos corretamente.      |
| CT-002 | Validar que o valor unitário não é alterado ao modificar a quantidade |     ✅ Passou     | Valor unitário permaneceu fixo em R$ 50,00. |
| CT-003 | Validar que não é possível adicionar outro produto ao checkout        | ⏸️ Não executado | Cenário não contemplado durante a execução. |
| CT-004 | Validar consistência do valor unitário durante todo o fluxo           |     ✅ Passou     | Valor permaneceu consistente.               |

---

## RN02 - Campos Obrigatórios

| ID     | Caso de Teste               |  Status  | Observações                                                            |
| ------ | --------------------------- | :------: | ---------------------------------------------------------------------- |
| CT-005 | Dados válidos               | ✅ Passou | Fluxo executado normalmente.                                           |
| CT-006 | Campos obrigatórios vazios  | ❌ Falhou | O sistema permite finalizar a compra com quantidade igual a 0.         |
| CT-007 | Dados inválidos             | ❌ Falhou | Sistema aceita CPF e e-mail inválidos e permite finalizar a compra.    |
| CT-008 | Consistência das validações | ❌ Falhou | Campo Quantidade não possui validação nem mensagem de obrigatoriedade. |

---

## RN03 - Limites de Quantidade

| ID     | Caso de Teste                 |  Status  | Observações                                                                                |
| ------ | ----------------------------- | :------: | ------------------------------------------------------------------------------------------ |
| CT-009 | Quantidade válida             | ✅ Passou | Funcionamento esperado.                                                                    |
| CT-010 | Quantidade inferior ao mínimo | ❌ Falhou | Quantidade igual a 0 é aceita.                                                             |
| CT-011 | Quantidade superior ao máximo | ❌ Falhou | Não existe validação para limite máximo.                                                   |
| CT-012 | Valores limite                | ✅ Passou | Valores válidos funcionam corretamente, porém inexistem validações para valores inválidos. |

---

## RN04 - Cupons de Desconto

| ID     | Caso de Teste            |  Status  | Observações                                                       |
| ------ | ------------------------ | :------: | ----------------------------------------------------------------- |
| CT-013 | Cupom válido             | ✅ Passou | Desconto aplicado corretamente.                                   |
| CT-014 | Cupom inválido           | ❌ Falhou | Sistema informa cupom inválido, porém permite finalizar o pedido. |
| CT-015 | Variações do cupom       | ✅ Passou | Comportamento conforme implementação atual.                       |
| CT-016 | Consistência do desconto | ✅ Passou | Recalcula corretamente o desconto.                                |

---

## RN05 - Cálculo do Total

| ID     | Caso de Teste           |  Status  | Observações                           |
| ------ | ----------------------- | :------: | ------------------------------------- |
| CT-017 | Total sem desconto      | ✅ Passou | Cálculo correto.                      |
| CT-018 | Total com desconto      | ✅ Passou | Desconto aplicado corretamente.       |
| CT-019 | Cupom inválido          | ✅ Passou | Não aplica desconto.                  |
| CT-020 | Consistência do cálculo | ✅ Passou | Recalcula corretamente o valor final. |

---

## RN06 - Finalização do Pedido

| ID     | Caso de Teste                      |  Status  | Observações                                                                                                       |
| ------ | ---------------------------------- | :------: | ----------------------------------------------------------------------------------------------------------------- |
| CT-021 | Finalização com sucesso            | ✅ Passou | Modal exibido corretamente.                                                                                       |
| CT-022 | Múltiplos cliques                  | ✅ Passou | Enquanto o modal permanece aberto o envio é impedido.                                                             |
| CT-023 | Finalização sem atender requisitos | ❌ Falhou | Sistema permite finalizar pedidos inválidos.                                                                      |
| CT-024 | Consistência do botão              | ❌ Falhou | O botão não é desabilitado conforme especificado na RN06, permitindo múltiplos envios após o fechamento do modal. |

---

# Índice de Rastreabilidade (RN → CT → BUG)

| RN        | Casos de Teste                 | Bugs Relacionados                  |
| --------- | ------------------------------ | ---------------------------------- |
| RN01      | CT-001, CT-002, CT-003, CT-004 | —                                  |
| RN02      | CT-005, CT-006, CT-007, CT-008 | BUG-002, BUG-003, BUG-006, BUG-007 |
| RN03      | CT-009, CT-010, CT-011, CT-012 | BUG-002, BUG-004, BUG-005, BUG-007 |
| RN04      | CT-013, CT-014, CT-015, CT-016 | BUG-008                            |
| RN05      | CT-017, CT-018, CT-019, CT-020 | BUG-005                            |
| RN06      | CT-021, CT-022, CT-023, CT-024 | BUG-006, BUG-009                   |
| Interface | Testes exploratórios           | BUG-001                            |
| Aplicação | Testes exploratórios           | BUG-010                            |

---

# Resumo dos Bugs Encontrados

| Bug     | Resumo                                                                      | Severidade | Possível Causa Raiz                                                                                                                    |
| ------- | --------------------------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| BUG-001 | Problema de responsividade no botão de aplicar cupom                        | Baixa      | Falha de CSS/Layout responsivo (margin/padding inadequados).                                                                           |
| BUG-002 | Sistema permite pedido com quantidade 0, CPF inválido e e-mail vazio        | Crítica    | Ausência de validações no frontend e/ou backend.                                                                                       |
| BUG-003 | Sistema aceita CPF e e-mail inválidos                                       | Alta       | Falta de validação de formato dos campos.                                                                                              |
| BUG-004 | Sistema aceita quantidade negativa                                          | Crítica    | Ausência de validação numérica e de limite mínimo.                                                                                     |
| BUG-005 | Quantidade negativa combinada com cupom altera incorretamente o valor final | Crítica    | Falha na validação da quantidade antes do cálculo do desconto.                                                                         |
| BUG-006 | Pedido finalizado com todos os campos inválidos                             | Crítica    | Fluxo de validação não bloqueia o envio do formulário.                                                                                 |
| BUG-007 | Campos aceitam valores extremamente altos                                   | Alta       | Ausência de limites de tamanho e validação dos inputs.                                                                                 |
| BUG-008 | Cupom inválido não impede a finalização da compra                           | Média      | Regra de negócio aplicada apenas visualmente, sem impedir o fluxo.                                                                     |
| BUG-009 | Botão "Finalizar Pedido" permanece habilitado após o clique                 | Alta       | Implementação parcial da RN06. O modal impede parcialmente o duplo envio, porém o botão nunca é desabilitado.                          |
| BUG-010 | Temporizador da prova é reiniciado ao atualizar a página                    | Média      | O estado do temporizador provavelmente é mantido apenas no cliente (frontend), sem persistência em armazenamento local ou no servidor. |

---

# Observação sobre o "BUG-010"

Durante a execução foi identificado um comportamento não relacionado diretamente às regras de negócio do checkout, mas que pode impactar a confiabilidade do ambiente de avaliação.

Ao atualizar a página (F5), **o cronômetro da prova é reiniciado**, permitindo reiniciar a contagem de tempo.

Embora esse comportamento provavelmente não faça parte do escopo funcional do desafio, ele representa uma inconsistência do ambiente de prova e pode comprometer o controle do tempo disponível para execução do teste técnico.

A execução completa deste desafio foi realizada em aproximadamente **1 hora a 1 hora e 30 minutos**, incluindo planejamento, elaboração dos casos de teste, execução dos cenários e testes exploratórios. Caso um candidato atualize a página durante a avaliação, o reinício do temporizador pode gerar inconsistências no tempo efetivamente utilizado e dificultar o acompanhamento da duração real da prova.

---

# Análise Geral

Os defeitos encontrados concentram-se principalmente em **validações de entrada**, **cumprimento das regras de negócio** e **controle do fluxo de finalização**.

Grande parte dos problemas possui uma mesma causa técnica: **ausência ou implementação incompleta das validações dos campos do formulário**, permitindo que dados inconsistentes avancem pelo fluxo da aplicação.

A correção dessas validações tende a eliminar diversos defeitos simultaneamente, reduzindo riscos de:

* registros inválidos;
* inconsistência dos dados;
* cálculos incorretos;
* pedidos inválidos;
* múltiplos envios do mesmo pedido.

---

# Observação baseada nos princípios de teste (CTFL)

De acordo com os princípios de teste definidos no **ISTQB Certified Tester Foundation Level (CTFL)**, é importante destacar três conceitos relevantes para a análise dos resultados obtidos.

## 1. Testes mostram a presença de defeitos, não a sua ausência

Durante a execução dos testes foram identificados diversos defeitos no sistema. Entretanto, isso não significa que todos os problemas existentes tenham sido encontrados. Os testes apenas demonstram a presença de defeitos nos cenários executados.

## 2. Teste exaustivo é impossível

Não é possível testar todas as combinações de entradas, estados e fluxos de uma aplicação. Assim, mesmo após a execução dos cenários documentados neste relatório, ainda podem existir defeitos não identificados.

## 3. Falácia da ausência de erros

Mesmo que todos os bugs encontrados sejam corrigidos, isso não garante automaticamente que o sistema esteja completamente livre de falhas ou que atenda plenamente às necessidades dos usuários. A qualidade também depende da aderência às regras de negócio e aos requisitos especificados.

Além disso, durante a análise foram identificados potenciais riscos relacionados à ausência de validações de entrada, permitindo registros inconsistentes e pedidos inválidos.

A implementação adequada das validações dos campos obrigatórios, das regras de quantidade, dos limites numéricos e do fluxo de finalização tende a corrigir diversos defeitos simultaneamente. Dessa forma, a correção de determinadas validações não resolve apenas um bug isolado, mas também reduz efeitos colaterais como inconsistência dos dados, cálculos incorretos, múltiplos envios e falhas em funcionalidades futuras.

