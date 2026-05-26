# EmpregoAI
## Agente criado para a Imersão IA da Alura 2026

Este projeto guia você na criação de um agente orquestrador inteligente utilizando o editor de código **Zed** e a API do **OpenRouter**.

---

### 1.0 Preparação

1. **Instale o Zed:** Baixe e instale o editor através do site oficial [zed.dev](https://zed.dev/).
2. **Configure o OpenRouter:** Crie uma conta em [openrouter.ai](https://openrouter.ai/), gere sua chave de API e copie-a.
   > **Dica de Segurança:** Salve sua chave em um gerenciador de senhas criptografado ou em um local seguro de sua preferência.

---

### 1.1 Configuração do Ambiente e do Provedor de IA

1. Com o Zed instalado, crie uma pasta(diretório) no seu computador para armazenar os arquivos do projeto.
2. Abra essa pasta no Zed.
3. Acesse o painel do assistente do Zed clicando no ícone de **estrelas** no canto inferior esquerdo (ou use o atalho `Ctrl + B`).
4. Clique em **Configure Providers**, selecione **OpenRouter**, cole a sua chave de API e pressione `Enter`.
5. No painel superior, clique em **Auto Router** (ou no seletor de modelos) e escolha um modelo gratuito (*free*) de sua preferência.

---

### 2.0 Planejamento do Agente (Estrutura)

Para criar um agente eficiente, precisamos delegar as funções da maneira mais detalhada possível. Nosso planejamento seguirá a seguinte estrutura:

* **a)** O que vamos criar, onde e para qual finalidade (contexto geral de maneira objetiva).
* **b)** Tipo de orquestrador e objetivo (é recomendado dar um nome para esse orquestrador para facilitar).
* **c)** Descrição do primeiro agente a ser criado (solicitando que ele **não** seja criado agora, para implementarmos pouco a pouco).
* **d)** Especialização do agente dando uma habilidade (*skill*) a ele (isso é o que difere um agente de IA de um chatbot comum).
* **e)** Rotina do maestro em uma outra lista para definir como funcionará o fluxo de trabalho (*playbook*).
* **f)** Passo a passo detalhado do que o maestro deve fazer.
* **g)** o plano prototipo esta pronto pode rodar

Abaixo segue o meu script para criação do projeto EmpregoAI
Imagem_01

