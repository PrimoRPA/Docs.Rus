# Google Drive

Коллекция элементов доступна для скачивания по ссылке

{% embed url="https://www.nuget.org/packages/Primo.LabVS.GoogleDrive" %}

### Создание нового проекта Google Cloud Platform (GCP) <a href="#create_a_new_google_cloud_platform_gcp_project" id="create_a_new_google_cloud_platform_gcp_project"></a>

Для использования API Google Workspace необходимо наличие проекта Google Cloud Platform. Проекты представляет собой основу для создания, подключения и использования всех сервисов GCP, включая управление API, выставление счетов, enabling billing, добавление и удаление соавторов, а также управление разрешениями.

Чтобы создать новый проект, выполните следующую последовательность действий: 

1. Откройте [консоль Google Cloud](https://console.cloud.google.com/).
2. Щелкните на указатель "стрелка вниз" рядом с "Google Cloud Platform" - появится диалог с перечислением всех текущих проектов. 
3. Click **New Project**. The New Project screen appears.
4. In the **Project Name** field, enter a descriptive name for your project. Если вы выполняете быстрый старт, используйте "Quickstart."
5. (Optional) To edit the **Project ID**, click **Edit**. The project ID can't be changed after the project is created, so choose an ID that meets your needs for the lifetime of the project.
6. Click **Organization** and select your organization.
7. In the **Location** field, click **Browse** to display potential locations for your project.
8. Click a location and click **Select**.
9. Click **Create**. The console navigates to the Dashboard page and your project is created within a few minutes.

![](<../../../../.gitbook/assets/image (544).png>)

![](<../../../../.gitbook/assets/image (457).png>)

For further information on GCP projects, refer to [Creating and managing projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

### Enable a Google Workspace API <a href="#enable-api" id="enable-api"></a>

1. Open the [Google Cloud Console](https://console.cloud.google.com/).
2. Next to "Google Cloud Platform," click the Down arrow arrow\_drop\_down and select a project.
3. In the top-left corner, click Menu menu > **APIs & Services**.
4. Click **Enable APIs and Services**. The **Welcome to API Library** page appears.
5. In the search field, enter the name of the API you want to enable. For example, type "Gmail API" to find the Gmail API. If you are enabling an API for a quickstart, refer to the quickstart's Prerequisites section for the API to enable.
6. Click the API to enable. The API page appears.
7. Click **Enable**. The Overview page appears.
8. To enable an additional API, repeat steps 3 - 7.
