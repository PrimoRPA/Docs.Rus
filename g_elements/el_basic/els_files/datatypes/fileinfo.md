 # FileInfo
 
 LTools.Data.Model.FileInfo - объект, который хранит информацию о файле или папке.
 
| Свойство             | Тип                                               | Описание                                           |
| -------------------- | ------------------------------------------------- | -------------------------------------------------- |
| IsDirectory          | Boolean                                           | Признак папки. Если значение true, то это информация о папке   |
| BaseFileInfo         | [System.IO.FileInfo](https://learn.microsoft.com/ru-RU/dotnet/api/system.io.fileinfo?view=net-8.0&viewFallbackFrom=net-4.6.1) | Основная информация о файле   |
| BaseDirectoryInfo    | [System.IO.DirectoryInfo](https://learn.microsoft.com/ru-RU/dotnet/api/system.io.directoryinfo?view=net-8.0&viewFallbackFrom=net-4.6.1) | Основная информация о папке   |
| Properties           | List\<FileInfoProperty\>                          | Список свойств. Структура свойства приведена ниже |

LTools.Data.Model.FileInfoProperty - свойство объекта с информацией о файле/папке.

| Свойство             | Тип                                               | Описание                                           |
| -------------------- | ------------------------------------------------- | -------------------------------------------------- |
| Header               | String                                            | Заголовок свойства    |
| Value                | String                                            | Значение свойства     |

 
 
 
