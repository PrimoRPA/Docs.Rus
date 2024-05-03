# Упаковка и публикация

Для упаковки элемента можно использовать приложение Nuget Package Explorer (NPE), доступное по [данному адресу](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).

Упаковка состоит из следующих шагов:

1. Запустите приложение и выберите пункт **Create a new package**.

![](<../../../.gitbook/assets/0 (144).png>)

2\. В панели **Package contents** щелкните правой кнопкой мыши и выберите пункт **Add Lib Folder**.

3\. Перетащите ваш файл `Primo.*.dll` в панель **Package contents** в папку *lib*.

![](<../../../.gitbook/assets/1 (120).png>)

4\. Нажмите кнопку **Edit metadata** и заполните информацию о вашем пакете. Она будет доступна всем пользователям пакета. Не забудьте поставить теги Primo и RPA.

![](<../../../.gitbook/assets/2 (6).png>)

5\. В завершение перейдите в раздел меню **File ➝ Save As…** и сохраните файл на диск.

Для публикации пакета зарегистрируйтесь на портале [NuGet Gallery | Home](https://www.nuget.org/). Далее перейдите в раздел **Manage Packages**, нажмите **Add new** и добавьте ваш файл `Primo.*.nupkg`. 

Загрузка пакета будет доступна в соответствующем [разделе](https://www.nuget.org/packages/manage/upload).
