# Diagramas do Sistema A.G.I.L

Índice dos diagramas do projeto.

| Diagrama | Arquivo |
|---|---|
| Casos de uso | [`casos-de-uso.png`](casos-de-uso.png) (abaixo) |
| Sequência: cadastro de funcionário | [`sequencia-cadastro-funcionario.png`](sequencia-cadastro-funcionario.png) (abaixo) |
| Sequência: movimentação de estoque | [`sequencia-movimentacao-estoque.png`](sequencia-movimentacao-estoque.png) (abaixo) |
| Classes | [`diagrama-de-classes.md`](diagrama-de-classes.md) |
| DER e modelo lógico | [`der-e-modelo-logico.md`](der-e-modelo-logico.md) |

---

## Diagrama de casos de uso

![Diagrama de Casos de Uso](casos-de-uso.png)

Especificação detalhada de cada caso de uso em [`../casos-de-uso.md`](../casos-de-uso.md).

---

## Diagramas de sequência

### Cadastro de funcionário

Fluxo em que o gestor cadastra um funcionário: validação dos campos obrigatórios, verificação de e-mail já cadastrado, hash da senha e gravação no banco (caso de uso UC_02).

![Diagrama de Sequência: Cadastro de Funcionário](sequencia-cadastro-funcionario.png)

### Movimentação de estoque (entrada e saída)

Fluxo de entrada e saída de produtos, com os caminhos de sucesso e erro (caso de uso UC_09). Nesta figura o ator aparece como "Gerente"; nos demais documentos ele é chamado de "Gestor".

![Diagrama de Sequência: Movimentação de Estoque](sequencia-movimentacao-estoque.png)

---

## Outros diagramas

- [Diagrama de classes](diagrama-de-classes.md)
- [DER e modelo lógico](der-e-modelo-logico.md)
