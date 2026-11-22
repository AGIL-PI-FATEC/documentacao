# DER e Modelo Lógico – A.G.I.L

Modelos do banco de dados **`agildb`**, de acordo com o script [`database/schema.sql`](../../database/schema.sql). Os diagramas são renderizados automaticamente pelo GitHub.

## 1. DER (modelo conceitual)

Visão das entidades e dos relacionamentos. Linha contínua indica chave estrangeira no banco; linha pontilhada indica referência lógica, sem chave estrangeira.

```mermaid
erDiagram
    GESTOR_EMPRESA ||--o{ FUNCIONARIO : "cadastra"
    GESTOR_EMPRESA ||--o{ PRODUTOS : "gerencia"
    GESTOR_EMPRESA ||--o{ HISTORICO : "possui"
    GESTOR_EMPRESA ||--o{ NOTIFICACOES : "recebe"
    PRODUTOS |o..o{ HISTORICO : "produto_id"
    PRODUTOS |o..o{ NOTIFICACOES : "produto_id"
```

### Cardinalidades

| Relacionamento | Entidade A | Entidade B | Cardinalidade |
|---|---|---|---|
| cadastra | `GESTOR_EMPRESA` | `FUNCIONARIO` | (1,1) para (0,N) |
| gerencia | `GESTOR_EMPRESA` | `PRODUTOS` | (1,1) para (0,N) |
| possui | `GESTOR_EMPRESA` | `HISTORICO` | (1,1) para (0,N) |
| recebe | `GESTOR_EMPRESA` | `NOTIFICACOES` | (1,1) para (0,N) |
| produto_id | `PRODUTOS` | `HISTORICO` | (0,1) para (0,N), sem FK |
| produto_id | `PRODUTOS` | `NOTIFICACOES` | (0,1) para (0,N), sem FK |

## 2. Modelo lógico

Tabelas, colunas, tipos e chaves. Os detalhes de cada campo estão no [dicionário de dados](../dicionario-de-dados.md).

```mermaid
erDiagram
    GESTOR_EMPRESA {
        bigint id_gestor PK
        varchar(18) cnpj_empresa UK "NOT NULL"
        varchar(80) email_gestor UK "NOT NULL"
        varchar(80) nome_gestor "NOT NULL"
        varchar(80) nome_empresa
        varchar(80) razao_social "NOT NULL"
        varchar(60) senha_gestor "NOT NULL"
        longtext foto
    }

    FUNCIONARIO {
        bigint id_funcionario PK
        varchar(60) cargo_funcionario "NOT NULL"
        varchar(80) email_funcionario UK "NOT NULL"
        varchar(80) nome_funcionario "NOT NULL"
        varchar(60) senha_funcionario "NOT NULL"
        varchar(255) foto_url
        longtext foto
        bigint id_gestor FK "NOT NULL"
    }

    PRODUTOS {
        bigint id PK
        varchar(255) nome
        decimal preco "DECIMAL(38,2)"
        int estoque_caixas
        longtext imagem
        int qtd_por_caixa
        bigint id_gestor FK "NOT NULL"
    }

    HISTORICO {
        bigint id PK
        datetime data "DATETIME(6)"
        varchar(255) produto
        bigint produto_id "sem FK"
        int quantidade
        varchar(255) tipo "ENTRADA ou SAIDA"
        varchar(255) unidade
        bigint id_gestor FK "NOT NULL"
    }

    NOTIFICACOES {
        bigint id PK
        bit(1) ativa
        datetime data "DATETIME(6)"
        bit(1) lida
        varchar(255) mensagem
        bigint produto_id "sem FK"
        varchar(255) tipo
        varchar(255) titulo
        bigint id_gestor FK "NOT NULL"
    }

    GESTOR_EMPRESA ||--o{ FUNCIONARIO : "id_gestor"
    GESTOR_EMPRESA ||--o{ PRODUTOS : "id_gestor"
    GESTOR_EMPRESA ||--o{ HISTORICO : "id_gestor"
    GESTOR_EMPRESA ||--o{ NOTIFICACOES : "id_gestor"
    PRODUTOS |o..o{ HISTORICO : "produto_id"
    PRODUTOS |o..o{ NOTIFICACOES : "produto_id"
```

**Legenda:** PK = chave primária · FK = chave estrangeira · UK = valor único.

## 3. Restrições de integridade

- **UNIQUE:** `gestor_empresa.cnpj_empresa`, `gestor_empresa.email_gestor` e `funcionario.email_funcionario`.
- **NOT NULL:** campos marcados no modelo lógico.
- **FOREIGN KEY:** `id_gestor` em `funcionario`, `produtos`, `historico` e `notificacoes`, todas apontando para `gestor_empresa.id_gestor`.

Os testes dessas restrições estão em [`database/testes_integridade.sql`](../../database/testes_integridade.sql).
