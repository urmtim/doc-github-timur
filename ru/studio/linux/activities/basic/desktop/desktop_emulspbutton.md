# Эмуляция спецкнопки

*Eng: Hot-key simulation*

Предназначен для эмуляции нажатия клавиш клавиатуры или их комбинаций. Этот элемент часто используется для автоматизации действий, требующих ввода с клавиатуры.

Для надежности рекомендуется использовать этот элемент в контейнере [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/el_desktop_attach). Подключаемое приложение указывается в контейнере.

![](../../resources/basic/desktop/image-(149).png)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

#### Группа «Новое ядро»

:bangbang: *Значения этих свойств учитываются, только если установлен чекбокс **Новое ядро***.

![](../../resources/basic/desktop/hot-key-emul-new-core-parameters.png)

Предоставляют возможность выбрать клавиши для эмулирования:

1. **Новое ядро**: Boolean. Признак использования нового ядра для взаимодействия с операционной системой. Установите галочку, если новое ядро нужно использовать. По умолчанию галочка снята.
1. **Основная кнопка**: LTools.Common.Model.VirtualKey. Клавиша, которая будет эмулирована. По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать клавишу. Пример: `VK_A` - клавиша А. [См. полное описание значений](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/emulspbutton-application).
1. **Модификатор**: LTools.Common.Model.VirtualKey. Кнопка-модификатор, которая позволяет добавить к основной клавише дополнительные функции (например, Ctrl, Shift, Alt). По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать модификатор. Пример: `CONTROL`. [См. полное описание значений](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/emulspbutton-application).
1. **Дополнительная кнопка**: LTools.Common.Model.VirtualKey. Позволяет указать вторую клавишу в комбинации, если она требуется. По умолчанию `NONE` - не задана. Щелкните выпадающий список, чтобы выбрать кнопку. Пример: `ESCAPE`. [См. полное описание значений](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/emulspbutton-application).

#### Группа «Процесс»

:bangbang: *Значения этих свойств проигнорируются, если установлен чекбокс **Новое ядро***. 

![](../../resources/basic/desktop/hot-key-emul-proccess-parameters-2.png)

Предназначены для указания комбинации клавиш для эмуляции: 

1. **Спецкнопки**: String. Эмулируемые спецкнопки. По умолчанию `"{ENTER}"`. С полным перечнем спецкнопок можно ознакомиться [на сайте Microsoft](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send).

    Убедитесь, что установлен **Режим без кода (выкл)**. Иначе могут возникнуть непредвиденные символы.

    ![](../../resources/basic/desktop/hot-key-emul-no-code.png)

1. **Асинхронный**: Boolean. Определяет тип ввода: синхронный или асинхронный. По умолчанию галочка не установлена - используется синхронный ввод. Отличия:
   * Синхронный - в этом режиме кнопки нажимаются одновременно. Например, если нужно нажать `Ctrl` + `A`, то обе клавиши активируются в один момент времени.
   * Асинхронный - в этом режиме между последовательными нажатиями происходит пауза. Например, при задержке в 500 миллисекунд будет сначала нажата первая клавиша, а через 500 мс - вторая.
1. **Пауза\***: Int32. Пауза в миллисекундах до и после нажатия кнопки. По умолчанию `500`.
1. **Таймаут\***: Int32. Предельное время ожидания завершения процесса в миллисекундах. По умолчанию `10000`.

### Пример эмуляции

Пример для эмуляции комбинации клавиш `Ctrl` + `A`.

С использованием **Нового ядра**:

* Новое ядро: Включено
* Основная кнопка: `VK_A`
* Модификатор: `CONTROL`

С использованием **Спецкнопки**:

* Новое ядро: Выключено
* Спецкнопки: `"^A"`

## Learning

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, обучающий работе с элементом:

1. Скачайте архив со всеми обучающими материалами.
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities > Ru > Рабочий стол > Эмуляция спецкнопки.ltw` для просмотра.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
_lib.LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}
{% endtabs %}

## Полезные материалы

1. [Приложение 1. Кнопки для эмулирования](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_desktop/emulspbutton-application) - описание значений для свойств **Основная кнопка**, **Модификатор** и **Дополнительная кнопка**.
2. [Описание значений для свойства Спецкнопки](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send).
