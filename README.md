# CRUD TodoApp

Um CRUD simples com api em C#, utilizando Entity Framework com Sqlite.

## Como Executar

Para executar o projeto, é preciso ter instalado em sua máquina o CLI do ef core. Um tutorial completo sobre o mesmo está disponível (Aqui)[https://learn.microsoft.com/pt-br/ef/core/cli/dotnet].

Execute `dotnet ef migrations add NOME_MIGRACAO`, onde o NOME_MIGRACAO pode ser qualquer um à sua escolha. O comando cria uma migração do entity framework na pasta Migrations do projeto.

Execute `dotnet ef database update`, o comando irá rodar o comando SQL para a criação do banco de dados e das tabelas (no caso do projeto, uma só), no local especificado que, por padrão é um banco Sqlite local na pasta raiz do projeto.

Também é possível rodar o comando `dotnet ef migrations script`, no qual será possível visualizar no terminal, qual o script gerado que será executado para a criação do banco e tabelas.

Após a criação do banco de dados, é possível rodar a API com o comando `dotnet watch run` ou `dotnet run`.

É recomendado o uso de alguma aplicação de requisições, como Postman ou Insomnia para os testes da API.

A API irá rodar nos seguintes endereços: `https://localhost:5001` e `http://localhost:5000`, podendo os mesmo serem alterados em Properties/launchSettings.json na chave `applicationUrl`.

## Rotas

GET /todos
Retorna todos os Todos salvos no banco.

GET /todos/{id}
Retorna um único Todo pelo que tenha o mesmo id informado na URL, retornando Not Found, se o mesmo não for encontrado.

POST /todos
Salva um todo no banco, enviado no corpo da requisição, que deverá conter obrigatoriamente um JSON com a chave "title" e um valor diferente de vazio.

PUT /todos/{id}
Edita um todo, que exista com o id informado na url, retornando Not Found se o mesmo não for encontrado. No corpo da requisição é preciso informar o "title" e o "done" no JSON enviado.

DELETE /todos/{id}
Remove um todo do banco para o id informado, retornando Not Found se o mesmo não for encontrado no banco.