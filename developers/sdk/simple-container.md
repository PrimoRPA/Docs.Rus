# Простой контейнер

Простой контейнер является контейнером без специального отображения, т.е. он не имеет дополнительного визуального оформления.

Базовый вид синхронного контейнера:

```csharp
    /// <summary>
    /// Simple container
    /// </summary>
    public class PrimoContainerBack : PrimoContainer
    {
        /// <summary>
        /// Group name
        /// </summary>
        private const string CGroupName = "SDK Test";

        /// <summary>
        /// Group name
        /// </summary>
        public override string GroupName
        {
            get => CGroupName;
            protected set { }
        }

        public PrimoContainerBack(IWFContainer container) : base(container)
        {
            InitClass(container);
        }

        /// <summary>
        /// Main action
        /// </summary>
        /// <param name="sd"></param>
        /// <returns></returns>
        public override ExecutionResult SimpleAction(ScriptingData sd)
        {
            return new ExecutionResult() { SuccessMessage = "Done" };
        }
    }
```
