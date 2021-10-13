# Localstack
Localstack é responsável por disponibilizar um ambiente idêntico ao de produção, porém localmente, para realizarmos o desenvolvimento e/ou testes.

- [O que é o localstack?](#o-que-%C3%A9-o-localstack)

## O que é o Localstack?
Nada mais é um projeto docker compose com um conjunto de servicos disponíveis ( que chamamos de modulos ). Essas funcionalidades são: Ambiente local da AWS, Banco de dados, Banco em Memória, MOCK de APIS entre outros serviços necessários para se emular um ambiente de produção.


## O que é necessário para rodar
Para rodar é necessário ter o docker e docker-compose na sua maquina e no mínimo 8Gb de memória.

## Como rodar
Para subir o ambiente basta está na pasta do localstack e realizar esse comando:

Para rodar, 
### Subir o ambiente
```sh
docker-compose up -d
```

### Para destruir o ambiente
```sh
docker-compose down -remove-orphans
```


# Issues

- [X] Descrever o que é o localstack
- [ ] O quê é necessário para rodar
- [ ] Como rodar
- [ ] Modulos prontos

