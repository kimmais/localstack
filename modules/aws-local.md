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
      DEFAULT_REGION: "us-east-1"
    ports:
      - "4566:4566"
      - "4571:4571"
    volumes:
      - "./entrypoints/tmp/localstack:/tmp/localstack" # Armazenamento dos arquivos temporários
      - "./entrypoints/aws:/docker-entrypoint-initaws.d" # Entrypoint para rodar scripts ao iniciar
# ==================
```

#### Configuração

- EDGE_PORT: número da porta para o serviço de borda, o principal ponto de entrada para todas as chamadas de API (padrão: 4566).

- SERVICE: lista de serviços a serem emulados separados por vírgulas de nomes de serviço. 
Os nomes de serviço correspondem basicamente aos nomes de serviço do AWS CLI (kinesis, lambda, sqs, etc), embora LocalStack só ofereça suporte a um subconjunto deles. Valor de exemplo: kinesis, lambda, sqs para iniciar Kinesis, Lambda e SQS. Além disso, os seguintes valores abreviados podem ser especificados para executar um conjunto predefinido de serviços: sem servidor: serviços de execução geralmente usados - para aplicativos sem servidor (iam, lambda, dynamodb, apigateway, s3, sns)

- DEFAULT_REGION: região AWS para usar ao falar com a API (padrão: us-east-1)

Alguns 

