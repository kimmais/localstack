# AWS Local
Stack AWS local totalmente funcional. 

Todas as APIs são expostas por meio de um único serviço de borda, que pode ser acessado em http://localhost:4566 por padrão (personalizável via EDGE_PORT, veja mais abaixo).

**Serviços emulados**

- ACM (alias: acm)
- API Gateway (alias: apigateway)
- CloudFormation (alias: cloudformation)
- CloudWatch (alias: cloudwatch)
- CloudWatch Logs (alias: cloudwatchlogs)
- DynamoDB (alias: dinamodb)
- DynamoDB Streams (alias: dynamodbstreams)
- EC2 (alias: apigateway)
- Elasticsearch Service (alias: elasticsearch)
- EventBridge (CloudWatch Events) (alias: eventbridge)
- Firehose (alias: firehose)
- IAM (alias: iam)
- Kinesis (alias: kinesi)
- KMS (alias: kms)
- Lambda (alias: lambda)
- Redshift (alias: redshift)
- Route53 (alias: route53)
- S3 (alias: s3)
- SecretsManager (alias: secretsmanaer)
- SES (alias: ses)
- SNS (alias: sns)
- SQS (alias: sqs)
- SSM (alias: ssm)
- StepFunctions (alias: stepfunction)
- STS (alias: sts)


### Usando o modulo

**docker-compose.yml**
```yaml

# Modulo: AWS Local
  aws_local:
    image: "localstack/localstack"
    restart: "always"
    environment:
      SERVICES: "secretsmanager"
      EDGE_PORT: "4566"
      DEFAULT_REGION: "us-east-2"
    ports:
      - "4566:4566"
      - "4571:4571"
    volumes:
      - "./entrypoints/tmp/localstack:/tmp/localstack" # Armazenamento dos arquivos temporários
      - "./entrypoints/aws:/docker-entrypoint-initaws.d" # Entrypoint para rodar scripts ao iniciar
# ==================
```

#### Configuração

Abaixo, segue algumas configurações para emular os ambientes

| Variável | Descrição |
| -------- | --------- |
| EDGE_PORT | número da porta para o serviço de borda, o principal ponto de entrada para todas as chamadas de API (padrão: 4566)|
| SERVICE | Lista de serviços a serem emulados separados por vírgulas de nomes de serviço. Os nomes de serviço correspondem basicamente aos nomes de serviço do AWS CLI (kinesis, lambda, sqs, etc)|
| DEFAULT_REGION | região AWS para usar ao falar com a API (padrão: us-east-1) |


Alguns serviços precisar de configurações específicas, neste caso oriento acessar o link [https://hub.docker.com/r/localstack/localstack](https://hub.docker.com/r/localstack/localstack)

