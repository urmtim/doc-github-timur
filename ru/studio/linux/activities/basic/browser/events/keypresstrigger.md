# Событие кнопки браузера

![](../../../resources/basic/browser/events/image-(153).png)



Компонент, ожидающий событие нажатия кнопки приложения

| Свойство              | Тип                                           | Описание                              |
| --------------------- | --------------------------------------------- | ------------------------------------- |
| Шаблон поиска         | String                                        | Шаблон поиска элемента управления     |
| Тип браузера          | LTools.WebBrowser.Model. BrowserTypes\_Short  | Тип используемого браузера            |
| Заголовок браузера    | String                                        | Заголовок подключаемого браузера      |
| Основная кнопка\*     | LTools.Common. Model.VirtualKey               | Основная кнопка                       |
| Модификатор           | LTools.Common. Model.VirtualKey               | Кнопка-модификатор (Ctrl, Shift...)   |
| Дополнительная кнопка | LTools.Common. Model.VirtualKey               | Дополнительная кнопка                 |
| Состояние             | LTools.Common.Model. Triggers.KeyTriggerState | Состояние кнопки                      |
| Дочерние              | Boolean                                       | Включая события от дочерних элементов |

