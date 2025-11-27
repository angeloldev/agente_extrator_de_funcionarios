# Agente Extrator de Entidades

*Visão geral* - O Agente Extrator de Entidades é um excelente caso de uso para demonstrar a eficácia do watsonx Orchestrate em extrair campos, entidades e informações encontradas em documentos inseridos pelo usuário.

‼️ É fundamental praticar engenharia de prompt, pois a forma como você formula a pergunta impacta diretamente a resposta do modelo e prompts mal elaborados podem levar a respostas incorretas ou a conteúdo inseguro. 

🧪 Este laboratório foi projetado para ajudá-lo a desenvolver habilidades práticas na criação, teste e ajuste de agentes.


## I. Criando e configurando agente

- Após acessar o watsonx Orchestrate, clique em **Create New Agent** <img src="./assets/create_agent.png" width=2% height=2%>. Role a página e selecione a aba **watsonx**.

Quando estiver na página Create an agent, coloque o nome e a descrição a seguir e clique em **Create**.

```
Agente Extrator de Funcionários
```
```
Esse agente ajuda a extrair entidades, campos e informações de funcionários em um documento enviado pelo usuário.
```

<img src="./assets/create_an_agent.png" width=75% height=75%>

### Modelo

Selecione **GPT-OSS 120B — OpenAI (via Groq)** como modelo do agente.

<img src="./assets/modelo.png" width=75% height=75%>

> [!NOTE]
> 💬 Neste caso de uso não precisamos adicionar um Knowledge (base de conhecimento) ao agente. A finalidade dele independe de um conhecimento prévio.

### Toolset

Selecione na barra lateral esquerda, ou role até **Toolset**, clique em **Add tool**, e escolha a opção **Agentic Workflow**.

<img src="./assets/add_tool.png" width=75% height=75%>
<img src="./assets/agentic_workflow.png" width=75% height=75%>

Através do Agentic Workflow, a ferramenta permite selecionar e arrastar atividades do usuário, ou do agente, até o fluxo de uma maneira dinâmica, rápida, intuitiva e simples.

Após colocar um nome, vamos começar o fluxo de trabalho que o agente deve percorrer ao longo do tempo de execução, pelo qual conseguirá extrair os campos desejados de um documento. 

1. Toque no ícone de "+" no canto superior esquerdo.
2. Selecione **User Activity** no menu flutuante, e arraste até a linha que liga **inputs** e **outputs**.
3. Dentro de User Activity (caixinha verde), clique em **Add** e depois na opção **File Upload**.
4. Agora, na linha externa, que liga User Activity até **outputs**, selecione **Document Extractor**

Todas essas etapas são realizadas no gif abaixo:

<img src="./assets/criacao_flowbuild.gif" width=75% height=75%>

Concluídas as etapas acima, um janela em **Document Extractor** se abrirá. Nela, selecione **Unstructred**.

<img src="./assets/doc_extractor_options.png" width=75% height=75%>

> [!NOTE]
> 💬 A opção **Structured** é utilizada em documentos que apresentam boa legibilidade, organização e padrões de escrita, que parecem sempre iguais. Exemplos: faturas, identidades, declarações fiscais.
> Caso seja um documento que apresente informações com um layout inconsistente, utilize a **Unstructured**. Exemplos: e-mails, relatórios.

Baixe o [perfil_de_funcionários](./assets/perfil_funcionarios.pdf) e faça o upload do arquivo.

<img src="./assets/drop_files.png" width=75% height=75%>

Nesta etapa, vamos adicionar os campos de interesse dentro do documento. É necessário que adicionemos alguns exemplos a fim de aprendizado do modelo, demonstrando um melhor direcionamento de entidades presentes no arquivo.

Vamos implementar desde a identificação dos campos, até o tratamento destes para melhores resultados.

Selecione a opção **Add field** e coloque um campo presente no documento, utilizaremos {nome do funcionario} como exemplo.

<img src="./assets/add_field.png" width=75% height=75%>
<img src="./assets/nome_funcionario.png" width=75% height=75%>

O modelo retorna o primeiro nome de funcionário encontrado, mas podemos ensiná-lo a identificar outros nomes!

<img src="./assets/maria_silva.png" width=75% height=75%>

Passando o cursor do mouse sobre o campo, um ícone aparecerá à direita, onde podemos realizar esse ajuste.

<img src="./assets/edit_field.png" width=75% height=75%>
<img src="./assets/edit-screen.png" width=75% height=75%>

Agora, podemos conceder uma pequena descrição, e um exemplo de entrada e saída para o modelo entender o que deve retornar quando o usuário solicitar aquele campo específico.

<img src="./assets/edit_field.png" width=75% height=75%>

> [!NOTE]
> 💬 Para ser ainda mais eficiente e específico, ao criar o exemplo, podemos inserir o input, e ao selecionar o campo de output, identificamos manualmente o campo desejado no documento com o cursor do mouse como mostra o gif a seguir!
> <img src="./assets/identificao_field.png" width=75% height=75%>




