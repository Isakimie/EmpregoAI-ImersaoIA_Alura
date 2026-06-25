# EmpregoAI
### Seu Orquestrador Inteligente de Carreira e Recolocação Profissional

O **EmpregoAI** é um ecossistema inteligente de suporte à carreira desenvolvido especialmente para a **Imersão IA Alura 2026**. O projeto utiliza o conceito de **Sistemas Multiagentes** para automatizar e otimizar a busca por recolocação profissional, capacitação técnica e preparação para processos seletivos.

A aplicação foi construída utilizando o editor de código de alta performance **Zed** e centraliza a inteligência de seus agentes através da API do **OpenRouter**, permitindo flexibilidade e robustez na escolha dos modelos de linguagem (LLMs).

---
## 📋 Passo a Passo para Execução

## 1.0 Preparação

### 1.1 Instalação e Configuração Inicial

1. **Instale o Zed:** Baixe e instale o editor de código através do site oficial [zed.dev](https://zed.dev/).
2. **Configure o OpenRouter:** Crie uma conta em [openrouter.ai](https://openrouter.ai/), gere sua chave de API e copie-a.
   > 🔐 **Dica de Segurança:** Salve suas chaves em um gerenciador de senhas criptografado ou em um local seguro de sua preferência. Nunca exponha suas credenciais diretamente no código.

### 1.2 Configuração do Firecrawl (Web Scraping Avançado)

Para garantir que a nossa IA consiga buscar dados na web sem sofrer bloqueios ou CAPTCHAs, vamos utilizar o **Firecrawl**. Siga os passos abaixo para preparar o seu ambiente:

1. **Instale o NVM para Windows:** Baixe o instalador do gerenciador de versões do Node.js através do link: [github.com/coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows).
2. **Liberar Execução de Scripts:** Ao final da instalação, abra o **PowerShell** e execute o comando abaixo para permitir a execução de scripts locais sem restrições de bloqueio:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
3. **Instalar e Ativar o Node.js:** No mesmo terminal do PowerShell, instale a versão mais recente do Node.js para habilitar globalmente os comandos `npm` e `npx`:
```
nvm install latest
```
Caso a versão seja diferente, confirme a ativação para usar a versão mais recente instalada, no meu caso:  `nvm use  26.3.0`.

Isso garante que você tenha total liberdade para gerenciar e usar qualquer versão do Node.js via terminal.

4. **Inicializar o Firecrawl CLI:** Crie uma conta gratuita em [firecrawl.dev](firecrawl.dev), obtenha sua API Key e execute o comando no PowerShell para inicializar:
```
npx -y firecrawl-cli@latest init --all -k [SUA CHAVE DE API]
```
### 1.3 Configuração do Ambiente e do Provedor de IA

Com as ferramentas preparadas, siga os passos abaixo para configurar o seu ambiente de desenvolvimento e conectar a inteligência artificial dentro do editor:

1. **Criar a Pasta do Projeto:** Crie um novo diretório (pasta) em seu computador para armazenar todos os arquivos do **EmpregoAI**.
2. **Abrir no Zed:** Inicialize o editor Zed e abra a pasta que você acabou de criar.
3. **Ativar o Assistente de IA:** Acesse o painel do assistente integrado clicando no ícone de **estrelas** localizado no canto inferior esquerdo da tela (ou utilize o atalho `Ctrl + B`).
4. **Configurar o Provedor (OpenRouter):** No painel do assistente, clique em **Configure Providers**, selecione a opção **OpenRouter**, cole a sua chave de API gerada anteriormente e pressione `Enter`.
5. **Selecionar o Modelo:** No menu superior do painel de IA, clique em **Auto Router** (ou no seletor de modelos) e escolha o modelo gratuito (*free*) de sua preferência para começar a rodar os agentes.
 > 💡 Neste projeto, foi utilizado o *****, mas a escolha do modelo fica a seu critério, visto que a disponibilidade de modelos gratuitos pode variar ao longo do tempo

## 2.0 Planejamento do Agente (Estrutura)

Para criar um agente eficiente, precisamos delegar as funções da maneira mais detalhada possível. Nosso planejamento seguirá a seguinte estrutura:

* **a)** O que vamos criar, onde e para qual finalidade (contexto geral de maneira objetiva).
* **b)** Tipo de orquestrador e objetivo (é recomendado dar um nome para esse orquestrador para facilitar).
* **c)** Descrição do primeiro agente a ser criado (solicitando que ele **não** seja criado agora, para implementarmos pouco a pouco).
* **d)** Especialização do agente, atribuindo uma habilidade (*skill*) a ele (isso é o que difere um agente de IA de um chatbot comum).
* **e)** Rotina do maestro em uma lista separada para definir como funcionará o fluxo de trabalho (*playbook*).
* **f)** Passo a passo detalhado do que o maestro deve fazer.
* **g)** O plano protótipo está pronto e pode rodar.

Abaixo segue o script para a criação do projeto **EmpregoAI**:

```
Vamos construir um plano no arquivo plano.md para criar um orquestrador que busca vagas de emprego:

- precisamos ter um agente no qual consiga se comunicar conosco, vamos chama-lo de maestro ele deve levar
nossas demandas para agentes especificos
- o primeiro a ser criado deve ser o agente que busca vagas de emprego, mas crie ele agora, apenas o coloque
no plano
- temos que dar um habilidade (skills) ao maestro de como delegar trabalho usando a sua ferramenta nativa de
despacho de agentes

0 playbook do maestro deve seguir a seguinte sequencia:

- Uma saudação ao usuário
- Deve conferir se existe um quiz das habilidades e preferencia do usuario
- Caso não exista, enviar as 5 perguntas para conhecer o usuário (anote as perguntas no plano)
- Disponibilizar um menu de opções ao usuario:
a) responder o quiz
b)buscar vagas de emprego futuramente
```

Exclua o arquivo `plano.md` gerado e substitua-o por:
> 💡 Essa substituição é necessária para eliminar diretrizes genéricas e garantir que o orquestrador siga estritamente as regras, o escopo e a arquitetura personalizada que definimos para o projeto.

``````

# Maestro — Orquestrador

## Visão Geral

Sistema multi-agente que auxilia usuários em sua jornada de desenvolvimento de carreira, combinando busca de empregos, identificação de lacunas de habilidades, recomendações de cursos e simulação de entrevistas.

**Objetivo**: Criar o Maestro — orquestrador que saúda, conduz o quiz, gera o perfil do usuário e apresenta o menu.

## Diretrizes para Modelos MoE

Todas as personas e skills são projetadas para modelos Mixture of Experts (MoE). Siga estas regras:

- Sem instruções ambíguas. Cada passo deve especificar exatamente o que fazer, qual ferramenta usar e qual formato de saída produzir.
- Sem tabelas markdown em nenhuma saída. Use listas numeradas com pares chave-valor para dados estruturados.
- Todos os caminhos de arquivo devem ser relativos à raiz do projeto com prefixo explícito `data/`. O workspace atual já é a raiz do projeto.Todos os caminhos devem ser relativos à raiz: data/, personas/, skills/, AGENTS.md.
- Se uma ferramenta falhar, o agente deve relatar a falha no campo `erros` e não continuar silenciosamente.
- Nunca invente dados. Se uma busca web falhar, reporte o erro exato e pare. **Exceção**: Em `skills/course-analysis.md`, se a busca falhar para uma habilidade específica, tente o fallback; se o fallback também falhar, pule essa habilidade e continue com as restantes.
- O agente NÃO deve escrever scripts Python, scripts de shell ou qualquer código para implementar personas. O agente personifica cada papel diretamente através do seu comportamento e respostas conversacionais. Personas são instruções comportamentais, não código a ser gerado.

## Arquitetura

```
┌─────────────────────────────────────────────────┐
│                  Usuário                          │
└────────────────────┬────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────┐
│              MAESTRO (Orquestrador)              │
│  - Interface principal com o usuário             │
│  - Coordena os agentes especializados            │
│  - Consolida resultados e apresenta ao usuário   │
└──┬──────────────┬──────────────┬────────────────┘
   │              │              │
   ▼              ▼              ▼
┌─────────┐  ┌──────────┐  ┌──────────────┐
│ SCOUT   │  │ CURATOR  │  │ COACH        │
│ (Busca  │  │ (Busca   │  │ (Simulação   │
│  de     │  │  de      │  │  de          │
│  Vagas) │  │  Cursos) │  │  Entrevistas)│
└─────────┘  └──────────┘  └──────────────┘
```

**Escopo**: Apenas o bloco Maestro. Os outros agentes serão construídos nas fases seguintes.

## Estrutura de Diretórios

```
empregoAI/
├── AGENTS.md                   # Instruções de inicialização para o agente
├── personas/
│   └── maestro.md          # Orquestrador principal
├── skills/
│   └── dispatch.md         # Despacho de agentes e protocolo de handoff
└── data/
    ├── personality-quiz.md       # Quiz de personalidade do usuário
    └── user-profile.md           # Perfil consolidado derivado do quiz
```

## Tasks

### 1. Criar `AGENTS.md`

```
**LEIA E ADOTE IMEDIATAMENTE A PERSONA EM `personas/maestro.md`**

Você É o Maestro — um assistente de desenvolvimento de carreira conversacional. Você NÃO deve escrever scripts Python, scripts de shell ou qualquer código para implementar a persona Maestro. Você a personifica diretamente através do seu comportamento e respostas.

**REGRAS CRÍTICAS:**
- NÃO crie scripts ou programas para agir como o agente
- NÃO escreva código que "implemente" a lógica da persona
- Você É o agente — interaja com o usuário de forma conversacional
- Use as ferramentas do Zed (`spawn_agent`, `terminal`, `find_path`) conforme descrito na persona para coordenar tarefas
- Todo estado é armazenado em arquivos Markdown em `data/` — leia e escreva esses arquivos diretamente

6. Mostrar o menu novamente

## Esquemas dos Arquivos de Dados

### data/personality-quiz.md

```
Área de interesse: [valor]
Nível de experiência: [valor]
Preferências de trabalho: [valor]
Localização: [valor]
Soft skills: [valor]
Objetivo de carreira: [valor]
Habilidades atuais: [valor]
Concluído: [true | false]
```

Um quiz está completo apenas quando todas as seções estão preenchidas e `Concluído` é `true`.

### data/user-profile.md

Gerado a partir de `personality-quiz.md`. Mesmos campos, mais `Funções alvo`:

```
Área de interesse: [valor]
Nível de experiência: [valor]
Preferências de trabalho: [valor]
Localização: [valor]
Soft skills: [valor]
Objetivo de carreira: [valor]
Habilidades atuais: [valor]
Funções alvo: [lista separada por vírgulas]
Concluído: [true | false]
```

**Mapeamento de funções alvo (hardcoded no maestro.md):**
1. Frontend + Júnior: Desenvolvedor Frontend, Desenvolvedor UI Júnior, Desenvolvedor Web
2. Frontend + Pleno: Engenheiro Frontend, Desenvolvedor UI, Desenvolvedor React
3. Frontend + Sênior: Engenheiro Frontend Sênior, Líder de Desenvolvimento UI, Arquiteto Frontend
4. Backend + Júnior: Desenvolvedor Backend, Desenvolvedor API Júnior, Desenvolvedor de Software
5. Backend + Pleno: Engenheiro Backend, Desenvolvedor API, Desenvolvedor Python/Java
6. Backend + Sênior: Engenheiro Backend Sênior, Arquiteto de Sistemas, Líder Técnico
7. Ciência de Dados + Júnior: Analista de Dados, Cientista de Dados Júnior, Analista BI
8. Ciência de Dados + Pleno: Cientista de Dados, Engenheiro de Machine Learning, Engenheiro de Dados
9. Ciência de Dados + Sênior: Cientista de Dados Sênior, Arquiteto ML, Líder IA
10. Mobile + Júnior: Desenvolvedor Mobile, Desenvolvedor iOS/Android Júnior
11. Mobile + Pleno: Desenvolvedor iOS, Desenvolvedor Android, Desenvolvedor React Native
12. Mobile + Sênior: Engenheiro Mobile Sênior, Arquiteto Mobile, Líder Flutter
13. DevOps + Júnior: Engenheiro DevOps Júnior, Suporte Cloud, SysAdmin
14. DevOps + Pleno: Engenheiro DevOps, Engenheiro Cloud, SRE
15. DevOps + Sênior: Engenheiro DevOps Sênior, Arquiteto Cloud, Líder de Plataforma
16. Full Stack + Júnior: Desenvolvedor Full Stack, Desenvolvedor Web Júnior
17. Full Stack + Pleno: Engenheiro Full Stack, Desenvolvedor de Aplicações Web
18. Full Stack + Sênior: Engenheiro Full Stack Sênior, Líder Técnico, Arquiteto de Soluções
19. Governança de Dados + Júnior: Analista de Governança de Dados Júnior, Gestor de Dados Júnior, Assistente de Compliance
20. Governança de Dados + Pleno: Analista de Governança de Dados, DPO, Analista de Qualidade de Dados
21. Governança de Dados + Sênior: Head de Governança de Dados, Diretor Chefe de Dados, Líder de Arquitetura de Dados
22. Design UX + Júnior: Designer UX Júnior, Assistente UI/UX, Pesquisador UX Jr
23. Design UX + Pleno: Designer UX, Pesquisador UX, Designer de Produto
24. Design UX + Sênior: Designer UX Sênior, Líder UX, Head de UX
25. Design UI + Júnior: Designer UI Júnior, Designer Visual Jr, Assistente de Design System
26. Design UI + Pleno: Designer UI, Designer Visual, Designer de Interação
27. Design UI + Sênior: Designer UI Sênior, Líder UI, Arquiteto de Design System
28. Liderança + Júnior: Líder de Equipe Júnior, Coordenador de Projetos, Scrum Master Jr
29. Liderança + Pleno: Gerente de Engenharia, Gerente de Projetos, Agile Coach
30. Liderança + Sênior: Diretor de Engenharia, VP de Tecnologia, CTO
31. RH + Júnior: Analista de RH Júnior, Assistente de Aquisição de Talentos, Coordenador de RH
32. RH + Pleno: Analista de RH, Recrutador, Especialista em Operações de Pessoas
33. RH + Sênior: Gerente de RH, Head de Pessoas, Diretor de Talentos
34. Marketing de Mídias Sociais + Júnior: Assistente de Mídias Sociais, Criador de Conteúdo Jr, Community Manager Jr
35. Marketing de Mídias Sociais + Pleno: Gerente de Mídias Sociais, Estrategista de Conteúdo, Analista de Marketing Digital
36. Marketing de Mídias Sociais + Sênior: Head de Mídias Sociais, Diretor de Mídias Sociais, Líder Estrategista de Marca
37. Growth Marketing + Júnior: Assistente de Growth Marketing, Analista de Marketing Jr, Marketing de Performance Jr
38. Growth Marketing + Pleno: Growth Marketer, Gerente de Marketing de Performance, Especialista CRO
39. Growth Marketing + Sênior: Head de Growth, Diretor de Growth, VP de Marketing
40. Gestão de Produtos + Júnior: Analista de Produto, Gerente de Produto Associado, Product Owner Jr
41. Gestão de Produtos + Pleno: Gerente de Produto, Product Owner, Gerente de Produto Técnico
42. Gestão de Produtos + Sênior: Gerente de Produto Sênior, Head de Produto, VP de Produto
43. Cibersegurança + Júnior: Analista de Segurança Júnior, Analista SOC, Assistente de Segurança da Informação
44. Cibersegurança + Pleno: Engenheiro de Segurança, Testador de Penetração, Consultor de Segurança
45. Cibersegurança + Sênior: Engenheiro de Segurança Sênior, CISO, Líder Arquiteto de Segurança

## Fluxo

```
1. Usuário abre o agente
        │
        ▼
2. Maestro saúda e verifica o quiz
        │
        ├─ Quiz ausente/incompleto → perguntar se deseja continuar ou recomeçar → se continuar, completar quiz; se recomeçar, guiar pelo quiz → salvar user-profile.md
        ├─ Quiz existente completo → carregar user-profile.md diretamente
        ▼
3. Maestro apresenta menu: A (vagas), B (cursos), C (entrevista), D (refazer quiz)
```

As opções A, B e C ainda não funcionam — serão implementadas nas fases seguintes. A opção D (refazer quiz) funciona neste plano.

## Notas Técnicas

- **Orquestração**: Roda dentro do editor Zed usando `spawn_agent` para despacho de sub-agentes. Nenhum framework externo necessário.
- **Armazenamento de estado**: Todos os dados em arquivos Markdown sob `data/`.
- **Simplicidade**: Sem cache, sem IDs de sessão, sem pontuação complexa. Cada agente faz uma coisa e retorna resultados diretamente.

## Testes

- Agente saúda o usuário
- Detecta quiz ausente e guia pelo quiz
- Salva `user-profile.md` com o mapeamento correto de funções alvo
- Mostra o menu com opções A/B/C/D
- Opção D (refazer quiz) funciona

## Entregável

Maestro totalmente funcional com quiz e menu.

``````
> *Para consultar a estrutura de referência oficial da Imersão, você também pode acessar o [Plano da Aula 1 Original](https://github.com/guilhermeonrails/i-agente-ia/blob/main/PLAN-AULA-1.md).*


***************PAREI AQUI

então peça para "implementar o @plano.md"
Aceite a criação dos agentes
e por fim clique em Keep All para manter todos os arquivos que foram criados e vc pode perceber que todos eles estão na barra lateral direita

Agora vamos no + para criar uma nova conversa sem contexto com Zed Agente
Imagem_02

Agora vamos pedir "Leia e siga o @AGENTS.md" pois nessa nova conversa não temos contexto algum, e para não precisar ficar pedindo já vamos entrega o contexto novamente
Perceba que ele criou separadamente 
*aqui firecrawl
Voltando ao nosso projeto:
1. Abra uma nova janela de conversa igual que fizemos anteriormente: + e Zed Agent
" Baseado no @plano.md , crie um segundo plano nomeado plano-segundo e nele tenha o planejamento para a acriação do agente buscador de vagas que chamamos de scout.

Esse agente deve utilizar a ferramenta firecrawl já instalada e disponível para ser executada como linha de comando. Caso essa ferramenta não funcione, utilize a ferramenta de acesso web que você tem nativamente. Crie esse procedimento dentro da skills.

Busque em sites como por exemplo: infojobs, vagas e indeed."

 Abra uma nova janela de conversa igual que fizemos anteriormente: + e Zed Agent
" Já temos parte do projeto implementado seguindo o @plano.md . Agora gostaria que você implemente o @plano-segundo.md "

Em Ctrl + J, no terminal confirme a instalação do node com:
node --version
Se ele retornou a versão está tudo certo e pode fechar o terminal
*********
 Abra uma nova janela de conversa igual que fizemos anteriormente: + e Zed Agent para ver se todas as perguntas estão funcionando bem
" Leia e siga o @AGENT.md "
Faca o teste
Imagem_03

 Abra uma nova janela de conversa igual que fizemos anteriormente: + e Zed Agent:

 "
 Agora vamos construir o terceiro plano chamado plano-terceiro.md para continuar o que já temos implementados seguindo o plano @plano.md e o @plano-segundo.md

 Desta vez, planeje um terceiro agente chamado curator que vai realizar a buscar de cursos na alura.com.br

 Ele deve navegar um site da alura.com.br usando o firecrawl assim como fizemos com o scout.

 Busque por cursos que complementem as habilidades faltantes para o usuario em relação as vagas de acordo com o quiz e as vagas encontradas.
 "
 Depois de tudo certo peça para implementar

 Agora vamos ver se tudo deu certo abra uma nova janela de conversa e peça: Leia e siga o @AGENTS.md

 Teste respondendo as perguntas
