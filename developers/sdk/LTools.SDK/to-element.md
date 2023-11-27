# Элемент с тайм-аутом

Базовый вид элемента с тайм-аутом:

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
    public class PrimoElementTOBack : PrimoComponentTO<PrimoElementTO>
    {
        private const string CGroupName = "SDK Test";

        public override string GroupName
        {
            get => CGroupName;
            protected set { }
        }
        protected override int sdkTimeOut 
        { 
            get => 10000;
            set { } 
        }

        public PrimoElementTOBack(IWFContainer container) : base(container)
        {
            InitClass(container);
        }

        public override ExecutionResult TimedAction(ScriptingData sd)
        {
            return new ExecutionResult();
        }
    }
}

```

Как можно заметить, данный класс имеет два отличия от синхронного:

1. Основной метод называется не SimpleAction, а TimedAction.
2. Наличие свойства sdkTimeOut. Данное свойство отвечает за время ожидания завершения работы метода TimedAction. Если метод не завершится вовремя, будет сгенерировано исключение о тайм-ауте.
