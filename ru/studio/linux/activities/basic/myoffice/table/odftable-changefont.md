# Изменение шрифта

![](../../../resources/basic/myoffice/table/Cropped-WriteFormula.png)

Компонент, изменяющий шрифт диапазона ячеек в Excel.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Диапазон\*** *[String]*: Диапазон ячеек. Пример: `A1:D12`.
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.
4. **Цвет** *[System.Drawing.Color?]*: Цвет шрифта. Пример: `System.Drawing.Color.Black.
5. **Размер** *[double?]*: Размер шрифта.
6. **Полужирный**: Полужирный.
7. **Наклонный**: Наклонный.
8. **Подчеркнутый**: Подчеркнутый.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`    
`app.SetFont(data, range, color, size, bold, italic, underline, [sheet], [sheetIdx]);`
