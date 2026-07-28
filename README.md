<p align="center">
  <img src="https://img.shields.io/static/v1?label=STATUS&message=EM%20ANDAMENTO&color=YELLOW&style=for-the-badge"/>
</p>

# Desafio Técnico QA Júnior — Checkout (Fadami)

Repositório contendo a documentação produzida durante a realização do **Desafio Técnico para a vaga de Analista de Testes (QA Júnior)** da **Fadami**.

O objetivo deste desafio foi validar funcionalmente o fluxo de checkout da aplicação disponibilizada, verificando sua conformidade com as Regras de Negócio fornecidas e documentando todos os artefatos produzidos durante o processo de testes.

---

# 👨‍💻 Autor

**Miguel Luis**

📍 QA Engineer | Quality Assurance

🔗 LinkedIn: https://www.linkedin.com/in/miguel-luisatf/

---

# 🌐 Aplicação sob teste

**Ambiente (Staging)**

https://desafioqafadami.lovable.app/

---

# 🎯 Objetivo

Validar o fluxo de checkout do produto **"Curso de Teste de Software"**, identificando possíveis defeitos antes de uma hipotética publicação em produção.

Durante o desafio foram produzidos os seguintes artefatos:

* Plano de Testes
* Casos de Teste
* Relatório de Bugs
* Evidências (prints e/ou vídeos)

---

# 📚 Regras de Negócio Avaliadas

| ID   | Regra                                                                                                                                     |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| RN01 | Produto único com valor unitário de **R$ 50,00**                                                                                          |
| RN02 | Nome Completo, CPF, E-mail e Quantidade são obrigatórios                                                                                  |
| RN03 | Quantidade mínima de **1** e máxima de **10**                                                                                             |
| RN04 | Cupom **DESC10** concede **10% de desconto**; qualquer outro deve exibir "Cupom inválido"                                                 |
| RN05 | Total = (Quantidade × R$ 50,00) − Desconto                                                                                                |
| RN06 | Ao finalizar o pedido deve ser exibido um modal de confirmação e o botão deve ser desabilitado imediatamente para evitar múltiplos envios |

---

## 📁 Estrutura do repositório
 
```
.
├── README.md
├── bug reports/
│   └── bug                          # Um arquivo por bug (BUG-AAAAMMDD-NNN-titulo.md)
│
└── documentacao/
    ├── plano de testes.md            # Estratégia e escopo dos testes
    ├── metrica do repositorio.md     # Métricas de execução (cobertura, pass rate, etc.)
    └── casos de teste/               # Casos de teste (CT-001 em diante)
```
 
---

# 📄 Artefatos Entregues

| Documento            | Descrição                                                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 📋 Plano de Testes   | Estratégia, escopo, ambiente, critérios, riscos e planejamento da execução dos testes.                                           |
| ✅ Casos de Teste     | Cenários elaborados a partir das regras de negócio e boas práticas de QA.                                                        |
| 🐞 Relatório de Bugs | Defeitos encontrados contendo severidade, prioridade, passos para reprodução, resultado esperado, resultado obtido e evidências. |
| 📸 Evidências        | Capturas de tela e/ou vídeos que comprovam os defeitos encontrados durante a execução.                                           |

---

# 🧪 Estratégia de Teste

A execução foi organizada nas seguintes etapas:

1. Exploração inicial da aplicação;
2. Levantamento das funcionalidades disponíveis;
3. Análise das Regras de Negócio;
4. Elaboração dos casos de teste;
5. Execução dos testes funcionais;
6. Testes de valor-limite;
7. Testes exploratórios complementares;
8. Registro dos defeitos encontrados;
9. Organização das evidências;
10. Revisão e entrega da documentação.

---

# ✅ Tipos de Testes Aplicados

| Tipo                                | Aplicado |
| ----------------------------------- | :------: |
| Testes Funcionais                   |     ✅    |
| Testes de Valor-Limite              |     ✅    |
| Testes de Validação de Campos       |     ✅    |
| Testes Exploratórios                |     ✅    |
| Responsividade *(quando aplicável)* |    ⚠️    |
| Performance                         |     ❌    |
| Segurança (Pentest)                 |     ❌    |
| Automação                           |     ❌    |

---

# 📌 Convenção de Nomenclatura

## Casos de Teste

```
CT-001
CT-002
CT-003
...
```

## Bugs

```
BUG-001
BUG-002
BUG-003
...
```

## Melhorias (quando aplicável)

```
MELHORIA-001
MELHORIA-002
...
```

---

# 📊 Entregáveis

| Entregável        |     Status     |
| ----------------- | :------------: |
| Plano de Testes   |        ✅       |
| Casos de Teste    |         ✅        |
| Relatório de Bugs | ⏳ Em andamento |
| Evidências        | ⏳ Em andamento |

---

# 🛠 Ambiente de Teste

| Item                | Valor                                 |
| ------------------- | ------------------------------------- |
| Ambiente            | Staging                               |
| Navegador           | Google Chrome e Brave (última versão estável) |
| Sistema Operacional | Windows 11                            |
| Resolução           | 1920 × 1080                           |
| Documentação        | Markdown                              |
| Evidências          | Jam.dev                               |

---

# 🐞 Classificação dos Defeitos

| Severidade       | Critério                                                    |
| ---------------- | ----------------------------------------------------------- |
| **S1 — Crítico** | Impede a finalização da compra                              |
| **S2 — Alto**    | Regra de negócio incorreta ou cálculo inconsistente         |
| **S3 — Médio**   | Funcionalidade inconsistente sem bloquear o fluxo principal |
| **S4 — Baixo**   | Problemas visuais, ortográficos ou cosméticos               |

---

# 📌 Observações

* Todos os testes foram realizados em ambiente **Staging**.
* Nenhum pagamento real foi efetuado.
* Todos os dados utilizados durante os testes são fictícios.
* As validações foram baseadas nas Regras de Negócio fornecidas para o desafio.
* Situações não descritas na especificação foram avaliadas utilizando boas práticas de Qualidade de Software e usabilidade.

---

# 🙏 Agradecimentos

Agradeço à equipe da **Fadami** pela oportunidade de participar do processo seletivo e pela proposta deste desafio técnico, que possibilitou demonstrar minha abordagem para planejamento, execução e documentação de testes de software.

Espero que este material reflita meu comprometimento com a qualidade, organização e melhoria contínua dos processos de teste.
