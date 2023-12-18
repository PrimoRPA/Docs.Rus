# Дополнительные методы

**T GetPropertyValue\<T>(string value, string name, ScriptingData sd)** - получает значение заданного свойства, например для свойства Prop1:&#x20;

string p1 = GetPropertyValue\<String>(this.Prop1, "Prop1", sd);



**object GetPropertyValue(string value, string name, ScriptingData sd)** - аналогично, но без строгой типизации

string p1 = GetPropertyValue(this.Prop1, "Prop1", sd) as string;



**void SetVariableValue\<T>(string varName, T val, ScriptingData sd)** - устанавливает значение свойства, например для свойства Prop1

SetVariableValue\<String>("Prop1", "value...", sd);



**void SetVariableValue(string varName, object val, Type dt, ScriptingData sd)** - то же самое, но без строгой типизации

SetVariableValue("Prop1", "value...", sd);



**T GetContainerOfType\<T>(IWFContainer container)** - получает ссылку на ближайший контейнер определенного типа, например для контейнера PrimoCustomContainerV

PrimoCustomContainerV cont = GetContainerOfType\<PrimoCustomContainerV>(this.WFContainer);



**Window GenerateWindow(UserControl ctrl)** - создает модальное окно с заданным содержимым



**IWFComponent ProduceControl(IWFContainer container)** - метод вызывается при создании элемента. В нем можно проверять валидность точки создания и создавать контейнер, если его нет. Например:

```csharp
public override IWFComponent ProduceControl(IWFContainer container)
{
    if (GetContainerOfType<MyContainer>(container) == null)
    {
        MyContainer db = new MyContainer(container);
        db.AddComponent(new MyComponent(db), null);
        return db;
    }
    return new MyComponent(container);
}
```



**bool IsAllowedMoveToContainer(IWFContainer cont)** - проверяет возможность перемещения элемента в заданную точку. Например, если хотим создать невозможность выноса элемента из контейнера:

```csharp
public override bool IsAllowedMoveToContainer(IWFContainer cont)
{
    if (GetContainerOfType<MyContainer>(cont) != null)
        return true;
    return false;
}
```
