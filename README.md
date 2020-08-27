# :man_technologist: Sobre o desafio 
Nesse desafio você deve criar uma aplicação para armazenar transações financeiras de entrada e saída do usuário logado, onde será possível o cadastro e listagem dessas transações.

## :hammer_and_wrench: Requisitos técnicos da aplicação
* Para o backend será necessário utilizar __NodeJS__.
* Para o frontend damos preferência para o __VueJS__, porém se tiver mais facilidade com __ReactJS__, manda bala! :bow_and_arrow:
* Para armazenamento dos dados, utilizar o banco de dados não relacional <b>MongoDB</b> (fique à vontade para utilizar Docker :whale:). 

## :scroll: :computer: Lista das funcionalidades do backend
### Usuários
A aplicação deve conter rotas de:
* Cadastro de usuários. A rota deve receber um objeto no corpo da requisição conforme exemplo abaixo e armazenar no banco.
```
{
  "name": "John Doe",
  "email": "johndoe@email.com,
  "password": "123456"
}
```
* Edição dos dados do usuário: A rota deve receber como parametro o user_id. No corpo da requisição deve receber um objeto com as propriedades name, email e password. Ao final deverá ser retornado um objeto com as novas informações do usuário. __Obs.__: O usuário deve estar logado para acessar essa rota.

### Autenticação
A aplicação deve conter rotas de:
* Login: A rota deve receber um objeto contendo email e senha do usuário, fazer devidas validações e retornar as informações do usuário juntamente com o token de autenticação. __Dica__: para autenticação, é legal você utilizar JWT.

* Logout: A rota receberá o user_id e simplesmente retornará um objeto com as informações abaixo:
```
{
  "_id": "user-id",
  "auth": false
}
```

### Transações
__Obs.__: Lembre-se que para acessar essas rotas, o usuário deve estar logado na aplicação. :wink:

A aplicação deve conter rotas de:
* Cadastro de transações. Essa rota deve receber title, value, type dentro do corpo da requisição, sendo type o tipo da transação, que deve ser income para entradas (depósitos) e outcome para saídas (retiradas). Deve receber também por parametro (req params) o user_id (id do usuário que está realizando a transação) e retornar as seguintes informações:
```
{
  "_id: "transaction-id",
  "user_id: "user-id",
  "title": "Salário",
  "value": 4000,
  "type": "income"
}
```
Obs: A aplicação não deve permitir que uma transação do tipo outcome extrapole o valor total que o usuário tem em caixa, retornando uma resposta com código HTTP 400.

* Listagem das transações. Essa rota deve receber como parametro o id do usuário e listar todas as transações feitas por ele junto com o valor de soma de entradas, retiradas e total de crédito. Essa rota deve retornar um objeto com o formato a seguir:
```
{
  "transactions": [
    {
      "_id": "mongo-id",
      "title": "Salário",
      "value": 4000,
      "type": "income"
    },
    {
      "_id": "mongo-id",
      "title": "Cadeira Gamer",
      "value": 1000,
      "type": "outcome"
    },
  ],
  "balance": {
    "income": 4000,
    "outcome": 1000,
    "total": 3000
  }
}
```

## :scroll: :nail_care: Lista das funcionalidades do frontend web
__Obs__.: Você deve conectar a aplicação com o backend via HTTP para a realização das funcionalidades abaixo:

### Página de cadastro
* Essa página deve conter um formulário com os inputs de nome, email e senha; um botão para cadastar e um link para acessar a página de login. Ao clicar no botão, deverá ser feita uma requisição HTTP para a api, e redirecionar o usuário para o dashboard.

### Página de login
* Essa página deve conter um formulário com os inputs de email e senha; um botão de login e um link para acessar a página de cadastro, caso o usuário ainda não for cadastrado. Ao clicar no botão, deverá ser feita uma requisição HTTP para a api, e se caso os dados estiverem corretos, salvar os dados do usuário no localstorage e redirecionar o usuário para o dashboard.

__Obs.__: Todas as páginas abaixo devem ser controladas por autenticação.

### Página de dashboard
* Essa página (dashboard) deve exibir a lista de todas as transações realizadas pelo usuário e o saldo em conta.
* Deve conter também um menu com as opções "Dashboard", "Nova transação", "Meu perfil" e "Logout".

### Página de cadastro de transação
* Essa página deve conter um formulário com os inputs de descrição (title), valor (value) e um botão para cadastrar. Ao cadastrar a nova transação, você pode apenas exibir uma mensagem de sucesso. __Dica__: antes de enviar a transação para a api, verifique se o valor é maior ou menor que 0 para definir o tipo (type) da transação.

### Página de edição do usuário
* Essa página deve conter um formulário com os inputs de nome, email, senha e um botão para editar. Ao editar as informações você pode apenas exibir uma mensagem de sucesso. 

### Logout
* A opção de logout deve fazer uma requisição para a rota de logout na api, limpar os dados do usuário no localstorage e redirecionar ele para o login.

## Considerações finais
* É necessário fazer somente o especificado acima. Porém, se quiser deixar sua criatividade fluir (principlamente no frontend) fique à vontade para acrescentar o que você quiser!
* Assuntos de como o desenvolvedor lida com status code, validações gerais e gerenciamento de estado (frontend) fará parte da avaliação.
* A organização e estrutura do projeto também fará parte da avaliação.

## Entrega e prazo do desafio
* Você deve subir o projeto (frontend e backend) para o seu github e compartilhar a url conosco através dos e-mails: caionascimento@questinteligencia.com.br e guilhermechi@indecx.com.br;
* Você tem 2 finais de semana para concluir esse desafio a partir da data de entrega. Se terminar antes, basta nos enviar o e-mail.

Boa sorte! <br />
Equipe IndeCX. :green_heart:
