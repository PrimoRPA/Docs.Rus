# Шаблон process.cshtml

**process.cshtml** — это шаблон, предназначенный для описания файла процесса (*.ltw). В этом шаблоне используется модель данных `ProcessInfo`, подключаемая с помощью директивы `@model`. 

```csharp
@using PrimoConverter.PrimoModel
@using PrimoDocum.ObjectModel
@model ProcessInfo
```

В шаблоне **process.cshtml** предусмотрен специальный тег `{Activities}`, который обозначает место, куда *AutoDoc* автоматически вставляет результат заполнения шаблона **ActivityInfo**. Это позволяет легко интегрировать информацию об активностях процесса в итоговый документ.


