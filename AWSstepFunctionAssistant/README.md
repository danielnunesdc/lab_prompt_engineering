# Criando uma Assistente de Delivery com AWS Step Functions e Bedrock

## Introdução

Este artigo explora como criar uma Assistente de Delivery utilizando AWS Step Functions e Bedrock. AWS Step Functions permite a coordenação de múltiplos serviços em um fluxo de trabalho serverless, enquanto o Bedrock oferece uma plataforma para integração de modelos de IA. Vamos abordar os conceitos fundamentais e mostrar como essas ferramentas podem ser combinadas para construir uma solução de delivery automatizada.

## 1. Bem-Vindo ao Step Functions

AWS Step Functions é um serviço que facilita a orquestração de fluxos de trabalho complexos envolvendo vários serviços AWS. Utilizando uma abordagem serverless, você pode criar aplicações altamente escaláveis e resilientes.

**Aplicação no projeto**: Utilizamos Step Functions para gerenciar o fluxo completo de um pedido de delivery, desde o recebimento até a entrega.

## 2. Pré-Requisitos

Antes de começar, você precisará:

- Uma conta ativa na AWS.
- Conhecimento básico de AWS Lambda, JSON, e conceitos de cloud computing.
- Ferramentas: AWS CLI e acesso ao AWS Management Console.

## 3. Situação Problema

**Desafio**: Criar uma solução automatizada para gerenciar pedidos de delivery, garantindo eficiência e comunicação constante com o cliente.

**Objetivo**: Desenvolver uma Assistente de Delivery que coordena tarefas automaticamente, como processamento de pedidos, alocação de entregadores, e envio de notificações.

## 4. Step Functions Official Page

Visite a [página oficial do AWS Step Functions](https://aws.amazon.com/step-functions/) para acessar a documentação completa, exemplos de uso e tutoriais detalhados.

## 5. Documentação Oficial

A leitura da [documentação oficial do AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html) é essencial para entender as funcionalidades e limitações do serviço.

## 6. Localizando o Serviço

No AWS Management Console, use a barra de busca ou navegue pelo menu para localizar o serviço "Step Functions". Certifique-se de estar na região correta onde deseja criar seus recursos.

## 7. Começando com um Projeto Template

AWS oferece templates prontos para Step Functions, que servem como ponto de partida. Por exemplo, o template "Order Processing" pode ser uma boa base para o desenvolvimento da Assistente de Delivery.

## 8. Workflow Studio & ASL

**Workflow Studio**: Ferramenta visual para construir e visualizar seus fluxos de trabalho em Step Functions.

**ASL (Amazon States Language)**: Linguagem JSON usada para definir os workflows. É importante entender a sintaxe básica para criar e modificar seus fluxos.

## 9. Criando um Hello World

Comece criando um simples "Hello World" para entender o básico do Step Functions. Isso ajudará a familiarizar-se com o processo de criação, implantação e monitoramento de um fluxo de trabalho.

### Passos:

1. Crie uma nova State Machine.
2. Defina um estado inicial que retorne uma mensagem "Hello World".
3. Implemente e teste.

## 10. Precificação e Custos

AWS Step Functions é cobrado por estado transicionado e tempo de execução. Consulte a [página de preços](https://aws.amazon.com/step-functions/pricing/) para entender os custos e otimizar a utilização.

## 11. Nível 1 de Configuração - Permissão de Perfil

**Permissões IAM**: Crie ou ajuste uma role IAM com as permissões necessárias para que o Step Functions acesse outros serviços AWS como Lambda, DynamoDB e Bedrock.

**Prática**: Atribua a role IAM correta ao criar a State Machine.

## 12. Nível 2 de Configuração - Disponibilidade de Serviço

Para garantir alta disponibilidade, configure seus serviços em múltiplas regiões ou zonas de disponibilidade. Isso aumenta a resiliência da Assistente de Delivery.

## 13. Criando um Assistente de Delivery na Prática

### Visão Geral

Nesta etapa, você utilizará AWS Step Functions para orquestrar as seguintes tarefas:

1. **Recebimento do Pedido**: Integração com API Gateway e Lambda.
2. **Verificação de Entregadores Disponíveis**: Alocação otimizada de entregadores.
3. **Notificação ao Cliente**: Utilização de serviços como SNS para manter o cliente informado.
4. **Atualização do Status do Pedido**: Persistência dos dados no DynamoDB.

### Exemplo Prático

Crie uma Step Function que coordena essas tarefas e integre com AWS Bedrock para aplicar modelos de IA, como a otimização de rotas de entrega e previsão de tempos de entrega.


### Construção

<img src = "assets/worklfow-removebg.png"/>

Para a criação/interligação dos Steps (passos) dos Workflows/Fluxo (maquinas de estado), disponibiliza:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
1 - **Ações**:   Serviços da AWS e respectivas ações pré-definidas destes serviços;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
2 - **Fluxos**:  Steps de apoio no direcionamento do fluxo, como por exemplo: 
- *Choice* - decisão (lógica if/then/else);
- *Parallel* - execução em paralelo; 
- *Map* - loop de execução;
- *Wait* - aguarda determinado tempo (configurável) para execução do próximo step;
- *Success* - para o fluxo e indica "Sucesso" na execução;
- *Fail* - para o fluxo e indica "Falha" na execução;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
3 - **Padrões**: Sub-fluxos pré-definidos, usados com frequencia. Exemplos:
- *Process S3 objects* - Usa o Maquina de Estado com o AWS Lambda para processar objetos num bucket S3;
 - *Process JSON file in S3* - Usa o Maquina de Estado com o AWS Lambda para processar dados de um arquivo JSON no S3;
 - *Process CSV file in S3* - Usa o Maquina de Estado com o AWS Lambda para processar dados de um arquivo CSV no S3;

### Configurações e Informações Adicionais

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
1 - Você não paga pela utilização do Step Functions, mas é **muito importante** lembrar que *estará utilizando* **Serviços Pagos** então verifique os custos;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
2 - Como o Steps Functions, utiliza Serviços da AWS, **o acesso** a estes Serviços devem ser Configurados;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
3 - Determinados Serviços necessitam de Configurações Adicionais. 
    Exemplo: AWS Bedrock, necessita da configuração da LLM que será utilizada, então além de você garantir (configurar) a utilização da LLM em sua Região, deverá configurar o Step do Bedrock, informando a utilização da LLM;
    

### Execução e Logs de Execução

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
Ao executar a Maquina de Estado, você terá a visão da execução de 2 maneiras:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
1 - **State View**: Log de Execução por Step/Task - você terá o Status e Tempo de Execução e conseguirá detalhar as informações de Entrada e Saída;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
2 - **Event View**: Log de Execução por Ações dentro de cada Task;


## Conclusão

Com AWS Step Functions e Bedrock, você pode construir uma Assistente de Delivery altamente eficiente e automatizada. Este artigo cobriu os conceitos essenciais e ofereceu uma base sólida para o desenvolvimento dessa solução. Explore as ferramentas e serviços oferecidos pela AWS para personalizar e expandir sua Assistente de Delivery conforme as necessidades do seu negócio.

---

### Referências:

- [AWS Step Functions](https://aws.amazon.com/step-functions/)
- [Documentação AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html)
- [Preços AWS Step Functions](https://aws.amazon.com/step-functions/pricing/)
