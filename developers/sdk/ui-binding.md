# Привязка данных к UI

Для изменения значения свойства Prop1 в визуальной части элемента, нужно использовать Binding. Например:

```markup
<UserControl x:Class="Primo.SDKSample.PrimoElement"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
             xmlns:local="clr-namespace:Primo.SDKSample"
             mc:Ignorable="d" 
             d:DesignHeight="450" d:DesignWidth="800">
    <Grid>
        <TextBox Text="{Binding Prop1}" IsReadOnly="False" BorderThickness="0" Grid.Column="0" Margin="5,0,5,0" Height="23" TextWrapping="NoWrap" VerticalAlignment="Center" BorderBrush="#D0D7E2" />
    </Grid>
</UserControl>

```

![](<../../.gitbook/assets/0 (126).png>)
