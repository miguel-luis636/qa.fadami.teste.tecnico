# Mini Plano de Testes — Checkout QA Júnior (Desafio Fadami)

## 1. Identificação

| Campo                         | Detalhes                              |
| ----------------------------- | ------------------------------------- |
| **Projeto**                   | Desafio Prático QA Júnior — Checkout  |
| **Aplicação sob teste ** | desafioqafadami.lovable.app           |
| **Tipo**                      | E-commerce  |
| **Responsável pelo plano**    | Miguel Luis — QA Júnior               |
| **Versão do documento**       | 1.1                                   |
| **Data**                      | Julho/2026                            |

---

# 2. Objetivo

Validar se o fluxo de checkout do "Curso de Teste de Software" está funcional, seguro e alinhado às Regras de Negócio (RN01–RN06) fornecidas, antes de uma hipotética liberação para Produção, entregando os artefatos solicitados pela avaliação.

---

# 3. Escopo

## 3.1 Dentro do escopo

| Módulo                 | Descrição                                                  |
| ---------------------- | ---------------------------------------------------------- |
| Formulário de checkout | Nome Completo, CPF, E-mail e Quantidade                    |
| Regras de quantidade   | Limites mínimo e máximo de itens (RN03)                    |
| Cupom de desconto      | Aplicação do cupom DESC10 e tratamento de cupons inválidos |
| Cálculo do total       | Validação da fórmula (Quantidade × R$ 50,00) − Desconto    |
| Finalização do pedido  | Modal de confirmação e prevenção de múltiplos envios       |

## 3.2 Fora do escopo

* Processamento real de pagamento
* Testes de carga e performance
* Pentest e testes avançados de segurança
* Automação de testes
* Testes de API (não documentados)

---

# 4. Estratégia de Teste

## 4.1 Abordagem

Será utilizada uma abordagem baseada nas Regras de Negócio (RN01–RN06), contemplando:

* Casos de teste funcionais;
* Testes de valor-limite;
* Testes de validação de dados;
* Testes exploratórios complementares.

Os casos de teste serão executados inicialmente conforme planejado. Após essa execução, será realizada uma sessão de testes exploratórios para identificar comportamentos não previstos nas regras de negócio ou inconsistências de usabilidade.

---

## 4.2 Tipos de teste

| Tipo           | Aplicado | Observação                                |
| -------------- | :------: | ----------------------------------------- |
| Funcional      |     ✅    | Validação principal das regras de negócio |
| Valor-limite   |     ✅    | Quantidade, CPF, e-mail e cupom           |
| Exploratório   |     ✅    | Busca de defeitos não previstos           |
| Regressão      |     ❌    | Não aplicável                             |
| Responsividade |    ⚠️    | Executado caso o tempo permita            |
| Performance    |     ❌    | Fora do escopo                            |
| Segurança      |     ❌    | Fora do escopo                            |

---

## 4.3 Dados de teste

* Nome fictício
* CPF válido e inválido
* E-mails válidos e inválidos
* Cupom válido (DESC10)
* Cupom inválido
* Quantidades mínimas, máximas e inválidas

---

# 5. Prioridade dos Testes

| Prioridade | Funcionalidade                  |
| ---------- | ------------------------------- |
| Alta       | Finalização do pedido           |
| Alta       | Cálculo do total                |
| Alta       | Aplicação do cupom              |
| Alta       | Regras de quantidade            |
| Média      | Validação dos campos            |
| Baixa      | Layout e mensagens informativas |

---

# 6. Matriz de Rastreabilidade

| Regra de Negócio | Casos de Teste  |
| ---------------- | --------------- |
| RN01             | CT-001          |
| RN02             | CT-002          |
| RN03             | CT-003 / CT-004 |
| RN04             | CT-005 / CT-006 |
| RN05             | CT-007          |
| RN06             | CT-008          |

---

# 7. Ordem de Execução

1. Exploração inicial da aplicação
2. Identificação das funcionalidades
3. Elaboração dos casos de teste
4. Execução dos casos de teste
5. Registro dos defeitos encontrados
6. Captura das evidências
7. Revisão da documentação
8. Entrega da avaliação

---

# 8. Critérios de Entrada

* Ambiente Staging disponível;
* Regras de Negócio compreendidas;
* Navegador configurado para execução dos testes.

---

# 9. Critérios de Saída

O teste será considerado concluído quando:

* Todos os casos de teste críticos forem executados;
* Todos os defeitos encontrados estiverem registrados com evidências;
* Os casos de teste estiverem documentados;
* A documentação solicitada estiver concluída dentro do tempo da avaliação.

---

# 10. Ambiente e Ferramentas

| Item                | Detalhe                             |
| ------------------- | ----------------------------------- |
| Ambiente            | Staging                             |
| Navegador           | Google Chrome (última versão)       |
| Sistema Operacional | Windows 11                          |
| Resolução           | 1920 × 1080                         |
| Documentação        | Markdown                            |
| Evidências          | Capturas de tela e vídeos (Jam.dev) |

---

# 11. Classificação de Severidade

| Severidade   | Critério                                                                  |
| ------------ | ------------------------------------------------------------------------- |
| S1 — Crítico | Impede a conclusão da compra                                              |
| S2 — Alto    | Regra de negócio incorreta                                                |
| S3 — Médio   | Funcionalidade apresenta comportamento inconsistente sem bloquear o fluxo |
| S4 — Baixo   | Problemas visuais ou cosméticos                                           |

---

# 12. Riscos

| Risco                         | Impacto | Mitigação                                                |
| ----------------------------- | ------- | -------------------------------------------------------- |
| Ambiente indisponível         | Alto    | Registrar evidência e informar no relatório              |
| Tempo limitado da avaliação   | Médio   | Priorizar funcionalidades críticas                       |
| Regras de negócio incompletas | Médio   | Validar conforme documentação disponível e boas práticas |
| Instabilidade da aplicação    | Médio   | Registrar evidências e repetir o teste quando possível   |

---

# 13. Premissas

* As validações serão realizadas exclusivamente com base nas regras de negócio disponibilizadas.
* Os dados utilizados serão fictícios.
* O ambiente corresponde a um ambiente de Staging, sem impacto em usuários reais.

---

# 14. Aprovação

Documento elaborado como parte da entrega do desafio técnico para a vaga de **QA Júnior**.

**Autor:** Miguel Luis
