# Вставка колонок

![](../../../resources/basic/myoffice/table/Cropped-InsertColumn.png)

Элемент вставляет колонки в лист Excel.

**Общие сведения**:

Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els-odf/els-table/el-odftable-save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Кол-во\*** *[Int32]*: Количество вставляемых колонок. По умолчанию `1`.
2. **Индекс** *[Int32]*: Порядковый номер колонки, **слева** от которой добавится новая. Отсчет с нуля. Если не указано, то вставка выполнится в конце листа.
3. **Страница** *[String]*: Наименование страницы. Пример: `"Лист 1"`.
4. **Индекс страницы** *[Int32]*: Порядковый номер страницы Excel, отсчет с нуля. Пример: `0`.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.InsertColumns(index, range, [sheet], [sheetIdx]);`
