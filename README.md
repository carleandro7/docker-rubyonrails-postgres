# Carleandro Nolêto
Usando o Docker com o  Ruby on Rails e PostgreSql
Versão
 - ruby 2.7.1
 - rails 6.0.3.2

# Instalação
Na pasta principal executar no terminal o comando para criar as imagens 
```sh
$ docker-compose build
$ docker-compose down 
```

Para criar um projeto com rails

```sh
$ docker-compose run app bundle exec rails new . -d postgresql
```
Para criar um projeto com rails

```sh
$ docker-compose run app bundle exec rails new . -d postgresql
```
Para atualizar as imagens

```sh
$ docker-compose build
$ docker-compose down 
```

Alterar o arquivo config/database.yml

> default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: mypassword
  pool: 5
development:
  <<: *default
  database: myapp_development
test:
  <<: *default
  database: myapp_test
production:
  <<: *default
>  database: myapp_production


Criar um CRUD com o nome da tabela users e atribuitos name, email
```sh
docker-compose run app bundle exec rails g scaffold user name email
```
Criar os bancos de dados no postgres e migrar a tabela users
```sh
docker-compose run app bundle exec rails db:drop db:create db:migrate
```
Adicionar a linha abaixo no arquivo confi/routes.rb
>root to: "users#index"

Por fim, subir os containers
```sh
docker-compose up -d
```
 Para acessar a aplicação no navegador digite: localhost
