
### https://rag-serenatto-cafes.vercel.app/

# Projeto Langflow: Chatbot Inteligente com Base de Conhecimento
### No Code

Este projeto utiliza o Langflow para criar um chatbot inteligente capaz de responder a perguntas com base em um conhecimento específico fornecido através de arquivos.

## Visão Geral da Arquitetura

A arquitetura deste chatbot é construída com os seguintes componentes do Langflow:

1.  **`File`**: Responsável por carregar dados de diversos tipos de arquivos (texto, PDF, etc.).
2.  **`SplitText`**: Segmenta o conteúdo dos arquivos carregados em partes menores (chunks) para facilitar o processamento e a busca.
3.  **`Google Generative AI Embeddings`**: Cria representações numéricas (embeddings) dos chunks de texto, capturando seu significado semântico. Isso é feito em duas instâncias: uma para os dados do conhecimento e outra para a consulta do usuário.
4.  **`Chroma`**: Um banco de dados vetorial onde os chunks de texto e seus respectivos embeddings são armazenados, permitindo buscas semânticas eficientes.
5.  **`ChatInput`**: Interface para receber a pergunta (mensagem) do usuário.
6.  **`ParserComponent`**: Componente para processar os dados recuperados do banco de dados vetorial.
7.  **`Memory`**: Gerencia o histórico da conversa, permitindo interações mais contextuais.
8.  **`Prompt`**: Constrói a instrução final para o modelo de linguagem, combinando a pergunta do usuário, o contexto relevante recuperado e o histórico da conversa.
9.  **`GroqModel`**: O modelo de linguagem grande (LLM) utilizado para gerar a resposta com base no prompt construído.
10. **`ChatOutput`**: Exibe a resposta gerada pelo modelo de linguagem ao usuário.

**Fluxo de Dados:**

1.  **Ingestão de Conhecimento:**
    * Um ou mais arquivos são carregados com o componente `File`.
    * O texto é dividido em chunks menores usando `SplitText`.
    * Embeddings desses chunks são gerados com `Google Generative AI Embeddings` e armazenados no banco de dados `Chroma`.

2.  **Processamento da Conversa:**
    * A pergunta do usuário é recebida pelo `ChatInput`.
    * A pergunta é convertida em um embedding usando `Google Generative AI Embeddings`.
    * Esse embedding é usado para buscar informações relevantes no `Chroma`.
    * Os resultados da busca são processados pelo `ParserComponent`.
    * Um `Prompt` é criado, combinando a pergunta do usuário, o contexto recuperado do `Chroma` e o histórico da conversa (`Memory`).
    * O `GroqModel` processa o prompt e gera uma resposta.
    * A resposta é exibida ao usuário através do `ChatOutput`.

## Status da Aplicação

Devido à hospedagem via Hugging Face, a aplicação pode entrar em estado de suspensão após um período de inatividade.

**Atualmente, o chatbot pode estar offline.**

Se você deseja vê-lo em funcionamento, por favor, me avise, e eu posso ativá-lo para uma demonstração.

## Como Usar (Após Ativação)

1.  Acesse o link da aplicação (se disponível publicamente).
2.  Interaja com a interface de chat, fazendo suas perguntas.

## Próximos Passos

* Melhorar a lógica do prompt para obter respostas mais concisas ou detalhadas.
* Implementar diferentes estratégias de divisão de texto.
* Explorar outras opções de modelos de linguagem ou bancos de dados vetoriais.
* Adicionar funcionalidades como upload de arquivos dinâmico.


---
