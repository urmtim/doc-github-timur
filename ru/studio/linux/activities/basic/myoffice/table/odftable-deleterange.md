# Удаление диапазона

![](../../../resources/basic/myoffice/table/Cropped-DeleteRange.png)

Компонент, удаляющий диапазон ячеек в Excel.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон\*** *[String]*: Диапазон удаления ячеек. Пример: `A1:D12`. Если не указан, будет удален выделенный диапазон.
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.
4. **Только ячейки** *[Boolean]*: Признак того, что будут уничтожены только ячейки диапазона, а не колонки и строки целиком.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.RemoveRange(range, [cellsOnly], [sheet], [sheetIdx]);`  
