
# Stack para Desenvolver Localmente


**Indice**
- [O que é o Localstack?](#o-que-é-o-localstack)
- [Criando localstack para o seu projeto?](#criando-localstack-para-o-seu-projeto)
- [Como rodar?](#como-rodar)
- [Módulos](#modulos)



## O que é o Localstack?
Localstack é responsável por disponibilizar um ambiente idêntico ao de produção, porém localmente, para realizarmos o desenvolvimento e/ou testes, ou seja, nada mais é um projeto docker compose com um conjunto de servicos disponíveis ( que chamamos de modulos ). Essas funcionalidades são: Ambiente local da AWS, Banco de dados, Banco em Memória, MOCK de APIS entre outros serviços necessários para se emular um ambiente de produção.


## Criando localstack para o seu projeto?
Cada projeto possui uma pasta **localstack**. Dentro dela terá um arquivo docker-compose.yml e uma pasta chamada entrypoints( pontos de entrada) a onde tera scripts e rotina auxiliares para cada módulo a ser utilizado.

Exemplo:

**docker-compose.yml**

```yaml
version: 3.1
services:

# Modulo: Database
  database:
    image: "postgres"
    restart: "always"
    environment:
      POSTGRES_PASSWORD: "password"
      POSTGRES_USER: "user"
      POSTGRES_DB: "kim"
    ports:
      - "5432:5432"
    volumes:
      - "./entrypoints/database:/docker-entrypoint-initdb.d"
# ----------------

```

## Como rodar?
Para subir o ambiente basta está na pasta do localstack e realizar ter instalado o docker e o docker-compose e executar os comando abaixo:

### Subir o ambiente
```sh
docker-compose up -d
```

### Para destruir o ambiente
```sh
docker-compose down --remove-orphans
```


## Modulos
Para acessar a lista de módulos, basta acessar a [https://kimmais.github.io/localstack/modules/](https://kimmais.github.io/localstack/modules/)

