# requisitos do sistema - ChamadoJÁ

## 1. Objetivo do sistema
O ChamdoJá é uma API de gestão de chamados de suporte técnico.

O sistema tem como objetivo permitir o registr, a classificação e o acompanhemento de solicitações de suporte, mantendo informações sobre os chamdos, seus responsaveis, categorias, prioridades, status, comentarios e hiistoricos de alterações.

A API tambem deverá disponibilizar consultas que auxiliem no acompanhemento e na analise dos chamados.

## 2. Descrição Do Problema
O atendimento de suporte técnico pode envolver diversas solicitações realizadas por diferentes usuarios. 
sem uma forma centralizada de registrar e acompanhar essas solicitações, pode ser dificil identificar quais problemas estão pendentes, qual é a prioridade de cada atendimento, quem realizou a solicitação e em qual etapa o atendimento se encontra.

O ChamdoJá busca solucionar esse problema por meio de uma api que centraliza o registro e o acompanhamento dos chamados de suporte técnico.

A aplicação deverá permitir organizar os chamados por categoria, prioriade e status, além de regidtrar comentarios e manter um historico de alterações de status.

dessa forma, as informações necessarias para acompanhar os atendimentos ficarão estruturadas e poderão ser consultadas por meio da API.

## 3. Publico Alvo
O ChamadoJá será usado por pessoas envolvidas no processo de solicitação e atendimento de suporte técnico.

### 3.1 Solicitante
é o usúario que registra uma solicitação de suporte.

suas principais atividades serão:
- abrir chamados;
- consultar chamados;
- acompanhar o andamento os chamados;
- adicionar comentarios aos chamados, quando permitido;

### 3.2 Atendente
É o usúario responsável pelo atendimento das solicitações.

Suas principais atividades serão:
- consultar chamdados;
- filtrar chamados;
- atualizar informações dos chamados;
- adicionar comentarios;
- alterar o status das chamadas;
- consultar o historico das alterações;

### 3.3 Administrador
É o usúario responsável por atividades adminstrativas do sistema.

Entre suas ppossíveis responsabilidades estão:
- gerenciar usúarios;
- gerenciar categorias;
- consultar informações gerais dos chamados;
- acompanhar indicadores quantitativos;


As regras específicas de autenticação e autorização dos diferentes tipos de usúarios serão definidas posteriomente.

## 4. Requisitos Funcionais

### RF001 - cadastro de usúarios

O siatema deverá permitir o cadastro de usúarios, armazenando as informações necessárias para sua identificação e utilização do sistema.

O e-mail do usuario deverá ser único.

Os dados recebidos deverão ser validados antes de seem armazenados.

### RF002 - Consulta de Usúarios

O sitema deverá permitir consultar os usúarios cadastrados.

A consulta deverá permitir obter informações necessárias para ientificar o usúario, sem expor dados sensíveis.

O siatema deverá permitir consultar um usúario específico por seu identificador.

### RF003 - Cadastro de Categorias

O siatema deverá permitir o cadastro de categorias de chamados.

Cada categoria deverá possuir, mínimo um nome.

O  nome da categoria deverá ser único no sistema
Os dados recebidos deverão ser validados antes de serem armazenados.

### RF004 - Consulta de Categorias

O sistema deverá permitir consultar as categorias cadastradas.

A consulta deverá permitir obter as informações necessárias para identificação e utilização das categorias nos chamados.

O sistema deverá permitir consultar uma categoria específica por seu identificador.

### RF005 - Abertura de Chamados

O siatema deverá permitir a abertura de chamados de suporte técnico.

Cada chamado deverá possuir, no mínimo:

- solicitante;
- categoria;
- título;
- descrição;
- prioridade;
- status.

O solicitante iformado deverá existir no sistema.

A categoria informada deverá existir e estra disponivel para utilização.

A prioridade deverá utilizar um dos valores permitidos pelo siatema.

Todo chamdo deverá ser criado inicialmente com o status 'aberto'.

Os dados recebidos deverão ser validados antes da criação do chamado.


### RF006 - Consulta de chamados

O sistema deverá permitir consultar os chamados cadastrados.

A consulta de um chamado específico deverá apresentar suas principais informações, incluindo:

- identificador;
- solicitante;
- categoria;
- titulo;
- descrição;
- prioridade;
- status;
- data de criação;
- data de atualização,

Quando aplicável,a consulta também deverá permitir acesso aos comentarios a ao historico de alterações do chamado.

Caso o chamdo informado não exista, o sistema deverpa informar que o recurso não foi encontrado.

### RF007 - Listagem de Chamados

O siatema deverá permitir listar os chamados cadastrados.

A listagem devera apresentar informações resumidas dos chamados, permitindo identificar os principais dados de cada registro.

A consulta deverá ser organizada de forma que possa receber filtros e paginação.

A listagem não deverá expor informações sensiveis ou desnecessárias para a consulta.

### RF008 - Atualização de Chamados
O sistema deverá permitir atualizar informações de um chamado.

A atualização deverá validar os dados recebidos antes de modificar o registro.

A atualização deverá preservar a identificação do chamado e seus relacionamentos.

A alteração do status devera ser realizada por uma operação especifica e deverá gerar um registro no historico de status.

Caso o chamado informado não exista, o sistema dverá informar que o recurso não foi encontrado.

### RF009 - Filtragem de Chamados
O sistema deverá permitir filtrar os chamados ppor diferentes criterios.

Inicialmente, deverão ser disponibilizados filtros por:

- status;
- prioridade;
- categoria.

Os filtros poderão ser utilizados individualmente ou combinados.

Exemplo de combinação:

status = aberto
prioridade = urgente
categoria = infraestrutura

A aplicação deverá validar os valores utilizados nos filtros.

Caso nenhum chamdo corresponda aos critérios informados, a API deverá retornar uma resposta válida indicando que não foram encontrados registros.

### RF010 - Paginação de Chamados

O sistema devrá permitir a consulta paginada dos chamados.

aA listagem deverá retornar uma quantidade limitada de registros por pagina.

A API  deverá fornecer informações necessarias para que o cliente possa navegar entre as páginas disponiveis.

A paginação deverá funcionar em conjunto com os filtros de chamados.

A quantidade de registros por pagina deverá possuir um limite definido pela aplicação, evitando solicitações excessivamnete grandes.

### RF011 - Registro de Comentarios

O sistema deverá permitir registrar comentarios vinculados a um chamado existente.

Cada comentario deverá possuir:

- chamado a qual pertence;
- usúario responsável pelo comentario;
- conteúdo;
- data e hora da criação.

O chamado informado deverá existir no sistema.

O conteudo do comentario deverá ser validado antes de ser armazenado.

Um comentario, depois de registrado deverá permanecer vinculado ao chamado ao qual pertence.

### RF012 - Alteração de status e registro de historico

O sistema dever´a permitir alterar o status de um chamado existente.

Os status permitidos inicialmente serão:

- 'aberto';
- 'em_andamento';
- 'aguardando';
- 'resolvido';
- 'fechado'.

Toda alteração de status deverá gerar um registro no historico do chamado.

O histórico deverá registrar, no mínimo:

- status anterior;
- novo status;
- usúario responsavel pela alteração;
- data e hora da alteração.

O sistema não deverá registrar uma alteração quando o novo status for igual ao status atual.

O chamado deverá sempre possuir um status válido.

Caso o chamado informado não exista, o sistema deverá informar que o recurso não foi encontrado.

### RF013 - resumo quantitativo dos chamados

O sistena deverá permitir consultar um resumo quantitativo dos chamados cadastrados.

O resumo deverá apresentar quantidades agrupadas por informações relevantes do atendimento, incluindo:

- quantidade total de chamados;
- quantidade de chamados por status;
- quantidade de chamados por prioridade;
- quantidade de chamados por categoria.

Os valores apresentados no resumo deverão refletir os dados atualmente registrados no sistema.

### RF014 - Validação dos Dados

O sistema deverá validar os dados recebidos nas operações de criação e atualização dos recursos.

A validação deverá verificar:

- presença dos campos obrigatórios;
- formato dos dados;
- tamanho dos campos;
- existencia de registros relacionados;
- valores permitidos para campos que possuam opções predefinidas;
- regras de unicidade quando aplicaveis.

Quando os dados enviados forem inválidos, a API deverá rejeitar a operação e retornar informações suficientes para identificar os campos que precisam ser corrigidos.

As validações deverão ser realizadas a tes da persistencia dos dados.

### RF015 - Tratamneto de recursos inexistentes

O sistema deverá identificar quando um recurso solicitado não existir.

Quando um usúario tentar consultar, atualizar ou realizar uma operação sobre um recurso inexistente , a API deverá retornar uma resposta adequada informando que o recurso não foi encontrado.

A resposta devera utilizar o codigo HTTP apropriado para indicar queo recurso solicitado não existe.

O sistema não deverá retornar informações internas da aplicação como parte da resposta de erro.

### RF016 - Controle das informações retornadas 

A API devrá retornar somente as informações necessárias para cada operação solicitada.

dados sensiveis ou internos da aplicação não deverão ser expostos nas respostas da API.

As respostas relacionadas aosusúarios não deverão incluir senhas ou seus hashes.

Informações internas utulizadas pela aplicação, mas que não sejam necessárias para o consumidor da API, também não deverão ser retornadas.

a estrutura das respostas deverá ser consistente e adequada ao recurso consultado.



## 5. Requisitos não Funcionais

### RNF001 — Tecnologia e arquitetura

A aplicação deverá ser desenvolvida utilizando Laravel e PHP.

O sistema deverá disponibilizar seus recursos por meio de uma API REST.

O banco de dados utilizado pela aplicação deverá ser PostgreSQL.

O gerenciamento das dependências deverá ser realizado utilizando Composer.

O código-fonte deverá ser versionado utilizando Git.

### RNF002 — Organização e manutenção

A aplicação deverá possuir uma estrutura organizada, respeitando as responsabilidades definidas pelo framework Laravel.

Os componentes da aplicação deverão ser separados de acordo com suas responsabilidades, evitando concentrar regras de negócio, validações e acesso aos dados em um único componente.

O código deverá utilizar nomes claros e consistentes.

As funcionalidades deverão ser desenvolvidas de forma que possam ser modificadas ou ampliadas sem alterações desnecessárias em outras partes do sistema.

### RNF003 — Banco de dados e integridade

A aplicação deverá utilizar PostgreSQL como banco de dados principal.

Os relacionamentos entre os recursos deverão ser representados adequadamente no banco de dados.

A estrutura do banco deverá possuir restrições que contribuam para a integridade dos dados, incluindo, quando aplicável:

- chaves primárias;
- chaves estrangeiras;
- campos obrigatórios;
- restrições de unicidade;
- valores padrão;
- regras de integridade referencial.

As regras de integridade do banco deverão complementar as validações realizadas pela aplicação.

### RNF004 — Segurança

A aplicação deverá adotar medidas básicas de segurança para proteger os dados e os recursos disponibilizados pela API.

As credenciais e informações sensíveis não deverão ser armazenadas diretamente no código-fonte.

As senhas dos usuários deverão ser armazenadas utilizando mecanismos seguros de hash, nunca em texto puro.

Senhas, hashes de senha e outras informações sensíveis não deverão ser retornados pelas respostas da API.

Os dados recebidos pela API deverão ser validados antes de serem processados ou persistidos.

A aplicação deverá utilizar os mecanismos de proteção contra atribuição em massa disponibilizados pelo Laravel.

Consultas ao banco de dados deverão utilizar os mecanismos seguros disponibilizados pelo framework e pelo sistema de acesso ao banco, evitando a concatenação direta de dados fornecidos pelo usuário em comandos SQL.

Informações internas da aplicação, como caminhos de arquivos, consultas SQL, stack traces e credenciais, não deverão ser expostas em respostas destinadas ao cliente.

O arquivo `.env` não deverá ser versionado no repositório. O projeto deverá disponibilizar um `.env.example` sem credenciais reais.

A aplicação deverá utilizar HTTPS quando disponibilizada em ambiente de produção.

Mecanismos de autenticação e autorização poderão ser implementados posteriormente utilizando Laravel Sanctum, conforme o aprofundamento definido para o projeto.

### RNF005 — Validação e tratamento de erros

A API deverá utilizar respostas HTTP adequadas para representar o resultado das operações realizadas.

Erros de validação deverão ser informados de maneira estruturada, permitindo que o consumidor da API identifique os campos que precisam ser corrigidos.

Erros relacionados a recursos inexistentes deverão utilizar o código HTTP apropriado.

Erros internos da aplicação não deverão expor informações sensíveis ou detalhes da implementação.

As respostas de erro deverão possuir estrutura consistente entre os diferentes recursos da API.

### RNF006 — Testes

A aplicação deverá possuir testes automatizados para os principais comportamentos do sistema.

Os testes deverão contemplar, no mínimo:

- cadastro de usuários;
- cadastro de categorias;
- abertura de chamados;
- validação dos dados;
- consulta de chamados;
- atualização de chamados;
- alteração de status;
- registro do histórico de status;
- registro de comentários;
- filtros;
- paginação;
- consultas quantitativas.

Os testes deverão ser executáveis de forma independente e deverão utilizar um ambiente de teste apropriado.

### RNF007 — Documentação

O projeto deverá possuir documentação suficiente para permitir sua instalação, configuração e utilização.

A documentação deverá incluir:

- requisitos necessários para executar o projeto;
- instruções de instalação;
- configuração do ambiente;
- configuração do banco de dados;
- forma de execução da aplicação;
- instruções para execução dos testes;
- descrição das principais decisões técnicas;
- documentação dos endpoints da API.

As alterações e decisões relevantes tomadas durante o desenvolvimento deverão ser registradas no diário do projeto.

### RNF008 — Desempenho e uso eficiente dos recursos

A aplicação deverá realizar consultas de forma eficiente, evitando operações desnecessárias no banco de dados.

As listagens deverão utilizar paginação quando houver possibilidade de retorno de múltiplos registros.

Os relacionamentos entre os recursos deverão ser consultados de forma adequada, evitando consultas repetitivas desnecessárias.

Filtros deverão ser aplicados preferencialmente no banco de dados, evitando carregar registros desnecessários para a aplicação.

Consultas quantitativas deverão utilizar mecanismos de agregação do banco de dados sempre que apropriado.

O sistema deverá evitar o processamento ou retorno de quantidade de dados superior ao necessário para cada operação.

### RNF009 — Versionamento e controle das alterações

O código-fonte do projeto deverá ser versionado utilizando Git.

As alterações relevantes deverão ser registradas por meio de commits que permitam identificar a evolução do projeto.

O repositório deverá manter uma estrutura organizada, permitindo acompanhar as alterações realizadas durante o desenvolvimento.

Decisões técnicas e alterações importantes nos requisitos deverão ser registradas na documentação do projeto.

### RNF010 — Configuração e execução do ambiente

A aplicação deverá possuir uma configuração de ambiente documentada, permitindo que o projeto seja executado em um ambiente de desenvolvimento compatível com os requisitos definidos.

As configurações específicas do ambiente, como credenciais do banco de dados e outras informações sensíveis, deverão ser fornecidas por meio de variáveis de ambiente.

O projeto deverá disponibilizar um arquivo `.env.example` contendo as configurações necessárias para orientar a criação do ambiente local, sem informações sensíveis reais.

A aplicação deverá informar, por meio da documentação, os requisitos necessários para sua execução.


## 6. Regras de negocio


## 7.Regra de Prioridade e status



## 8.Limites do Escopo


## 9.Dúvidas e Hipóteses da Equipe
 



