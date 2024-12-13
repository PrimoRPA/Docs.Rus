# Шаблон process.cshtml

**process.cshtml** — это шаблон, предназначенный для описания файла процесса (*.ltw). В этом шаблоне используется модель данных `ProcessInfo`, подключаемая с помощью директивы `@model`. 

```csharp
@using PrimoConverter.PrimoModel
@using PrimoDocum.ObjectModel
@model ProcessInfo
```

В шаблоне **process.cshtml** предусмотрен специальный тег `{Activities}`, который обозначает место, куда *AutoDoc* автоматически вставляет результат заполнения шаблона **ActivityInfo**. Это позволяет легко интегрировать информацию об активностях процесса в итоговый документ.

### Типы и свойства данных в шаблонах AutoDoc

По ссылкам ниже представлены описания свойств используемых типов в шаблонах `.cshtml`. Каждому типу данных сопоставлен набор свойств.

1. [Тип ProjectInfo](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-1.-tip-projectinfo)  
2. [Тип ProcessInfo](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-2.-tip-processinfo)  
3. [Тип ToCItem](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-3.-tip-tocitem)  
4. [Тип ScriptVariable](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-4.-tip-scriptvariable)  
5. [Тип SerializationComponent](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-5.-tip-serializationcomponent)  
6. [Тип Components](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-6.-tip-components)  
7. [Тип Properties](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-7.-tip-properties)  
8. [Тип SerializationItem](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-8.-tip-serializationitem)  
9. [Тип ActivityInfo](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-9.-tip-activityinfo)  
10. [Тип ActivityProp](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/tools/autodoc/templ_properties#id-10.-tip-activityprop)

