# Localstack
Localstack é responsável por disponibilizar um ambiente idêntico ao de produção, porém localmente, para realizarmos o desenvolvimento e/ou testes.


## O que é o Localstack?
Nada mais é um projeto docker compose com um conjunto de servicos disponíveis ( que chamamos de modulos ). Essas funcionalidades são: Ambiente local da AWS, Banco de dados, Banco em Memória, MOCK de APIS entre outros serviços necessários para se emular um ambiente de produção.

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
      POSTGRES_PASSWORD:"password"
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

Para rodar, 
### Subir o ambiente
```sh
docker-compose up -d
```

### Para destruir o ambiente
```sh
docker-compose down --remove-orphans
```


# Módulos
Abaixo, segue como usar os modulos fornecidos nos projetos.

Lista de módulos:
- [AWS Local](https://kimmais.github.io/localstack/modules/aws-local)
- [Database](https://kimmais.github.io/localstack/modules/database)
- [Mock Server](https://kimmais.github.io/localstack/modules/mockserver)
