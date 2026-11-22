# Requisitos do Sistema A.G.I.L

Requisitos conforme o documento **Projeto Integrador** (seções 6 e 7).

**Prioridades:** Essencial, Importante ou Desejável.
**Usuários:** Gestor e Funcionário são os perfis do sistema; "Sistema" indica requisito sobre o próprio software.

## 1. Requisitos funcionais

| ID | Nome | Descrição | Usuários | Prioridade |
|---|---|---|---|---|
| RF001 | Fazer login no sistema | O usuário pode realizar login no sistema informando e-mail e senha previamente cadastrados. O sistema deve validar os dados e permitir o acesso à área principal (Início) caso estejam corretos. | Funcionário e Gestor | Essencial |
| RF002 | Fazer o cadastro de gestor | O sistema deve permitir o cadastro de novos gestores, solicitando informações como nome, login e senha. Após o preenchimento correto, o cadastro poderá ser finalizado. | Gestor | Essencial |
| RF003 | Fazer o cadastro de funcionários | O gestor pode realizar o cadastro de novos funcionários no sistema, informando dados como nome, login e senha. Após o preenchimento correto das informações, o cadastro deve ser salvo e o funcionário poderá acessar o sistema conforme seu nível de permissão. | Gestor | Essencial |
| RF004 | Cadastrar produtos | O sistema deve permitir cadastrar informações como nome, quantidade e descrição. | Funcionário e Gestor | Essencial |
| RF005 | Editar produtos | O sistema deve permitir editar informações como nome, quantidade e descrição. | Funcionário e Gestor | Essencial |
| RF006 | Excluir produtos | O sistema deve permitir a exclusão de produtos e informações dentro do estoque. | Funcionário e Gestor | Essencial |
| RF007 | Registrar entrada de produtos | O sistema deve permitir registrar a entrada de produtos no estoque, atualizando automaticamente a quantidade disponível. | Funcionário e Gestor | Essencial |
| RF008 | Registrar saída de produtos | O sistema deve permitir registrar a saída de produtos do estoque, reduzindo a quantidade disponível. | Funcionário e Gestor | Essencial |
| RF009 | Disponibilizar um histórico de movimentação | O sistema deve armazenar e exibir o histórico de entrada e saída de produtos, incluindo data e responsável pela ação. | Funcionário e Gestor | Importante |
| RF010 | Buscar produtos | O sistema deve permitir a busca de produtos por nome ou código para facilitar a localização no estoque. | Funcionário e Gestor | Desejável |
| RF011 | Alertar estoque mínimo | O sistema deve emitir alertas quando a quantidade de um produto atingir o nível mínimo definido. | Funcionário e Gestor | Importante |
| RF012 | Disponibilizar um canal de ajuda geral | O sistema deve disponibilizar um canal de ajuda geral, acessível em todas as telas, contendo manuais de operação, guias de usuário e informações de contato para suporte técnico. | Funcionário e Gestor | Desejável |
| RF013 | Editar as informações do perfil | O sistema deve permitir que o usuário visualize e edite suas informações de perfil, incluindo nome, foto e e-mail de contato. | Funcionário e Gestor | Importante |
| RF014 | Excluir funcionários | O sistema deve permitir que o gestor delete cadastros de funcionários. | Gestor | Importante |
| RF015 | Editar funcionários | O sistema deve permitir que o gestor edite informações do funcionário. | Gestor | Importante |

## 2. Requisitos não funcionais

| ID | Nome | Descrição | Usuários | Prioridade |
|---|---|---|---|---|
| RNF001 | Assegurar autenticação | O sistema deve armazenar as senhas de forma criptografada para garantir a segurança dos dados dos usuários. | Sistema | Essencial |
| RNF002 | Fornecer boa experiência de desempenho | O sistema deve responder às ações do usuário em até 2 segundos. | Sistema | Desejável |
| RNF003 | Disponibilizar acesso com a internet | A utilização da aplicação depende de conexão com a internet para acesso às funcionalidades do sistema. | Sistema | Essencial |
| RNF004 | Facilitar o uso pelo usuário | A aplicação deve ser de fácil utilização, com interface intuitiva que permita ao usuário navegar e executar tarefas sem dificuldades. | Sistema | Essencial |
| RNF005 | Compatibilizar com navegadores | A aplicação deve ser compatível com os principais navegadores para garantir a experiência do usuário e o funcionamento do site. | Sistema | Essencial |
| RNF006 | Manter continuamente a aplicação | A aplicação deve estar disponível 24 horas por dia, 7 dias por semana, garantindo acesso contínuo aos usuários. | Sistema | Essencial |
| RNF007 | Manter a escalabilidade | A aplicação deve ser capaz de suportar o crescimento no número de usuários sem perda significativa de desempenho. | Sistema | Essencial |
| RNF008 | Facilitar manutenção | O código-fonte da aplicação deve seguir padrões de boas práticas de programação, facilitando manutenção e evolução do sistema. | Sistema | Importante |

## 3. Resumo por prioridade

| Prioridade | Requisitos funcionais | Requisitos não funcionais |
|---|---|---|
| Essencial | RF001 a RF008 | RNF001, RNF003, RNF004, RNF005, RNF006, RNF007 |
| Importante | RF009, RF011, RF013, RF014, RF015 | RNF008 |
| Desejável | RF010, RF012 | RNF002 |

Os casos de uso que detalham esses requisitos estão em [`casos-de-uso.md`](casos-de-uso.md).
