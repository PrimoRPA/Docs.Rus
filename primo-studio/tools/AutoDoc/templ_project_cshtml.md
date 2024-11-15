# Шаблон project.cshtml

**project.cshtml**  - это шаблон, предназначенный для описания проекта в формате HTML. Для этого используется модель данных `ProjectInfo`, которая подключается через директиву `@model`:

```csharp
@using PrimoAutodoc.ObjectModel
@using PrimoConverter.Utils
@using PrimoDocum.ObjectModel
@model ProjectInfo
```

Модель данных `ProjectInfo` определяет доступ к информации о проекте, такой как имя, описание и список компонентов, которые можно включить в выходной документ.шаблона 

