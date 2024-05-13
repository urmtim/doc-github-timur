# Клик мышью

![](../../resources/basic/desktop/image-(239).png)

Компонент, производящий клик мышью на выбранном элементе управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство          | Тип                                   | Описание                                           |
| ----------------- | ------------------------------------- | -------------------------------------------------- |
| Шаблон поиска     | String                                | Шаблон поиска элемента управления                  |
| Элемент           | LTools.Desktop.Model.DUIControl       | Ссылка на элемент управления                       |
| Координаты        | System.Drawing.Rectangle              | Координаты клика курсора                           |
| Кнопка клавиатуры | LTools.Desktop.Model.KeyboardKeys     | Кнопка клавиатуры                                  |
| Кнопка мыши       | LTools.Desktop.Model.MouseButtons     | Кнопка мыши                                        |
| Позиция           | LTools.Common.Model.ClickPositions    | Позиция курсора при клике                          |
| Таймаут\*         | Int32                                 | Предельное время ожидания завершения процесса (мс) |


{% tabs %}
{% tab title="C#" %}
```csharp
//Функционал пока не реализован!!!
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, LTools.Desktop.Model.KeyboardKeys.CTRL, 20000);
//Элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.Click(el);
//Координаты
app.Click(new System.Drawing.Rectangle(100, 150, 0, 0));
```
{% endtab %}

{% tab title="Python" %}
```python
#Функционал пока не реализован!!!
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, LTools.Desktop.Model.KeyboardKeys.CTRL, 20000)
#Элемент
el = app.FindElement("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.Click(el)
#Координаты
app.Click(System.Drawing.Rectangle(100, 150, 0, 0))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Функционал пока не реализован!!!
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
	_lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, _lib.LTools.Desktop.Model.KeyboardKeys.CTRL, 20000);
//Элемент
var el = app.FindElement("{\"Name\":\"Hide\",\"AutomationID\":\"btnVanish\",\"ClassName\":\"Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.Click(el);
//Координаты
app.Click(new _lib.System.Drawing.Rectangle(100, 150, 0, 0));
```
{% endtab %}
{% endtabs %}
