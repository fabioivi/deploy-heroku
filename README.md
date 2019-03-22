# Como fazer deploy de uma aplicação NodeJS no Heroku

### Clonar projeto inicial criado no github
````
$ git clone https://github.com/user/meu-projeto.git
````
### Criar o arquivo .gitignore 
````
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
lerna-debug.log*

# Dependency directories
node_modules/
jspm_packages/
````

### Inicializar o gerenciador de pacotes npm no projeto
````
$ npm init
````

### Instalar os pacotes express e ejs
````
$ npm install express
$ npm install ejs
````

### Criar o arquivo de inicialização da aplicação (server.js)
````node
var express = require('express');
var app = express();

var port = process.env.PORT || 8080;
app.set('view engine', 'ejs');

// make express look in the public directory for assets (css/js/img)
app.use(express.static(__dirname + '/public'));

app.get('/', function(req, res) {
	// ejs render automatically looks in the views folder
	res.render('index');
});

app.listen(port, function() {
	console.log('Our app is running on http://localhost:' + port);
});
````

### Adicione no arquivo package.json o comando usado para iniciar a aplicação
````
 "scripts": {
    "start": "node server.js"
  },
````

### Agora vamos criar o arquivo inicial do nosso projeto (views/index.ejs)
````
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Site em NodeJs</title>
    <link href="//maxcdn.bootstrapcdn.com/bootswatch/3.2.0/superhero/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
<div class="container">
    <div class="jumbotron">
        <h1>Aprendendo usar o Heroku</h1>
        <p>Disciplina de Gerência e Configuração de Sistemas para Internet</p>
        <p>Prof. Fábio Duarte de Oliveira</p>
    </div>
</div>
</body>
</html>
````

### Também vamos adicionar o arquivo css do nosso projeto (public/css/style.css)
````
body    { padding-top:50px; }
.container .jumbotron    { border-radius:40px; }
````

### Iniciar o servidor para testes
````
npm run start
````    

### Verificar se nossa aplicação ok
````
Nossa aplicação deve estar rodando em http://localhost:8080
````  

### Fazendo deploy da aplicação no Heroku
````
heroku git:remote -a nome_app_heroku
$ git push heroku master
````

### Fazendo deploy da aplicação no Heroku
````
heroku git:remote -a nome_app_heroku
$ git push heroku master
````

### Agora é só checar se a aplicação subiu no Heroku
````
heroku open
````
