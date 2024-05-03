# Дополнительные методы

1. **T GetPropertyValue\<T>(string value, string name, ScriptingData sd)** — получает значение заданного свойства. Пример использования для свойства Prop1:&#x20;
   ```
   string p1 = GetPropertyValue<String>(this.Prop1, "Prop1", sd);
   ```


2. **object GetPropertyValue(string value, string name, ScriptingData sd)** — аналогично, но без строгой типизации. Пример для свойства Prop1: 
   ```
   string p1 = GetPropertyValue(this.Prop1, "Prop1", sd) as string;
   ```


3. **void SetVariableValue\<T>(string varName, T val, ScriptingData sd)** — устанавливает значение свойства. Пример для свойства Prop1:
   ```
   SetVariableValue\<String>("Prop1", "value...", sd);
   ```


4. **void SetVariableValue(string varName, object val, Type dt, ScriptingData sd)** — то же самое, но без строгой типизации. Пример:
   ```
   SetVariableValue("Prop1", "value...", sd);
   ```

5. **T GetContainerOfType\<T>(IWFContainer container)** — получает ссылку на ближайший контейнер определенного типа. Пример для контейнера PrimoCustomContainerV:
   ```
   PrimoCustomContainerV cont = GetContainerOfType\<PrimoCustomContainerV>(this.WFContainer);
   ```
 

6. **Window GenerateWindow(UserControl ctrl)** — создает модальное окно с заданным содержимым.


7. **IWFComponent ProduceControl(IWFContainer container)** — метод вызывается при создании элемента. В нем можно проверять валидность точки создания и создавать контейнер, если его нет. Например:

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



8. **bool IsAllowedMoveToContainer(IWFContainer cont)** — проверяет возможность перемещения элемента в заданную точку. Например, если хотим создать невозможность выноса элемента из контейнера:

```csharp
public override bool IsAllowedMoveToContainer(IWFContainer cont)
{
    if (GetContainerOfType<MyContainer>(cont) != null)
        return true;
    return false;
}
```
