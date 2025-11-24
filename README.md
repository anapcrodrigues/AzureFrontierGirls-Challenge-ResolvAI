# Desafio do Azure Frontier Girls de AI Foundry

## Azure Frontier Girls – Build Your First Copilot Challenge (Foundry Edition)

# ResolvAI - Assistente de Diagnóstico

## 📌 Descrição do Projeto

O **ResolvAI** é um agente desenvolvido no **Azure AI Foundry** com o objetivo de apoiar técnicos de TI na identificação de problemas comuns reportados em tickets de suporte. Ele conduz uma conversa estruturada com o usuário, coletando informações adicionais e organizando hipóteses de diagnóstico para que o técnico possa **resolver o chamado de forma mais rápida e eficiente**.

## 🎯 Objetivo do Agente

- Conduzir perguntas de diagnóstico em fluxo lógico (hardware → software → rede → acesso).
- Extrair detalhes relevantes que auxiliem o técnico na resolução.
- Fornecer uma lista de possíveis causas e soluções ao técnico e usuário.

## 📊 Benefícios

- Redução do tempo médio de resolução de chamados.
- Padronização do processo de diagnóstico.
- Apoio a técnicos menos experientes com um guia interativo.

## 🤖 Criação do Agente

O **ResolvAI** foi desenvolvido no Azure AI Foundry seguindo as etapas de infraestrutura e configuração abaixo:

### Criação de um Grupo de Recursos

1. Acesse o [Portal do Azure](https://portal.azure.com).
2. Faça assinatura.
3. Clique em "+ Criar um recurso".
4. Localize "Grupo de recursos" e clique em "Criar".
5. Faça as configurações obrigatórias, como `Nome do grupo de recursos` e `Região`.
6. Para o grupo de recursos utilizado para o **ResolvAI**, selecionei a região `East US`.

### Criação de um Agente no Foundry

1. Acesse o [Portal do Azure AI Foundry](https://ai.azure.com).
2. Clique em "Comece a criar" e em seguida, "Criar agente"
![Criar agente](01_criar-recurso-foundry/01_criar-agente.png)
3. Dê um nome para o agente, **ResolvAI**.
4. Selecione qual modelo de IA deseja implantar, `gpt-4o-mini`.
![Selecione modelo de IA](03_criar-agente/02_modelo-ia.png)
5. Defina os parâmetros Temperatura e Top P do modelo para 0,3 e 0,3, respectivamente.
> Temperatura: Controla a aleatoriedade. Abaixar a temperatura significa que o modelo produzirá respostas mais repetitivas e determinísticas. Aumentar a temperatura resultará em respostas mais inesperadas ou criativas.
> Top P: Semelhante à temperatura, isso controla a aleatoriedade, mas usa um método diferente. Abaixar o Top P restringirá a seleção de tokens do modelo para tokens mais prováveis. Aumentar o Top P permitirá que o modelo escolha tokens com alta e baixa probabilidade.
6. Defina o Formato de texto como "Texto".
7. Passe as instruções do agente de acordo com o script abaixo:
**Script de instruções**
```
Você é um Assistente de Diagnóstico especializado em suporte técnico de TI. Sua função é ajudar técnicos a identificar problemas comuns a partir de tickets recebidos e interagir com o usuário para coletar informações adicionais.
Objetivo:
- Interpretar a descrição inicial do ticket.
- Conduzir uma conversa estruturada com o usuário, fazendo perguntas de diagnóstico.
- Extrair detalhes relevantes que auxiliem o técnico na resolução.
- Sugerir soluções práticas ou encaminhar para suporte avançado quando necessário.
Entrada: Um ticket contendo a descrição do problema relatado pelo usuário.
Instruções de interação:
- Leia atentamente o ticket e identifique os sintomas principais.
- Inicie o diálogo com o usuário para confirmar ou detalhar os sintomas.
- Faça perguntas simples e objetivas, seguindo um fluxo lógico:
    Hardware: "O computador liga normalmente?", "Há ruídos ou sinais físicos incomuns?"
    Software: "Há mensagens de erro na tela?", "O sistema está lento ou travando?"
    Rede: "O dispositivo está conectado à internet?", "Outros usuários enfrentam o mesmo problema?"
    Acesso: "O usuário consegue entrar com suas credenciais em outro dispositivo?"
- Após cada resposta, refine suas hipóteses e avance para a próxima pergunta relevante.
- Após identificar uma ou mais possíveis soluções comuns, encerre a conversa encaminhando o atendimento para o suporte técnico especializado.
- A partir das soluções identificadas, descreva-as de forma clara e prática em uma lista para consulta do técnico que irá finalizar o atendimento do ticket.
- Mantenha o tom profissional, objetivo e colaborativo.
Regras:
- Não invente informações técnicas sem base.
- Sempre valide hipóteses com perguntas antes de sugerir soluções.
- Se não houver dados suficientes, peça mais detalhes ao usuário.
- Registre as respostas do usuário como parte do histórico do ticket.
- Não sugira soluções para o usuário.
- Forneça a lista de soluções em uma mensagem final direcionada para o técnico.
```
8. Adicione Ferramentas como **Pesquisa na Web** para que o agente aumente seu repertório e consiga realizar buscas na internet

## 🚀 Como Funciona

- O usuário abre o agente ResolvAI.
- Insire um ticket de suporte como entrada.
- Interaje com o agente respondendo às perguntas de diagnóstico.
- Ao final, o agente emite uma lista de causas e soluções para o técnico, o usuário e abriria o ticket na ferramenta de gestão de tickets.

# Execução do ResolvAI

![ResolvAI](01_ResolvAI.png)
![Interação ResolvAI](02_interacao-ResolvAI.png)
![Interação 2 ResolvAI](03_interacaoResolvAI.png)

## Thread Logs

![Log 1](04_log/01_log.png)
![Log 2](04_log/02_log.png)
![Log 3](04_log/03_log.png)

# Referências
- [Azure AI Foundry](https://ai.azure.com/)
- [Documentação de Agentes no Foundry](https://learn.microsoft.com/pt-br/azure/ai-foundry/?view=foundry-classic)
