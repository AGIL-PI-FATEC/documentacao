# Dicionário de Dados – A.G.I.L

Dicionário do banco de dados **`agildb`** (MySQL 8), baseado no script de criação [`database/schema.sql`](../database/schema.sql), que foi extraído do banco gerado pelo Hibernate.

O banco tem **5 tabelas**. Todas as tabelas dependentes ligam-se a `gestor_empresa` pela coluna `id_gestor`.

| Tabela | Finalidade |
|---|---|
| [`gestor_empresa`](#gestor_empresa) | Gestor e dados da empresa |
| [`funcionario`](#funcionario) | Funcionários vinculados a um gestor |
| [`produtos`](#produtos) | Produtos do estoque |
| [`historico`](#historico) | Histórico de movimentações (entradas e saídas) |
| [`notificacoes`](#notificacoes) | Notificações e alertas do sistema |

**Legenda:** PK = chave primária · FK = chave estrangeira · UK = valor único · NN = não nulo.

---

## gestor_empresa

Armazena o gestor e os dados da empresa. As senhas são guardadas com hash BCrypt (RNF001).

| Campo | Tipo | Nulo? | Chave / Restrição | Descrição |
|---|---|---|---|---|
| `id_gestor` | BIGINT | NN | PK, auto incremento | Identificador do gestor |
| `cnpj_empresa` | VARCHAR(18) | NN | UK | CNPJ da empresa |
| `email_gestor` | VARCHAR(80) | NN | UK | E-mail de login do gestor |
| `nome_gestor` | VARCHAR(80) | NN | | Nome do gestor |
| `nome_empresa` | VARCHAR(80) | Sim | | Nome da empresa |
| `razao_social` | VARCHAR(80) | NN | | Razão social da empresa |
| `senha_gestor` | VARCHAR(60) | NN | | Senha com hash BCrypt |
| `foto` | LONGTEXT | Sim | | Foto do perfil |

---

## funcionario

Funcionários cadastrados pelo gestor.

| Campo | Tipo | Nulo? | Chave / Restrição | Descrição |
|---|---|---|---|---|
| `id_funcionario` | BIGINT | NN | PK, auto incremento | Identificador do funcionário |
| `cargo_funcionario` | VARCHAR(60) | NN | | Cargo do funcionário |
| `email_funcionario` | VARCHAR(80) | NN | UK | E-mail de login do funcionário |
| `nome_funcionario` | VARCHAR(80) | NN | | Nome do funcionário |
| `senha_funcionario` | VARCHAR(60) | NN | | Senha com hash BCrypt |
| `foto_url` | VARCHAR(255) | Sim | | URL da foto |
| `foto` | LONGTEXT | Sim | | Foto do perfil |
| `id_gestor` | BIGINT | NN | FK → `gestor_empresa.id_gestor` | Gestor responsável pelo cadastro |

---

## produtos

Produtos do estoque. O estoque é controlado em caixas.

| Campo | Tipo | Nulo? | Chave / Restrição | Descrição |
|---|---|---|---|---|
| `id` | BIGINT | NN | PK, auto incremento | Identificador do produto |
| `nome` | VARCHAR(255) | Sim | | Nome do produto |
| `preco` | DECIMAL(38,2) | Sim | | Preço do produto (por caixa) |
| `estoque_caixas` | INT | Sim | | Quantidade de caixas em estoque |
| `qtd_por_caixa` | INT | Sim | | Quantidade de unidades por caixa |
| `imagem` | LONGTEXT | Sim | | Imagem do produto |
| `id_gestor` | BIGINT | NN | FK → `gestor_empresa.id_gestor` | Gestor dono do produto |

---

## historico

Registra as movimentações de estoque mostradas na tela de Histórico.

| Campo | Tipo | Nulo? | Chave / Restrição | Descrição |
|---|---|---|---|---|
| `id` | BIGINT | NN | PK, auto incremento | Identificador do registro |
| `data` | DATETIME(6) | Sim | | Data e hora da movimentação |
| `produto` | VARCHAR(255) | Sim | | Nome do produto movimentado |
| `produto_id` | BIGINT | Sim | sem FK | Identificador do produto movimentado |
| `quantidade` | INT | Sim | | Quantidade movimentada |
| `tipo` | VARCHAR(255) | Sim | | Tipo da movimentação: `ENTRADA` ou `SAIDA` |
| `unidade` | VARCHAR(255) | Sim | | Unidade da quantidade (ex.: caixas) |
| `id_gestor` | BIGINT | NN | FK → `gestor_empresa.id_gestor` | Gestor dono do registro |

---

## notificacoes

Notificações e alertas exibidos na tela de Notificações.

| Campo | Tipo | Nulo? | Chave / Restrição | Descrição |
|---|---|---|---|---|
| `id` | BIGINT | NN | PK, auto incremento | Identificador da notificação |
| `titulo` | VARCHAR(255) | Sim | | Título da notificação |
| `mensagem` | VARCHAR(255) | Sim | | Texto da notificação |
| `tipo` | VARCHAR(255) | Sim | | Tipo da notificação |
| `data` | DATETIME(6) | Sim | | Data e hora da notificação |
| `lida` | BIT(1) | Sim | | Indica se a notificação foi lida |
| `ativa` | BIT(1) | Sim | | Indica se a notificação está ativa |
| `produto_id` | BIGINT | Sim | sem FK | Produto relacionado à notificação |
| `id_gestor` | BIGINT | NN | FK → `gestor_empresa.id_gestor` | Gestor dono da notificação |

---

## Relacionamentos

| Tabela pai | Tabela filha | Coluna | Cardinalidade | Tipo |
|---|---|---|---|---|
| `gestor_empresa` | `funcionario` | `id_gestor` | 1 para N | FK |
| `gestor_empresa` | `produtos` | `id_gestor` | 1 para N | FK |
| `gestor_empresa` | `historico` | `id_gestor` | 1 para N | FK |
| `gestor_empresa` | `notificacoes` | `id_gestor` | 1 para N | FK |
| `produtos` | `historico` | `produto_id` | 1 para N | referência lógica, sem FK |
| `produtos` | `notificacoes` | `produto_id` | 1 para N | referência lógica, sem FK |

## Índices e restrições de unicidade

| Tabela | Restrição | Coluna |
|---|---|---|
| `gestor_empresa` | UNIQUE | `cnpj_empresa` |
| `gestor_empresa` | UNIQUE | `email_gestor` |
| `funcionario` | UNIQUE | `email_funcionario` |

Os testes que verificam essas restrições (UNIQUE, NOT NULL e FOREIGN KEY) estão em [`database/testes_integridade.sql`](../database/testes_integridade.sql).
