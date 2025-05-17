````markdown
# Assistente Saúde - Seu Guia Inicial para o Cuidado com a Saúde 🩺🤖

Bem-vindo(a) ao repositório do Assistente Saúde! Este é um chatbot multiagente projetado para ajudar você a dar os primeiros passos quando surgem dúvidas sobre sintomas e qual caminho seguir para buscar ajuda médica.

## 🤔 Qual problema o Assistente Saúde busca resolver?

Muitas vezes, quando começamos a sentir algo diferente em nosso corpo, como uma dor persistente ou um mal-estar, a primeira dúvida que surge é: "O que pode ser isso?" e, em seguida, "Qual médico eu deveria procurar?". Navegar por informações de saúde online pode ser confuso e, às vezes, até mesmo alarmante.

O Assistente Saúde foi criado para oferecer uma **orientação inicial amigável e organizada**. Ele não tem a intenção de dar diagnósticos (isso é tarefa para profissionais de saúde!), mas sim de:

1.  Ajudar você a organizar seus sintomas.
2.  Sugerir, com base nos sintomas informados, possíveis áreas da medicina e especialidades médicas relacionadas.
3.  Indicar qual especialidade médica poderia ser a mais adequada para uma primeira consulta.
4.  Facilitar a busca por clínicas ou consultórios dessa especialidade próximos à sua localidade.

Nosso objetivo é diminuir a ansiedade inicial e direcionar você de forma mais informada para o cuidado profissional adequado.

**⚠️ IMPORTANTE: O Assistente Saúde é uma ferramenta de auxílio e informação preliminar. Ele NÃO SUBSTITUI uma consulta médica, diagnóstico ou tratamento profissional. Sempre consulte um médico para questões de saúde.**

## ✨ Como o Assistente Saúde funciona?

O Assistente Saúde é construído como um sistema multiagente. Isso significa que diferentes "agentes" (pequenos programas especializados) trabalham em conjunto, cada um com uma tarefa específica:

1.  **Agente Coletor de Sintomas:** Conversa com você para entender o que você está sentindo.
2.  **Agente de Pesquisa:** Utiliza a inteligência artificial do Google Gemini para cruzar seus sintomas com possíveis condições e especialidades médicas relacionadas.
3.  **Agente Determinador de Especialidade:** Analisa os resultados da pesquisa para sugerir qual especialidade médica parece ser o melhor ponto de partida.
4.  **Agente de Busca Local:** Se você desejar, ele pergunta sua cidade e estado.
5.  **Agente Buscador de Clínicas:** Com sua permissão e localização, ele usa o Google Maps para encontrar clínicas ou consultórios da especialidade indicada próximos a você.

Um agente **Orquestrador** gerencia todo esse fluxo, garantindo que cada etapa aconteça na ordem correta.

## 🛠️ Tecnologias Utilizadas

* **Python:** Linguagem de programação principal.
* **Google Colab:** Ambiente de notebook online para fácil execução e teste.
* **Google Gemini API:** Para as funcionalidades de inteligência artificial generativa (análise de sintomas, sugestão de especialidades).
* **Google Maps API (Geocoding API & Places API):** Para a busca de clínicas e consultórios.

## 🚀 Como Testar o Assistente Saúde no Google Colab

Você pode testar o Assistente Saúde diretamente no seu navegador usando o Google Colab. Siga os passos abaixo:

### Pré-requisitos:

* Uma conta Google (para usar o Google Colab).
* Um navegador de internet (Chrome, Firefox, etc.).

### Passo 1: Obtenha suas Chaves de API (API Keys)

Para que o chatbot funcione, ele precisa acessar duas APIs do Google. Você precisará obter suas próprias chaves de API gratuitas (dentro dos limites de uso gratuito oferecidos pelo Google).

1.  **Google Gemini API Key:**
    * Acesse o [Google AI Studio](https://aistudio.google.com/).
    * Faça login com sua conta Google.
    * Crie um novo projeto ou use um existente.
    * Clique em "Get API key" (Obter chave de API) e siga as instruções para gerar sua chave. Guarde-a em um local seguro.

2.  **Google Maps API Key:**
    * Acesse o [Google Cloud Console](https://console.cloud.google.com/).
    * Crie um novo projeto ou selecione um existente.
    * No menu de navegação, vá para "APIs e Serviços" > "Biblioteca".
    * Procure e ative as seguintes APIs para o seu projeto:
        * **Geocoding API**
        * **Places API**
    * Depois de ativá-las, vá para "APIs e Serviços" > "Credenciais".
    * Clique em "Criar credenciais" > "Chave de API". Uma chave será gerada. Guarde-a em um local seguro.
    * **IMPORTANTE:** É altamente recomendável restringir sua chave de API do Google Maps para evitar uso não autorizado. Você pode restringi-la para ser usada apenas com as APIs que você ativou (Geocoding e Places).

### Passo 2: Acesse o Notebook no Google Colab

* Clique no link a seguir para abrir o notebook do Assistente Saúde no Google Colab:
    * **[COLOQUE O LINK DO SEU NOTEBOOK COLAB COMPARTILHÁVEL AQUI]**
    * *(Exemplo: `https://colab.research.google.com/drive/SEU_ID_DO_ARQUIVO?usp=sharing`)*
* Ao abrir, recomendamos que você salve uma cópia no seu próprio Google Drive ("Arquivo" > "Salvar uma cópia no Drive") para poder fazer alterações e executar livremente.

### Passo 3: Configure suas API Keys no Código

No notebook Colab que você abriu (ou na sua cópia), localize a **Célula 2**, que geralmente contém as importações e configurações de API. Você verá linhas como estas:

```python
# --- Configuração da API do Google Gemini ---
GOOGLE_API_KEY = "SUA_API_KEY_DO_GOOGLE_GEMINI_AQUI" # ATENÇÃO: Substitua pela sua chave
genai.configure(api_key=GOOGLE_API_KEY)

# --- Configuração da API do Google Maps ---
Maps_API_KEY = "SUA_API_KEY_DO_Maps_AQUI" # ATENÇÃO: Substitua pela sua chave
gmaps = googlemaps.Client(key=Maps_API_KEY)
````

  * Substitua `"SUA_API_KEY_DO_GOOGLE_GEMINI_AQUI"` pela chave de API do Google Gemini que você obteve no Passo 1.
  * Substitua `"SUA_API_KEY_DO_Maps_AQUI"` pela chave de API do Google Maps que você obteve no Passo 1.

**Atenção:** Mantenha suas chaves de API em segredo\! Não as compartilhe publicamente. Se você for compartilhar seu notebook, lembre-se de remover suas chaves ou avisar aos outros para inserirem as próprias.

### Passo 4: Execute as Células

As células de código no Colab precisam ser executadas em ordem.

1.  **Célula 1 (Instalação de Dependências):** Clique no botão "play" (▶️) ao lado da célula ou selecione a célula e pressione `Ctrl+Enter` (ou `Cmd+Enter` no Mac). Aguarde a instalação ser concluída.
2.  **Célula 2 (Importações e Configuração das APIs):** Execute esta célula da mesma forma. É aqui que suas chaves de API são carregadas.
3.  **Célula 3 (Definição dos Agentes):** Execute esta célula para definir todas as funções que compõem os agentes do chatbot.
4.  **Célula 4 (Agente Orquestrador e Loop Principal):** Execute esta célula para iniciar o chatbot\!

### Passo 5: Interaja com o Chatbot

Após executar a Célula 4, o Assistente Saúde começará a interagir com você diretamente no output da célula. Ele fará perguntas e você deverá digitar suas respostas e pressionar `Enter`.

Siga as instruções do chatbot. Ele perguntará sobre seus sintomas, mostrará os resultados da pesquisa, sugerirá uma especialidade e, se você quiser, buscará clínicas. Ao final, ele perguntará se você deseja refazer a pesquisa desde o início.

## 🤝 Contribuições

Se você tiver ideias para melhorar o Assistente Saúde, sinta-se à vontade para abrir uma *issue* neste repositório ou, se tiver familiaridade com Git e Python, enviar um *pull request*\!

## 📜 Aviso Legal Final

Reiteramos que o **Assistente Saúde é uma ferramenta experimental e educacional**. As informações fornecidas por ele são geradas por modelos de linguagem e APIs de busca, e **não constituem aconselhamento médico, diagnóstico ou indicação de tratamento**.

**Procure sempre a orientação de um médico qualificado ou outro profissional de saúde para quaisquer dúvidas que possa ter sobre uma condição médica.** Nunca desconsidere o aconselhamento médico profissional nem adie a sua procura por causa de algo que você leu ou interagiu com este chatbot.

-----

```

```
