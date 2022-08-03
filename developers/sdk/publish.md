# Упаковка и публикация

Для упаковки элемента можно использовать приложение Nuget Package Explorer (NPE) (доступно по адресу [GitHub - NuGetPackageExplorer/NuGetPackageExplorer: Create, update and deploy Nuget Packages with a GUI](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)).

Запустите приложение и выберите пункт Create a new package

![](<../../.gitbook/assets/0 (144).png>)

Нажмите правой кнопкой в панели Package contents и выберите Add Lib Folder

Перетащите ваш файл Primo.\*.dll в панель Package contents в папку lib

![](<../../.gitbook/assets/1 (120).png>)

Нажмите кнопку Edit metadata и введите данные вашего пакета. Данные будут доступны всем пользователям пакета. Не забудьте поставить тэги Primo и RPA

![](<../../.gitbook/assets/2 (6).png>)

Нажмите File -> Save As… и сохраните ваш пакет на диск

Зарегистрируйтесь на портале [NuGet Gallery | Home](https://www.nuget.org/), перейдите в раздел Manage Packages, нажмите Add new и добавьте ваш файл Primo.\*.nupkg ([https://www.nuget.org/packages/manage/upload](https://www.nuget.org/packages/manage/upload) )
