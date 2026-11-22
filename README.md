# Documentação do Projeto – A.G.I.L

Documentação técnica do **A.G.I.L** (Agilidade, Ganho, Inovação, Logística), plataforma web de gerenciamento de estoque para clínicas e microempresas, desenvolvida no Projeto Integrador do curso de Desenvolvimento de Software Multiplataforma da FATEC Indaiatuba (Dr. Archimedes Lammoglia).

Esta pasta reúne os **requisitos** e os **diagramas** do sistema. O relatório completo do projeto (análise de mercado, design, usabilidade e demais seções) está no documento **Projeto Integrador** entregue em PDF.

## Conteúdo

| Arquivo | O que contém |
|---|---|
| [`requisitos.md`](requisitos.md) | Requisitos funcionais (RF001 a RF015) e não funcionais (RNF001 a RNF008) |
| [`casos-de-uso.md`](casos-de-uso.md) | Diagrama de casos de uso e especificação dos casos de uso (UC_01 a UC_12) |
| [`dicionario-de-dados.md`](dicionario-de-dados.md) | Tabelas, campos, tipos e restrições do banco de dados |
| [`diagramas/README.md`](diagramas/README.md) | Índice dos diagramas (casos de uso e sequência) |
| [`diagramas/diagrama-de-classes.md`](diagramas/diagrama-de-classes.md) | Diagrama de classes (entidades do domínio) |
| [`diagramas/der-e-modelo-logico.md`](diagramas/der-e-modelo-logico.md) | DER e modelo lógico do banco de dados |

## Estrutura da pasta

```
docs/
├── README.md
├── requisitos.md
├── casos-de-uso.md
├── dicionario-de-dados.md
└── diagramas/
    ├── README.md
    ├── diagrama-de-classes.md
    ├── der-e-modelo-logico.md
    ├── casos-de-uso.png
    ├── sequencia-cadastro-funcionario.png
    └── sequencia-movimentacao-estoque.png
```

## Banco de dados

Os scripts SQL (criação, dados de exemplo, manipulação e testes de integridade) ficam na pasta [`database/`](../database/README.md) deste repositório.

## Repositórios e acesso

- Organização no GitHub: <https://github.com/AGIL-PI-FATEC>
  - `front-end-AGIL`: interface web (React)
  - `back-end-AGIL`: API (Java, Spring Boot) e banco de dados relacional (MySQL)
- Versão publicada do front-end: <https://agil-two.vercel.app/>

## Tecnologias

- **Front-end:** React JS
- **Back-end:** Java com Spring Boot (persistência com Hibernate)
- **Banco de dados:** MySQL
- **Protótipos:** Figma
- **Versionamento:** Git e GitHub

## Equipe

Alice de Góes Maria, Henrique Correa Magalhães Prates, Livia Mayumi Hayashida, Sara Rossi Bacherolo e Vicenzo Cirilo.
