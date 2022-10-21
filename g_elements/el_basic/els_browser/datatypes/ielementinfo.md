# IElementInfo

LTools.WebBrowser.Model.IElementInfo - объект, который содержит ссылку на элемент управления.

| Свойство    | Тип                  | Описание          |
| ----------- | -------------------- | ----------------- |
| BaseElement | Object               | Базовый элемент   |
| ID          | String               | ID                |
| TagName     | String               | Имя тега          |
| ClassName   | String               | Класс             |
| Name        | String               | Имя               |
| Value       | String               | Значение          |
| InnerText   | String               | Текст             |
| ListItems   | List\<string>        | Элементы списка   |
| ListCurrent | List\<string>        | Выбранный элемент списка |
| Attributes  | List\<ElementAttribute> | Атрибуты элемента |
| SearchPattern | ElementSearchPattern | Шаблон поиска  |
| Index       | Int                  | Индекс            |
| X           | Int                  | X                 |
| AbsoluteX   | Int                  | X                 |
| Y           | Int                  | Y                 |
| AbsoluteY   | Int                  | Y                 |
| Width       | Int                  | Ширина            |
| Height      | Int                  | Высота            |
| Visible     | Boolean              | Видимость элемента |
| IsChecked   | Boolean              | Признак выбранного чекбокса |
| BoundingRect | [Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=net-6.0) | Границы элемента |
| OuterHtml    | String              | HTML               |

