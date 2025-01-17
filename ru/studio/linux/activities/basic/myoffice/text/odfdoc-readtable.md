# Прочитать таблицу

![](../../../resources/basic/myoffice/text/Cropped-ReadTable.png)

Элемент, читающий таблицу из документа. Элемент работает корректно только внутри контейнера Word

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Индекс\*** *[Int32]*: Порядковый номер таблицы.
2. **Данные** *[List\<List\<String>>]*: Данные таблицы.
3. **Таблица** *[System.Data.DataTable]*: Данные таблицы.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`   
`List<List<string>> list = app.ReadTableArr(idx);`  
`System.Data.DataTable table = app.ReadTable(idx);`
