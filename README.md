# Mini Portfólio de QA: Testes no Sauce Demo

Projeto prático de testes manuais e exploratórios no [Sauce Demo](https://www.saucedemo.com), uma loja virtual pública criada para treino de testes. O repositório reúne o planejamento, a execução dos casos de teste, os relatórios de bug e as evidências.

## Sobre o projeto

- **Objetivo:** praticar o trabalho de um QA Júnior: planejar, executar e documentar testes e reportar bugs com evidências.
- **Aplicação testada:** Sauce Demo (https://www.saucedemo.com). O site tem defeitos propositais em alguns usuários de teste.
- **Tipo de teste:** funcional manual e exploratório, caixa-preta.
- **Dentro do escopo:** login, lista de produtos, checkout e o comportamento dos usuários de teste com defeitos propositais. O carrinho é exercitado dentro dos fluxos de checkout e do TC-USR-02.
- **Fora do escopo:** performance sob carga, segurança, automação e API.
- **Técnicas aplicadas:** partição de equivalência (campos obrigatórios), tabela de decisão (login), transição de estado (carrinho), suposição de erros e teste exploratório.
- **Ambiente:** Google Chrome, Windows, novembro de 2026.
- **Usuários de teste** (listados na tela de login do site): `standard_user`, `locked_out_user`, `problem_user`, `performance_glitch_user`, `error_user` e `visual_user`. A senha de todos é `secret_sauce`.

## Cenários de teste

1. **Login:** acesso com dados válidos e inválidos, campos obrigatórios, usuário bloqueado, logout e acesso sem login.
2. **Lista de produtos:** exibição, ordenação, detalhe e imagens.
3. **Checkout:** compra completa, campos obrigatórios, total, cancelamento e carrinho vazio.
4. **Outros usuários de teste:** `problem_user`, `error_user`, `performance_glitch_user` e `visual_user`.

## Resumo da execução

| Módulo | Casos | Aprovados | Reprovados |
|---|---|---|---|
| Login | 8 | 8 | 0 |
| Lista de produtos | 5 | 5 | 0 |
| Checkout | 7 | 6 | 1 |
| Outros usuários de teste | 7 | 1 | 6 |
| **Total** | **27** | **20** | **7** |

- **Casos executados:** 27
- **Bloqueados:** 0
- **Bugs confirmados:** 8, sendo 2 de severidade alta, 4 média e 2 baixa

Com o `standard_user`, o fluxo principal (login, lista, ordenação e compra) funciona como esperado, e as validações de campos obrigatórios no login e no checkout se comportam corretamente. A única exceção é o checkout com carrinho vazio (BUG-008). Os demais defeitos aparecem nos usuários de teste com falhas propositais.

## Bugs encontrados

| ID | Título | Usuário | Severidade |
|---|---|---|---|
| [BUG-001](relatorios-de-bug.md#bug-001-imagens-dos-produtos-não-correspondem-aos-itens-problem_user) | Imagens dos produtos não correspondem aos itens | `problem_user` | Média |
| [BUG-002](relatorios-de-bug.md#bug-002-sobrenome-digitado-vai-para-o-campo-nome-no-checkout-problem_user) | Sobrenome digitado vai para o campo Nome no checkout | `problem_user` | Alta |
| [BUG-003](relatorios-de-bug.md#bug-003-ordenação-de-produtos-não-funciona-problem_user) | Ordenação de produtos não funciona | `problem_user` | Média |
| [BUG-004](relatorios-de-bug.md#bug-004-campo-last-name-não-aceita-digitação-e-checkout-avança-sem-validação-error_user) | Campo Last Name não aceita digitação e checkout avança sem validação | `error_user` | Alta |
| [BUG-005](relatorios-de-bug.md#bug-005-login-mais-lento-que-o-esperado-performance_glitch_user) | Login mais lento que o esperado | `performance_glitch_user` | Baixa |
| [BUG-006](relatorios-de-bug.md#bug-006-imagem-e-preços-diferentes-do-standard_user-visual_user) | Imagem e preços diferentes do `standard_user` | `visual_user` | Média |
| [BUG-007](relatorios-de-bug.md#bug-007-títulos-de-produtos-desalinhados-visual_user) | Títulos de produtos desalinhados | `visual_user` | Baixa |
| [BUG-008](relatorios-de-bug.md#bug-008-checkout-permite-finalizar-com-carrinho-vazio-standard_user) | Checkout permite finalizar com carrinho vazio | `standard_user` | Média |

## Observações e riscos

- Todos os testes foram manuais e executados em uma única rodada, apenas no Chrome. Não houve teste em outros navegadores nem em dispositivos móveis.
- A medição de tempo do `performance_glitch_user` foi manual e pode variar entre tentativas.
- Os defeitos dos usuários `problem_user`, `error_user`, `performance_glitch_user` e `visual_user` são propositais, criados pelo Sauce Demo para treino. Aqui eles são tratados como bugs reais, para praticar a documentação.

## Estrutura do repositório

```
portfolio-qa-saucedemo/
├── README.md                  # visão geral e resumo da execução
├── casos-de-teste.md          # os 27 casos de teste com resultados
├── relatorios-de-bug.md       # os 8 bugs documentados
└── evidencias/                # prints usados como evidência
```

## Próximos passos

Repetir o exercício com testes de API no Postman, usando a [ServeRest](https://serverest.dev), e acrescentar ao mesmo portfólio.
