# ChamadoJá — API de Gestão de Chamados de Suporte Técnico

## 1. Apresentação do Projeto
O **ChamadoJá** é uma API REST desenvolvida como Projeto Integrador no curso de Back-end do Instituto Federal. A aplicação tem como objetivo centralizar, organizar e acompanhar solicitações de suporte técnico, substituindo processos informais como planilhas, ligações e mensagens soltas.

## 2. Descrição do Problema

Sem um sistema centralizado de atendimento, a gestão de TI enfrenta dificuldades para:

- Saber quem abriu cada solicitação.
- Classificar e priorizar os atendimentos urgentes.
- Acompanhar quais problemas estão pendentes ou em andamento.
- Manter o histórico de alterações e interações de cada suporte.

## 3. Tecnologias Utilizadas

- **Linguagem:** PHP
- **Framework:** Laravel
- **Banco de Dados:** PostgreSQL
- **Gerenciador de Dependências:** Composer
- **Controle de Versão:** Git
- **Documentação de API:** Markdown / Postman / Insomnia

## 4. Estrutura do Repositório

chamado-ja/
├── app/                  # Código-fonte da aplicação Laravel
├── database/             # Migrations, Seeders e Factories do banco de dados
├── docs/                 # Documentação técnica do projeto
│   ├── requisitos.md     # Requisitos funcionais, não funcionais e regras de negócio
│   ├── casos-de-uso.md   # Especificação dos casos de uso e atores
│   ├── contrato-api.md   # Contrato das rotas, payloads e respostas JSON
│   └── diario.md         # Diário de bordo das etapas e uso de IA
├── routes/               # Definição das rotas da API (`api.php`)
├── tests/                # Testes automatizados da aplicação
├── .env.example          # Exemplo das variáveis de ambiente
├── README.md             # Documentação principal
└── composer.json         # Gerenciamento de dependências PHP

## 5. Instruções de Instalação e Execução (Em Desenvolvimento)Requisitos PréviosPHP 8.2 ou superiorComposerPostgreSQLGitPasso a Passo InicialClonar o repositório:Bashgit clone [https://github.com/prodgyBRT/chamadoja.git](https://github.com/prodgyBRT/chamadoja.git)

cd chamadoja

Instalar as dependências:Bashcomposer install

Configurar o Arquivo .env:Bashcp .env.example .env

Configure as credenciais do seu banco PostgreSQL no arquivo .env.

Gerar a chave da aplicação:Bashphp artisan key:generate

Executar as Migrations:Bashphp artisan migrate

Iniciar o Servidor de Desenvolvimento:Bashphp artisan serve

A API estará acessível em http://localhost:8000.6. Documentação ComplementarPara consultar o detalhamento de requisitos funcionais e regras de negócio, acesse docs/requisitos.md.   Para consultar o fluxo de casos de uso, acesse docs/casos-de-uso.md.   Para consultar o mapeamento completo de rotas e payloads, acesse docs/contrato-api.md.   Para verificar o histórico semanal de desenvolvimento, acesse docs/diario.md.   