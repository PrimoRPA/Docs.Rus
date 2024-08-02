# Google Drive

Коллекция элементов доступна для скачивания по ссылке

{% embed url="https://www.nuget.org/packages/Primo.LabVS.GoogleDrive" %}

### Создание нового проекта Google Cloud Platform (GCP) <a href="#create_a_new_google_cloud_platform_gcp_project" id="create_a_new_google_cloud_platform_gcp_project"></a>

Для использования Google Workspace API необходимо наличие проекта Google Cloud Platform. Проекты представляет собой основу для создания, подключения и использования всех сервисов GCP, включая управление API, выставление счетов, добавление и удаление соавторов, а также управление разрешениями.

Чтобы создать новый проект, выполните следующую последовательность действий: 

1. Откройте [консоль Google Cloud](https://console.cloud.google.com/).
2. Нажмите на указатель "стрелка вниз" рядом с "Google Cloud Platform" - появится диалог с перечислением всех текущих проектов. 
3. Нажмите на **New Project** - будет открыто окно New Project.
4. В поле **Project Name** укажите название проекта. Если вы выполняете быструю загрузку, используйте "Quickstart."
5. (Необязательно) Чтобы изменить **Project ID**, нажмите **Edit**. После создания проекта его идентификатор изменить невозможно, поэтому следует выбирать такой идентификатор, который будет удовлетворять потребности на всем протяжении его существования. 
6. Нажмите на **Organization** и выберите вашу организацию.
7. В поле **Location** нажмите на **Browse** - будут показаны возможные варианты расположения проекта. 
8. Нажмите на вариант расположения, затем нажмите на **Select**.
9. Нажмите **Create**. Консоль переключится на страницу панели инструментов, и ваш проект будет создан в течение нескольких минут. 

![](<../../../../.gitbook/assets/image (544).png>)

![](<../../../../.gitbook/assets/image (457).png>)

Дополнительную информацию о проектах GCP можно найти на странице [Creating and managing projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

### Подключение Google Workspace API <a href="#enable-api" id="enable-api"></a>

1. Откройте [консоль Google Cloud](https://console.cloud.google.com/).
2. Нажмите на указатель "стрелка вниз" рядом с "Google Cloud Platform" и выберите проект.
3. В верхнем левом углу нажмите на Menu > **APIs & Services**.
4. Нажмите на **Enable APIs and Services** - откроется страница **Welcome to API Library**.
5. In the search field, enter the name of the API you want to enable. For example, type "Gmail API" to find the Gmail API. If you are enabling an API for a quickstart, refer to the quickstart's Prerequisites section for the API to enable.
6. Click the API to enable. The API page appears.
7. Click **Enable**. The Overview page appears.
8. To enable an additional API, repeat steps 3 - 7.
