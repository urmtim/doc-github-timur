# ВЕРСИЯ ПОД WINDOWS

# Редактор диалогов

Редактор диалогов служит для создания пользовательских диалогов и работает совместно с элементами группы "Пользовательские формы".

![](<../../.gitbook/assets/image (122).png>)

Для добавления элемента в форму диалога просто перетащите его из палитры "Элементы".

Свойства элемента задаются в палитре "Свойства". Основным свойством является "Наименование", при помощи этого свойства происходит внешнее взаимодействие с элементом.

Для создания нового диалога нажмите кнопку "Новая форма". Для сохранения диалога используйте кнопки "Сохранить" или "Сохранить как". Для открытия файла диалога используйте кнопку "Открыть". Для проверки внешнего вида диалога используйте кнопку "Тестировать форму".

Сохраненный диалог можно использовать в элементе "Пользовательская форма", указав путь к файлу шаблона в его свойствах. Для передачи данных элементам управления используйте свойство "Данные" (группы Форма). Например, если у Вас имеется текстовое поле с именем "textbox", значение ему можно задать конструкцией:

```
forminput.TextEdit.Add("textbox", "test text")
```

где forminput - переменная типа LTools.UserInteractions.UserFormResult, а "test text" - значение, которое необходимо передать элементу.&#x20;

Получить значения элементов можно из переменной, указанной в свойстве "Данные" (группы Вывод). Например, значение текстового поля с именем "textbox" можно получить следующей конструкцией:

```
formdata.TextEdit["textbox"]
```

Окно диалога будет появляться пока не нажата кнопка закрытия окна, либо не вызван элемент "Закрыть форму". Чтобы получить имя последней нажатой кнопки, можно воспользоваться конструкцией (закрытие окна возвращает null):

```
formdata.Action
```
