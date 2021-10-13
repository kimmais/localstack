
# Modulo: Mockserver
Esse modulo é resposnável por construir uma Mock API para testes e desenvolvimento local.

O serviço, trabalha com conceito de mock incremental, a onde ele vai adicionando localmente os registros da api no arquivo db.json, além disso ele 

### Instalando modulo:
para instalar o modulo de banco de dados, basta copiar o script abaixo e inserir no atributo service do seu yml no docker-compose.

**Passos para utilização**

1. Incluir o modulo no arquivo docker-compose
2. Copiar e colar os arquivos que estão em: https://github.com/kimmais/localstack/edit/main/modules/mockserver
3. Incluir no arquivo db.json os nomes do serviço e setá-los como lista, como está no exemplo do proprio arquivo.



**Estrutura básica**
```yaml

# Modulo: Database
  mockserver:
    image: node:12
    wokking_dir: "/app/mockserver"
    command: |
      npm i -g json-server;
      npm i;
      npm start;
    ports:
      - "3000:3000"
    entrypoint:
      - "./entrypoints/mockserver:/app/mockserver"
# ================
```



#### Configurando as rotas e a base com db.json

```json
{
  "employees":[],
  "orders":[],
  "products":[]
}
```

## Mais informações
- Para mais informações sobre o postgres no docker compose, basta acessar o link: [https://hub.docker.com/_/node](https://hub.docker.com/_/node)
- Para informações sobre json-server acesse: [https://www.npmjs.com/package/json-server](https://www.npmjs.com/package/json-server)
