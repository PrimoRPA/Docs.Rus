# Шаблон ActivityInfo.cshtml

**ActivityInfo.cshtml** — это шаблон активностей, предназначенный для описания элементов процесса. В этом шаблоне используется модель данных `IEnumerable<ActivityInfo>`, которая подключается с помощью директивы `@model`.

```csharp
@using PrimoAutodoc.ObjectModel
@using PrimoConverter.Utils
@using PrimoDocum.ObjectModel
@using System.Collections.Generic
@using System.Linq
@model IEnumerable<ActivityInfo>
```

Шаблон **ActivityInfo.cshtml** выполняет обход дерева элементов процесса в порядке их вызова. Для отображения структуры элементов используется метод `ShowTree(@Model)`, который обеспечивает последовательное отображение всех активностей внутри процесса.
