# Специальный контейнер

Специальный контейнер - это контейнер с расширенным графическим оформлением. Графическое оформление выполняется по определенным правилам:

```xml
<UserControl x:Class="Primo.SDKSample.PrimoCustomContainerV"
             xmlns:WFItems="clr-namespace:LTools.Common.WFItems;assembly=LTools.Common"
             xmlns:ui="clr-namespace:LTools.Common.UIElements;assembly=LTools.Common"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:Primo.SDKSample"
             mc:Ignorable="d" 
             d:DesignHeight="450" d:DesignWidth="800">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="Auto"/>
            <RowDefinition />
        </Grid.RowDefinitions>
        <Label Grid.Row="0" Content="Message" HorizontalAlignment="Left" Margin="5,0,0,0"/>
        <TextBox x:Name="txtCondition" Grid.Row="1" Text="{Binding Prop1}" IsReadOnly="False" Margin="5,0,5,0" Height="23" />
        <Grid Grid.Row="2">
            <Grid Grid.Column="0">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto"/>
                    <RowDefinition />
                </Grid.RowDefinitions>
                <Label Grid.Row="0" Content="Container" HorizontalAlignment="Center"/>
                <Grid Grid.Row="1" Margin="5">
                    <Border BorderThickness="1" CornerRadius="0,0,0,0" Padding="{x:Static ui:WFElementBase.ContainerPadding}">
                        <WFItems:WFContainerBase x:Name="cntThen" />
                    </Border>
                </Grid>
            </Grid>
        </Grid>
    </Grid>
</UserControl>
```

WFItems:WFContainerBase - обязательный элемент оформления и представляет собой, собственно, контейнер элементов

ui:WFElementBase.ContainerPadding - отвечает за настраиваемый Студией отступ от краев

Код специального контейнера в общем виде:

```csharp
    /// <summary>
    /// Custom container
    /// </summary>
    public class PrimoCustomContainerBack : PrimoContainerCustom<PrimoCustomContainerV>
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

        public PrimoCustomContainerBack(IWFContainer container) : base(container)
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

Где PrimoCustomContainerV - имя контролла WPF, отвечающего за отображение

Для доступа к контроллу WPF можно использовать свойство this.UIControl
