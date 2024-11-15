## Engenharia de Prompts na AWS com Claude

### :computer: Desafio de projeto: Criando um Personal Trainer IA com Boas Práticas de Prompt Engineer

### Objetivo do desafio:

Confira a descrição completa em [prompt-challenger-personal-ia](https://github.com/digitalinnovationone/prompt-challenger-personal-ia).


> Este projeto visa criar um assistente de personal trainer automatizado que ajuda a gerar treinos personalizados. O usuário fornecerá informações como o biotipo corporal, a quantidade de dias disponíveis para treinar na semana e o tipo de exercício preferido, e o assistente gerará um plano de treino ideal com base nessas informações.

### Pré-requisitos

- Serviço: AWS
- Aplicação: Amazon Bedrock
- Modelos LLM: Claude 3

> Verifique as documentações sobre lbieração e preços para utilização do Amazon Bedrock.

### Exemplo Prático

Carregue o prompt [prompt_aws_bedrock_v1.md](prompt_aws_bedrock_v1.md) no playground do Amazon Bedrock e cite uma entrada como a descrita a seguir:

```console
Entrada do usuário:
Tipo corporal endomorfo. 3 dias para treinar. Tipos de exercícios Maquinário, Peso Livre e HIIT.
```

### Conclusão

A utilização e ajustes dos prompts com esses modelos no Amazon Bedrock é bem prática, fornece diversas integrações para que sirvam de base para inumeras aplicações. Um ponto de atenção são os preços para utilização. Considerando os valores, uma alternativa é o desenvolvimento de uma aplicação com Ollama, Langflow e Streamlit. [Clique aqui para ver a solução](#)

---

**Referências:**

- [Getting started](https://docs.aws.amazon.com/pt_br/bedrock/latest/userguide/getting-started.html)
- [Amazon Bedrock](https://aws.amazon.com/pt/bedrock/)
- [Acessar modelos](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access.html)
- [Preços do Amazon Bedrock](https://aws.amazon.com/pt/bedrock/pricing/?refid=82b1c10f-8aa4-4e6c-ab52-c75550a4a31e)