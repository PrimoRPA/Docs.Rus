# Синхронный элемент

Базовый вид синхронного элемента:

```csharp
using LTools.Common.Model;
using LTools.Common.UIElements;
using LTools.SDK;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Primo.SDKSample
{
    public class PrimoElementBack : PrimoComponentSimple<PrimoElement>
    {
        private const string CGroupName = "SDK Test";

        public override string GroupName 
        { 
            get => CGroupName; 
            protected set { }
        }

        public PrimoElementBack(IWFContainer container) : base(container)
        {
            InitClass(container);
        }

        public override ExecutionResult SimpleAction(ScriptingData sd)
        {
            return new ExecutionResult();
        }
    }
}

```

**Рассмотрим детали данного класса подробнее:**

Свойство **GroupName** отвечает за наименование группы, в которой будет содержаться ваш элемент в рамках палитры Элементы Primo Studio. Для создания вложенности ярусы дерева группы нужно разделять при помощи константы LTools.Common.UIElements. WFPublishedElementBase.TREE\_SEPARATOR. Например, для формирования дерева:

    Group1

    ---- Group2

    -------- Element1

Нужно создать имя группы вида “Group1” + WFPublishedElementBase.TREE\_SEPARATOR + “Group2”.

Метод **InitClass** в теле конструктора обязателен и производит сервисные действия при создании компонента. Данный метод должен вызываться в конце, но перед инициализацией кастомных свойств элемента.

Метод **SimpleAction** является основным и вызывается роботом в качестве логики элемента. Таким образом, данный метод должен содержать основную бизнес-логику.

Класс **ExecutionResult** служит для оповещения робота об успешном либо неуспешном выполнении элемента, а также для формирования записи журнала. Например:

* `new ExecutionResult() { IsSuccess = true, SuccessMessage = "Completed successfully" }` – оповещает об успешном завершении работы элемента и пишет в лог сообщение “Completed successfully”.

* `new ExecutionResult() { IsSuccess = false, ErrorMessage = "Execution error" }` – информирует робота об ошибке.
