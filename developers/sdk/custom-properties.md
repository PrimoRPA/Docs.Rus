# Кастомные свойства

Для создания свойств, отображаемых в палитре Свойства элемента Primo Studio, необходимо произвести следующие действия:

1. **Создать свойство**

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

В данном примере мы создаем свойство Prop1

Атрибут StoringProperty отвечает за то, что значение свойства будет сохранено в файле процесса

Атрибут ValidateReturnScript не обязателен и служит для проверки синтаксиса скрипта свойства. Значение данного атрибута – тип данных, который может быть присвоен данному свойству. В примере это строка. Если при создании сценария пользователь введет значение с типом, отличным от строки, Студия покажет ошибку. Если данный атрибут отсутствует, Студия не будет проверять тип данных свойства

Атрибут Category отвечает за имя группы, содержащую данное свойство в палитре Свойств Студии

Атрибут DisplayName отвечает за имя свойства, отображаемое в палитре Свойства Студии

**2.  Добавление свойства в палитру свойств**

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

Добавление производится в конструкторе до вызова метода InitClass. Свойство имеет следующие параметры:

PropName – имя свойства

PropertyType – тип редактора свойства. Доступны варианты SCRIPT – редактор скрипта, VARIABLE – выбор переменной, OBJECT – автоматический (например для перечислений), CUSTOM – пользовательский (на данный момент не реализован в рамках SDK)

DataType – тип данных свойства

ToolTip – текст всплывающей подсказки

IsReadOnly – признак только для чтения

**3.  Задание значения по умолчанию (не обязательно)**

```csharp
this.Prop1 = this.IsNoCode("Prop1") ? "test text" : "\"test text\"";
```

В данном примере, свойству будет присвоено значение test text, если включен режим No-code, либо значение “test text”, при выключенном No-code.

Значение по умолчанию задается после вызова метода InitClass

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

![](<../../.gitbook/assets/0 (140).png>)





**Получение значения кастомного свойства**

При выполнении бизнес-логики, безусловно необходимо получить значение, содержащееся в свойстве. Для этой цели служит синтаксис:

```csharp
string p1 = GetPropertyValue<string>(this.Prop1, "Prop1", sd);
```

,где первый параметр – само свойство, второй – имя свойства.

Например, элемент, выводящий окно сообщение с введенным текстом будет иметь следующий синтаксис:

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
