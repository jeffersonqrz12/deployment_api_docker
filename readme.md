IaC - Infrastructure as Code 🚧 Deploy de uma API (Flask)
💻 Sobre o Projeto
Este projeto visa provisionar uma infraestrutura na AWS usando Terraform para suportar a execução de uma API desenvolvida com Flask. A API é empacotada em uma imagem Docker e executada em um container, permitindo uma configuração e deployment simplificados e eficientes.

💪 Funcionalidades
Criação e Execução da Imagem Docker: O projeto cria a imagem Docker da API Flask e executa o container com essa imagem.
Infraestrutura como Código (IaC): Usa Terraform para provisionar a infraestrutura necessária na AWS.
🛠 Pré-requisitos
Git: Para controle de versão e colaboração no repositório.
Docker: Para empacotar a aplicação em uma imagem e executar o container.
🎲 Instalação
Clone este repositório:

Copiar código
git clone https://github.com/jeffersonqrz12/deployment_api_docker


Navegue para o diretório do projeto:

Copiar código
cd seu_repositorio


🚀 CI/CD
Passos para executar o pipeline:

Configure o arquivo .gitlab-ci.yml: Certifique-se de que o arquivo .gitlab-ci.yml está localizado no diretório raiz do seu repositório GitLab.

Commit e Push: Faça commit e push das suas alterações para o repositório no GitLab.

Pipeline Automático: O GitLab CI/CD detectará automaticamente o arquivo .gitlab-ci.yml e iniciará o pipeline conforme definido.

Explicação do Funcionamento da Pipeline:

stages: Define as fases do pipeline, como build e test.
variables: Configurações específicas do Docker.
services: Utiliza Docker-in-Docker para permitir a execução de containers dentro do pipeline.
before_script: Exibe informações sobre o Docker antes da execução dos scripts.
Fases do Pipeline:

build:

Fase: Build
Script: Constrói a imagem Docker da API Flask.
only: Executa apenas na branch main.
test:

Fase: Test
Script: Executa a imagem Docker e verifica se a aplicação está funcionando corretamente através de comandos curl.
📜 Testando a API
Para testar a API, use os seguintes comandos curl para criar e listar comentários:

Criando Comentários:

Matéria 1:

bash
Copiar código
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"alice@example.com","comment":"first post!","content_id":1}'
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"alice@example.com","comment":"ok, now I am gonna say something more useful","content_id":1}'
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"bob@example.com","comment":"I agree","content_id":1}'
Matéria 2:

bash
Copiar código
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"bob@example.com","comment":"I guess this is a good thing","content_id":2}'
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"charlie@example.com","comment":"Indeed, dear Bob, I believe so as well","content_id":2}'
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"eve@example.com","comment":"Nah, you both are wrong","content_id":2}'
Listando Comentários:

Matéria 1:

bash
Copiar código
curl -sv host/api/comment/list/1
Matéria 2:

bash
Copiar código
curl -sv host/api/comment/list/2
Este resumo cobre os principais aspectos do seu projeto e fornece instruções claras para configuração e teste. Ajuste conforme necessário para se adequar ao seu público e à sua apresentação! Se precisar de mais detalhes ou alterações, estou à disposição.
