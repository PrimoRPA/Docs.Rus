# Кастомные свойства

Свойства каждого элемента Primo RPA Studio отображаются в панели «Свойства». Чтобы определить кастомные свойства элемента, выполните действия:

1\. **Создайте свойство**.

Пример:

```csharp
private string prop1;

[LTools.Common.Model.Serialization.StoringProperty]
[LTools.Common.Model.Studio.ValidateReturnScript(DataType = typeof(string))]
[System.ComponentModel.Category("SDK"), System.ComponentModel.DisplayName("My Prop 1")]
public string Prop1
{
    get { return this.prop1; }
    set { this.prop1 = value; this.InvokePropertyChanged(this, "Prop1"); }
}

```

В данном примере мы создаем свойство **Prop1** с атрибутами:

* StoringProperty - устанавливает, что значение свойства будет сохранено в файле процесса.
* ValidateReturnScript - необязательный атрибут, служит для проверки синтаксиса скрипта свойства. В качестве значения выступает тип данных, который может быть присвоен данному свойству. В примере это строка. Если при создании сценария пользователь введет значение с типом, отличным от строки, Студия отобразит ему ошибку. Если этот атрибут отсутствует, то Студия не будет проверять тип данных свойства.
* Category - имя группы, в которую нужно поместить наше свойство в панели свойств Студии.
* DisplayName - имя свойства, отображаемое в панели свойств Студии.

**2\. Добавьте созданные свойства в панель свойств**.

Добавление производится в конструкторе до вызова метода InitClass. 

Пример:

```csharp
sdkProperties = new List<LTools.Common.Helpers.WFHelper.PropertiesItem>()
{
    new LTools.Common.Helpers.WFHelper.PropertiesItem() 
    { 
        PropName = "Prop1", 
        PropertyType = LTools.Common.Helpers.WFHelper.PropertiesItem.PropertyTypes.SCRIPT, 
        EditorType = ScriptEditorTypes.NONE, 
        DataType = typeof(string), ToolTip = "SDK Tooltip1", IsReadOnly = false 
    }
};

```

Свойство имеет следующие параметры:

* PropName – имя свойства.
* PropertyType – тип редактора свойства. Доступны варианты SCRIPT – редактор скрипта, VARIABLE – выбор переменной, OBJECT – автоматический (например для перечислений), CUSTOM – пользовательский (на данный момент не реализован в рамках SDK).
* DataType – тип данных свойства.
* ToolTip – текст всплывающей подсказки.
* IsReadOnly – признак только для чтения

**3\. Задайте свойствам значения по умолчанию (не обязательно)**.

Пример:

```csharp
this.Prop1 = this.IsNoCode("Prop1") ? "test text" : "\"test text\"";
```

В данном примере свойству будет присвоено значение `test text`, если включен режим No-code, либо значение `“test text”` при выключенном No-code.

Значение по умолчанию задается после вызова метода InitClass.

Пример:

```csharp
public PrimoElementBack(IWFContainer container) : base(container)
{
    sdkComponentName = "My sync element";
    sdkComponentHelp = "This is my first sync element";
    sdkComponentIcon = "pack://application:,,/Primo.SDKSample;component/Images/sample.png";
    sdkProperties = new List<LTools.Common.Helpers.WFHelper.PropertiesItem>()
    {
        new LTools.Common.Helpers.WFHelper.PropertiesItem()
        {
            PropName = "Prop1",
            PropertyType = LTools.Common.Helpers.WFHelper.PropertiesItem.PropertyTypes.SCRIPT,
            EditorType = ScriptEditorTypes.NONE,
            DataType = typeof(string), ToolTip = "SDK Tooltip1", IsReadOnly = false
        }
    };
    InitClass(container);
    this.Prop1 = this.IsNoCode("Prop1") ? "test text" : "\"test text\"";
}

```

![](<../../../.gitbook/assets/0 (140).png>)


## Получение значения кастомного свойства

При выполнении бизнес-логики безусловно необходимо получить значение, содержащееся в свойстве. Для этой цели служит синтаксис:

```csharp
string p1 = GetPropertyValue<string>(this.Prop1, "Prop1", sd);
```

Где первый параметр – это само свойство, а второй – имя свойства.

Например, элемент, выводящий в окно сообщение с введенным текстом будет иметь следующий синтаксис:

```csharp
public override ExecutionResult SimpleAction(ScriptingData sd)
{
    try
    {
        string p1 = GetPropertyValue<string>(this.Prop1, "Prop1", sd);
        System.Windows.MessageBox.Show(p1);
        return new ExecutionResult() { SuccessMessage = "Done" };
    }
    catch (Exception ex)
    {
        return new ExecutionResult() { IsSuccess = false, ErrorMessage = ex?.Message };
    }
}

```
