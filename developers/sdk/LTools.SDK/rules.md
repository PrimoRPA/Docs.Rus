# Правила анализа кода

Подробнее о назначении механизма см. в разделе [Анализ проекта](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/analyzer).

## Начало работы

1.	Запустите Visual Studio.
2.	Выберите **Create a new project** с типом Class Library (.NET Framework) либо Class Library (поддерживаются .NET Framework 4.6.1 и .NET Standard 2.0).
3.	Введите имя проекта. **Имя проекта и библиотеки dll должны начинаться с префикса Primo.**
4.	Найдите в папке Primo Studio сборку `Primo.ProjectAnalyzer.Dto.dll` и добавьте ее в Dependencies проекта:
  
  ![](<../../../.gitbook/assets/1.sdk.rules.png>) 

5\. Создайте класс (Add ➝ Class...), который будет содержать правило. Для этого надо унаследовать интерфейс Primo.ProjectAnalyzer.IAnalysisRule.

## Создание правила

Пример правила ST-PR-003, проверяющего вложенность диаграмм:

```csharp
using Primo.ProjectAnalyzer.Model;
using Primo.ProjectAnalyzer.Model.Serialization;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace Primo.ProjectAnalyzer.Dto.Rules
{
    /// <summary>
    /// ST-PR-003: Несколько уровней диаграмм
    /// </summary>
    public class StPr003 : IAnalysisRule
    {
        #region Константы
        /// <summary>
        /// Кол-во
        /// </summary>
        private const string ARG_COUNT_KEY = "Count";
        /// <summary>
        /// Кол-во
        /// </summary>
        private const int ARG_COUNT = 2;
        #endregion

        #region Свойства контракта IAnalysisRule
        /// <summary>
        /// Код
        /// </summary>
        public string Code
        {
            get { return Properties.StPr003.Code; }
        }

        /// <summary>
        /// Наименование
        /// </summary>
        public string Name
        {
            get { return Properties.StPr003.Name; }
        }

        /// <summary>
        /// Описание
        /// </summary>
        public string Description
        {
            get { return Properties.StPr003.Recomendation; }
        }

        /// <summary>
        /// URL помощи
        /// </summary>
        public string HelpUrl
        {
            get { return null; }
        }

        /// <summary>
        /// Области
        /// </summary>
        public RuleAreas[] Areas
        {
            get { return new RuleAreas[] { RuleAreas.Process }; }
        }

        private RuleActions defaultAction = RuleActions.Error;
        /// <summary>
        /// Действие по умолчанию
        /// </summary>
        public RuleActions DefaultAction
        {
            get { return defaultAction; }
            set { this.defaultAction = value; }
        }

        /// <summary>
        /// Аргументы
        /// </summary>
        public AnalysisRuleArg[] Arguments
        {
            get;
            set;
        }
        #endregion

        #region Конструкторы
        /// <summary>
        /// Конструктор
        /// </summary>
        public StPr003()
        {
            this.Arguments = new AnalysisRuleArg[] 
            {
                new AnalysisRuleArg()
                {
                    Key = ARG_COUNT_KEY,
                    Name = Properties.StPr003.Arg_Count,
                    Value = ARG_COUNT.ToString(),
                    RegEx = @"^\d+$"
                }
            };
        }
        #endregion

        #region Методы контракта IAnalysisRule
        /// <summary>
        /// Проверка проекта
        /// </summary>
        /// <param name="project">Проект</param>
        /// <returns>Результат проверки</returns>
        public RuleResult Inspect(IRobotProject project)
        {
            return new RuleResult();
        }

        /// <summary>
        /// Проверка процесса
        /// </summary>
        /// <param name="process">Процесс</param>
        /// <returns>Результат проверки</returns>
        public RuleResult Inspect(IRobotProcess process)
        {
            int mx = Int32.Parse(this.Arguments.Where(it => it.Key == ARG_COUNT_KEY).FirstOrDefault().Value);
            int mmx = 0;
            foreach (var c in process.GetAllElements())
            {
                int cn = 0;
                if (c.ClassName == "LTools.Workflow.Elements.WFWorkflowContainer")
                {
                    cn++;
                    cn += CountWFs(c as SerializationContainer);
                }
                if (cn > mmx) mmx = cn;
            }

            if (mmx > mx)
            {
                return new RuleResult()
                {
                    HasErrors = true,
                    Level = this.DefaultAction,
                    RecommendationMessage = Properties.StPr003.Recomendation,
                    Messages = new string[] { String.Format(Properties.StPr003.Description, mmx, mx) }
                };
            }

            return new RuleResult();
        }

        private static int CountWFs(SerializationContainer cont)
        {
            int cn = 0;
            int mx = 0;
            if (cont != null)
            {
                foreach (var c in cont.Components)
                {
                    cn = 0;
                    if (c.ClassName == "LTools.Workflow.Elements.WFWorkflowContainer")
                    {
                        cn++;
                        cn += CountWFs(c as SerializationContainer);
                    }
                    if (cn > mx) mx = cn;
                }
            }
            return mx;
        }

        /// <summary>
        /// Проверка элемента
        /// </summary>
        /// <param name="component">Элемент</param>
        /// <returns>Результат проверки</returns>
        public RuleResult Inspect(SerializationComponent component)
        {
            return new RuleResult();
        }

        /// <summary>
        /// Сброс к исходным значениям
        /// </summary>
        public void Reset()
        {
            this.Arguments.Where(it => it.Key == ARG_COUNT_KEY).FirstOrDefault().Value = ARG_COUNT.ToString();
        }
        #endregion
    }
}
```

### Описание классов
**IAnalysisRule**

| Имя члена класса | Описание |
| ---------------- | -------- |
| Code	          | Код правила |
| Name	          | Наименование правила |
| Description	    | Описание правила |
| HelpUrl	        | Ссылка на описание |
| Areas	          | Области, к которым применимо правило (Проект, Процесс, Элемент) |
| DefaultAction	  | Действие по умолчанию (Info, Error, Warning, Verbose) |
| Arguments	      | Аргументы правила |
| Inspect(...)	  | Методы, осуществляющие проверку правила |
| Reset()	        | Вызывается при сбросе правила в состояние по умолчанию |


**AnalysisRuleArg**

| Имя члена класса | Описание |
| ---------------- | -------- |
| Key	             | Ключ-идентификатор |
| Name	           | Наименование аргумента |
| RegEx	           | Регулярное выражение, применяемое при проверке ввода аргумента |
| Value	           | Значение аргумента |

![](<../../../.gitbook/assets/2.sdk.rules.png>) 

**RuleResult**

| Имя члена класса | Описание |
| ---------------- | -------- |
| Level	           | Действие |
| HasErrors	       | Признак наличия ошибки (для Error, Warning и Vaerbose). Info попадает в результат всегда |
| RecommendationMessage	| Текст рекомендации |
| Messages	       | Сообщения  |

![](<../../../.gitbook/assets/3.sdk.rules.png>) 
 
## Анатомия проекта Primo

**IRobotProject** – информация о проекте.

| Имя члена класса | Описание |
| ---------------- | -------- |
| Project	         | Данные проекта |
| Items	           | Массив файлов проекта |
| Dependencies	   | Массив зависимостей проекта |
| GetAllProcesses() |	Возвращает все процессы проекта |

**IRobotProcess** – информация о процессе.

| Имя члена класса | Описание |
| ---------------- | -------- |
| FileName	       | Имя файла |
| ProcessType	     | Тип процесса |
| IsTestCase	     | Признак тестового случая |
| UseArgs	         | Признак использования аргументов |
| ScriptType	     | Тип скрипта |
| RootContainer	   | Корневой контейнер (для последовательности) |
| Components	     | Элементы процесса (для диаграммы) |
| GlobalVariables  | Перменные |
| Arguments	       | Аргументы |
| GetAllElements() |Возвращает все элементы процесса |

**SerializationComponent** – информация об элементе.

| Имя члена класса | Описание |
| ---------------- | -------- |
| ClassName	       | Имя класса |
| AssemblyName	   | Имя сборки |
| Properties	     | Массив свойств (Name – имя, Value – значение) |

**SerializationContainer : SerializationComponent** – информация об элементе-контейнере.

| Имя члена класса | Описание |
| ---------------- | -------- |
| Components	     | Массив элементов контейнера |

## Сборка и отладка

Для отладки можно использовать класс Inspector. 

Пример:

```csharp
Primo.ProjectAnalyzer.Inspector insp = new Primo.ProjectAnalyzer.Inspector();

//Проверка проекта
var proj = Primo.ProjectAnalyzer.Helper.ProcessHelper.LoadProject(@"C:\Test\project.ltp");
var ret = insp.InspectRule(proj, testrule1);

//Проверка процесса
var proc = Primo.ProjectAnalyzer.Helper.ProcessHelper.LoadProcess(@"C:\Test\Main.ltw");
ret = insp.InspectRule(proc, testrule2);

//Проверка элемента
var els = proc.GetAllElements();
ret = insp.InspectRule(els.Where(it => it.Properties.Where(it2 => (it2.Name == "ComponentID") && (it2.Value.ToString() == "20a3444a-70fe-4657-a4fa-390668af67f9")).Count() > 0).First(), testRule);
```

В результате сборки нового правила будет получена библиотека Primo.\*.dll. Ее нужно скопировать и добавить в папку Primo Studio. Если библиотека не содержит ошибок, после запуска Студии правило станет доступно в меню **Общие > Анализ**.








