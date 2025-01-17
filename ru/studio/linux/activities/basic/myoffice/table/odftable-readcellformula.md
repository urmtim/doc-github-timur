# Чтение формулы из ячейки

![](../../../resources/basic/myoffice/table/Cropped-ReadFormulaFromCell.png)

Компонент, производящий считывание формулы из указанной ячейки Excel. 

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
Символ `*` в названии свойства указывает на обязательность его заполнения.

1. **Ячейка\*** *[String]*: Ячейка, из которой нужно извлечь формулу. Пример: `"A4"`.
2. **Страница** *[String]*: Название страницы с указанной ячейкой.
3. **Индекс страницы** *[Int32]*: Порядковый номер страницы, отсчет с 0.
4. **Формула\*** *[String]*: Формула, полученная из ячейки.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`String data = app.ReadCellFormula(cell, [sheet], [sheetIdx]);`
