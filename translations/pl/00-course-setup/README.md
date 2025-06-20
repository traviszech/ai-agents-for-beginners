<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "c729f7442eb5afd55b5522e3ad65c822",
  "translation_date": "2025-06-11T04:42:16+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "pl"
}
-->
Powinieneś teraz mieć własną, zforkowaną wersję tego kursu pod następującym linkiem:

![Forked Repo](../../../00-course-setup/images/forked-repo.png)

## Uruchamianie kodu

Ten kurs oferuje serię notatników Jupyter, które możesz uruchomić, aby zdobyć praktyczne doświadczenie w tworzeniu Agentów AI.

Przykłady kodu wykorzystują:

**Wymaga konta GitHub - darmowe**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Oznaczone jako (semantic-kernel.ipynb)  
2) AutoGen Framework + GitHub Models Marketplace. Oznaczone jako (autogen.ipynb)

**Wymaga subskrypcji Azure**:  
3) Azure AI Foundry + Azure AI Agent Service. Oznaczone jako (azureaiagent.ipynb)

Zachęcamy do wypróbowania wszystkich trzech typów przykładów, aby zobaczyć, który najlepiej Ci odpowiada.

Wybrana opcja określi, które kroki konfiguracji musisz wykonać poniżej:

## Wymagania

- Python 3.12+  
- Konto GitHub – dostęp do GitHub Models Marketplace  
- Subskrypcja Azure – dostęp do Azure AI Foundry  
- Konto Azure AI Foundry – dostęp do Azure AI Agent Service

W katalogu głównym repozytorium znajduje się plik `requirements.txt` z wszystkimi wymaganymi pakietami Pythona do uruchomienia przykładów kodu.

Możesz je zainstalować, uruchamiając następujące polecenie w terminalu, w katalogu głównym repozytorium:

```bash
pip install -r requirements.txt
```  
Zalecamy utworzenie wirtualnego środowiska Pythona, aby uniknąć konfliktów i problemów.

## Konfiguracja dla przykładów korzystających z GitHub Models

### Krok 1: Pobierz swój GitHub Personal Access Token (PAT)

Obecnie kurs korzysta z GitHub Models Marketplace, który oferuje darmowy dostęp do dużych modeli językowych (LLM), wykorzystywanych do tworzenia Agentów AI.

Aby uzyskać dostęp do tej usługi, musisz utworzyć GitHub Personal Access Token.

Można to zrobić, przechodząc do swojego konta GitHub.

Wybierz `Fine-grained tokens` option on the left side of your screen.

Then select `Generate new token`.

![Generate Token](../../../00-course-setup/images/generate-token.png)

You will be prompted to enter a name for your token, select the expiration date (Recommended: 30 Days), and select the scopes for your token (Public Repositories).

It's also necessary to edit the permissions of this token: Permissions -> Models -> Allows access to GitHub Models

Copy your new token that you have just created. You will now add this to your `.env` file included in this course. 


### Step 2: Create Your `.env` File

To create your `.env` i uruchom następujące polecenie w terminalu.

```bash
cp .env.example .env
```

To skopiuje plik przykładowy i utworzy plik `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

You should now be able to run the code samples of this course.

## Set Up for Samples using Azure AI Foundry and Azure AI Agent Service

### Step 1: Retrieve Your Azure Project Connection String


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Azure AI Foundry portal.

![Project Connection String](../../../00-course-setup/images/project-connection-string.png)

### Step 2: Create Your `.env` File

To create your `.env`. Uruchom następujące polecenie w terminalu.

```bash
cp .env.example .env
```

To skopiuje plik przykładowy i utworzy plik `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `PROJECT_CONNECTION_STRING` field.

### Step 3: Sign in to Azure

As a security best practice, we'll use [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. Before you can do so, you'll first need to install the **Azure CLI** per the [installation instructions](https://learn.microsoft.com/cli/azure/install-azure-cli?WT.mc_id=academic-105485-koreyst) for your operating system.

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.


## Additional Environment Variables - Azure Search and Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - Check **Project details** on the **Overview** page of your project.

- `AZURE_AI_PROJECT_NAME` - Look at the top of the **Overview** page for your project.

- `AZURE_OPENAI_SERVICE` - Find this in the **Included capabilities** tab for **Azure OpenAI Service** on the **Overview** page.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Go to **Project properties** on the **Overview** page of the **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources**, find the **Azure AI Services** connection name. If not listed, check the **Azure portal** under your resource group for the AI Services resource name.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Select your embedding model (e.g., `text-embedding-ada-002`) and note the **Deployment name** from the model details.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Select your chat model (e.g., `gpt-4o-mini`) and note the **Deployment name** from the model details.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Look for **Azure AI services**, click on it, then go to **Resource Management**, **Keys and Endpoint**, scroll down to the "Azure OpenAI endpoints", and copy the one that says "Language APIs".

- `AZURE_OPENAI_API_KEY` - From the same screen, copy KEY 1 or KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find your **Azure AI Search** resource, click it, and see **Overview**.

- `AZURE_SEARCH_API_KEY` - Then go to **Settings** and then **Keys** to copy the primary or secondary admin key.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - Visit the [API version lifecycle](https://learn.microsoft.com/en-us/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Setup keyless authentication

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` funkcję, aby uzyskać poświadczenia.

```python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Utknąłeś gdzieś?

Jeśli masz jakiekolwiek problemy z uruchomieniem tej konfiguracji, dołącz do naszego

lub

.

## Następna lekcja

Jesteś teraz gotowy, aby uruchomić kod tego kursu. Życzymy owocnej nauki i odkrywania świata Agentów AI!

[Wprowadzenie do Agentów AI i przypadków użycia Agentów](../01-intro-to-ai-agents/README.md)

**Zastrzeżenie**:  
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mimo że dążymy do dokładności, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym powinien być uważany za źródło autorytatywne. W przypadku informacji krytycznych zaleca się skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.