# Валидация ввода

Для проверки логического содержимого значений свойств служит метод **Validate**.

```csharp
public override ValidationResult Validate()
{
    LTools.Common.Model.ValidationResult ret = new LTools.Common.Model.ValidationResult();
    return ret;
}

```

Например, для проверки того, что пользователь ввел данные в свойство Prop1 можно использовать синтаксис:

```csharp
public override ValidationResult Validate()
{
    ValidationResult ret = new ValidationResult();
    if (String.IsNullOrEmpty(this.Prop1)) ret.Items.Add(new ValidationResult.ValidationItem() { PropertyName = "My Prop 1", Error = "Text not specified" });
    return ret;
}

```

Если пользователь не введет значение в свойство **Prop1**, студия выведет ошибку из свойства **Error**.
