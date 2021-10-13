# Modulo: Database
O Banco de dados usado na KIM+ é o postgres, por esse motivo, abaixo, segue como instalar o postgres no seu docker compose.


### Instalando modulo:
para instalar o modulo de banco de dados, basta copiar o script abaixo e inserir no atributo service do seu yml no docker-compose

**Estrutura básica**
```yaml

// Modulo: Database
  database:
    image: "postgres"
    restart: "always"
    environment:
      POSTGRES_PASSWORD: "password"
      POSTGRES_USER: "user"
      POSTGRES_DB: "kim"
    ports:
      - "5432:5432"
// ================

```

## Mais informações
Para mais informações sobre o postgres no docker compose, basta acessar o link: [!https://hub.docker.com/_/postgres](https://hub.docker.com/_/postgres)
