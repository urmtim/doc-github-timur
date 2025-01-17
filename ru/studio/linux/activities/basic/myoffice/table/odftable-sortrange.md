# Сортировка диапазона

![](../../../resources/basic/myoffice/table/Cropped-SortRange.png)

Компонент, устанавливающий сортировку диапазона ячеек Excel.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон\*** *[String]*: Диапазон считывания ячеек (A1:D12). Если не указан, будет отсортирован выделенный диапазон.
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.
4. **Направление\***: Направление сортировки.                                   

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.SortRange(range, [dir], [sheet], [sheetIdx]);`
