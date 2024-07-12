IaC - Infraestructure as Code 🚧 Deploy de um api (flask)

💻 Sobre o projeto Provisionar uma infraestrutura na AWS com Terraform

💪 Funcionalidades Cria a imagem da api em docker e executa o container 

🛠 Pré-requisitos Git e docker 

🎲 Instalação

Clone este repositório

🚀 CI/CD

Passos para executar o pipeline:

Configure o arquivo .gitlab-ci.yml: Certifique-se de que o arquivo .gitlab-ci.yml está no diretório raiz do seu repositório GitLab.

Commit e Push: Faça commit e push das suas alterações para o repositório no GitLab.

Pipeline Automático: O GitLab CI/CD irá automaticamente detectar o arquivo .gitlab-ci.yml e iniciar o pipeline conforme definido.


Explicação do funcionamento da Pipeline:


stages: Fases do pipeline (build e test).
variables: Configurações do Docker.
services: Usa Docker-in-Docker (docker
).
before_script: Exibe informações do Docker.
build:

Fase: build.
Script: Constrói a imagem Docker.
only: Executa apenas na branch main.
test:

Fase: test.
Script:
Executa a imagem Docker.
Verifica se a aplicação está funcionando atraves do comando  curl.








Utilizei os seguintes comando para testar a interação com a API.

Criando e listando comentários por matéria
matéria 1
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"alice@example.com","comment":"first post!","content_id":1}'

curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"alice@example.com","comment":"ok, now I am gonna say something more useful","content_id":1}'

curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"bob@example.com","comment":"I agree","content_id":1}'

matéria 2
curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"bob@example.com","comment":"I guess this is a good thing","content_id":2}'

curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"charlie@example.com","comment":"Indeed, dear Bob, I believe so as well","content_id":2}'

curl -sv host/api/comment/new -X POST -H 'Content-Type: application/json' -d '{"email":"eve@example.com","comment":"Nah, you both are wrong","content_id":2}'

listagem matéria 1
curl -sv host/api/comment/list/1

listagem matéria 2
curl -sv host/api/comment/list/2