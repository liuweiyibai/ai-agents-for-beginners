<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "76945069b52a49cd0432ae3e0b0ba22e",
  "translation_date": "2025-07-12T07:59:32+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "uk"
}
-->
Тепер у вас має бути власна форкнута версія цього курсу за наступним посиланням:

![Forked Repo](../../../translated_images/forked-repo.33f27ca1901baa6a5e13ec3eb1f0ddd3a44d936d91cc8cfb19bfdb9688bd2c3d.uk.png)

## Запуск коду

Цей курс пропонує серію Jupyter Notebook, які ви можете запускати, щоб отримати практичний досвід створення AI агентів.

Приклади коду використовують:

**Потрібен обліковий запис GitHub - безкоштовно**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Позначено як (semantic-kernel.ipynb)  
2) AutoGen Framework + GitHub Models Marketplace. Позначено як (autogen.ipynb)

**Потрібна підписка Azure**:  
3) Azure AI Foundry + Azure AI Agent Service. Позначено як (azureaiagent.ipynb)

Радимо спробувати всі три варіанти, щоб визначити, який підходить вам найкраще.

Обраний варіант визначить, які кроки налаштування вам потрібно виконати далі:

## Вимоги

- Python 3.12+  
  - **NOTE**: Якщо у вас не встановлено Python 3.12, обов’язково встановіть його. Потім створіть віртуальне середовище, використовуючи python3.12, щоб переконатися, що встановлені правильні версії пакетів з файлу requirements.txt.  
- Обліковий запис GitHub – для доступу до GitHub Models Marketplace  
- Підписка Azure – для доступу до Azure AI Foundry  
- Обліковий запис Azure AI Foundry – для доступу до Azure AI Agent Service

У корені цього репозиторію є файл `requirements.txt`, який містить усі необхідні пакети Python для запуску прикладів коду.

Ви можете встановити їх, виконавши наступну команду в терміналі в корені репозиторію:

```bash
pip install -r requirements.txt
```  
Рекомендуємо створити віртуальне середовище Python, щоб уникнути конфліктів і проблем.

## Налаштування VSCode  
Переконайтеся, що у VSCode використовується правильна версія Python.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Налаштування для прикладів з GitHub Models

### Крок 1: Отримайте свій персональний токен доступу GitHub (PAT)

Наразі цей курс використовує GitHub Models Marketplace для безкоштовного доступу до великих мовних моделей (LLM), які використовуються для створення AI агентів.

Щоб отримати доступ до цієї служби, потрібно створити персональний токен доступу GitHub.

Це можна зробити у вашому обліковому записі GitHub.

Виберіть опцію `Fine-grained tokens` зліва на екрані.

Потім натисніть `Generate new token`.

![Generate Token](../../../translated_images/generate-token.9748d7585dd004cb4119b5aac724baff49c3a85791701b5e8ba3274b037c5b66.uk.png)

Вам запропонують ввести назву токена, вибрати дату закінчення терміну дії (рекомендується: 30 днів) та встановити області дії токена (Public Repositories).

Також необхідно відредагувати дозволи цього токена: Permissions -> Models -> Дозволити доступ до GitHub Models.

Скопіюйте новий токен, який ви щойно створили. Тепер додайте його у файл `.env`, що входить до цього курсу.

### Крок 2: Створіть файл `.env`

Щоб створити файл `.env`, виконайте наступну команду в терміналі:

```bash
cp .env.example .env
```

Це скопіює приклад файлу та створить `.env` у вашій директорії, де ви зможете заповнити значення змінних середовища.

Відкрийте файл `.env` у вашому улюбленому текстовому редакторі та вставте скопійований токен у поле `GITHUB_TOKEN`.

Тепер ви можете запускати приклади коду цього курсу.

## Налаштування для прикладів з Azure AI Foundry та Azure AI Agent Service

### Крок 1: Отримайте кінцеву точку вашого проекту Azure

Дотримуйтесь інструкцій зі створення хаба та проекту в Azure AI Foundry тут: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Після створення проекту потрібно отримати рядок підключення до проекту.

Це можна зробити на сторінці **Overview** вашого проекту в порталі Azure AI Foundry.

![Project Connection String](../../../translated_images/project-endpoint.8cf04c9975bbfbf18f6447a599550edb052e52264fb7124d04a12e6175e330a5.uk.png)

### Крок 2: Створіть файл `.env`

Щоб створити файл `.env`, виконайте наступну команду в терміналі:

```bash
cp .env.example .env
```

Це скопіює приклад файлу та створить `.env` у вашій директорії, де ви зможете заповнити значення змінних середовища.

Відкрийте файл `.env` у вашому улюбленому текстовому редакторі та вставте рядок підключення у поле `PROJECT_ENDPOINT`.

### Крок 3: Увійдіть в Azure

З міркувань безпеки ми використовуємо [автентифікацію без ключів](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) для підключення до Azure OpenAI через Microsoft Entra ID. Спершу потрібно встановити **Azure CLI** відповідно до [інструкцій з встановлення](https://learn.microsoft.com/cli/azure/install-azure-cli?WT.mc_id=academic-105485-koreyst) для вашої операційної системи.

Потім відкрийте термінал і виконайте команду `az login --use-device-code` для входу в обліковий запис Azure.

Після входу виберіть вашу підписку в терміналі.

## Додаткові змінні середовища – Azure Search та Azure OpenAI

Для уроку Agentic RAG – Урок 5 – є приклади, які використовують Azure Search та Azure OpenAI.

Щоб запускати ці приклади, додайте наступні змінні середовища у файл `.env`:

### Сторінка огляду (проект)

- `AZURE_SUBSCRIPTION_ID` – Перевірте **Project details** на сторінці **Overview** вашого проекту.  
- `AZURE_AI_PROJECT_NAME` – Зверху сторінки **Overview** вашого проекту.  
- `AZURE_OPENAI_SERVICE` – Знайдіть у вкладці **Included capabilities** для **Azure OpenAI Service** на сторінці **Overview**.

### Центр керування

- `AZURE_OPENAI_RESOURCE_GROUP` – Перейдіть до **Project properties** на сторінці **Overview** в **Management Center**.  
- `GLOBAL_LLM_SERVICE` – У розділі **Connected resources** знайдіть назву підключення **Azure AI Services**. Якщо немає, перевірте в **Azure portal** у вашій групі ресурсів назву ресурсу AI Services.

### Сторінка моделей і кінцевих точок

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – Виберіть модель embedding (наприклад, `text-embedding-ada-002`) і зверніть увагу на **Deployment name** у деталях моделі.  
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – Виберіть чат-модель (наприклад, `gpt-4o-mini`) і зверніть увагу на **Deployment name** у деталях моделі.

### Портал Azure

- `AZURE_OPENAI_ENDPOINT` – Знайдіть **Azure AI services**, натисніть на нього, перейдіть до **Resource Management**, **Keys and Endpoint**, прокрутіть до розділу "Azure OpenAI endpoints" і скопіюйте той, що позначений як "Language APIs".  
- `AZURE_OPENAI_API_KEY` – На тій же сторінці скопіюйте KEY 1 або KEY 2.  
- `AZURE_SEARCH_SERVICE_ENDPOINT` – Знайдіть ресурс **Azure AI Search**, натисніть на нього і перегляньте **Overview**.  
- `AZURE_SEARCH_API_KEY` – Перейдіть до **Settings**, потім **Keys** і скопіюйте основний або додатковий ключ адміністратора.

### Зовнішня веб-сторінка

- `AZURE_OPENAI_API_VERSION` – Відвідайте сторінку [API version lifecycle](https://learn.microsoft.com/en-us/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) у розділі **Latest GA API release**.

### Налаштування автентифікації без ключів

Замість того, щоб жорстко прописувати облікові дані, ми використаємо безключове підключення з Azure OpenAI. Для цього імпортуємо `DefaultAzureCredential` і пізніше викличемо функцію `DefaultAzureCredential` для отримання облікових даних.

```python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Застрягли?

Якщо у вас виникли проблеми з налаштуванням, приєднуйтесь до нашої

або

.

## Наступний урок

Тепер ви готові запускати код цього курсу. Бажаємо успіхів у вивченні світу AI агентів!

[Вступ до AI агентів та приклади використання агентів](../01-intro-to-ai-agents/README.md)

**Відмова від відповідальності**:  
Цей документ було перекладено за допомогою сервісу автоматичного перекладу [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, будь ласка, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.