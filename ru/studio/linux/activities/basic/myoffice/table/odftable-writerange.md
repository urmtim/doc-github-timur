# Запись диапазона

![](../../../resources/basic/myoffice/table/Cropped-WriteRange.png)

Элемент записывает данные в указанный диапазон ячеек Excel.

**Общие сведения**:

Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els-odf/els-table/el-odftable-save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.
                                                                                                         |
1. **Диапазон\*** *[String]*: Диапазон записи ячеек. Пример: `"A1:D12"`.
2. **Всю строку** *[Boolean]*: Добавить строку целиком. Свойство следует применять, если на странице Excel настроен фильтр.
3. **Добавлять заголовки** *[Boolean]*: Добавлять заголовки колонок таблицы.
4. **Страница** *[String]*: Наименование страницы. Если заполнен индекс, лист в целевом файле может быть переименован.
5. **Индекс страницы** *[Int32]*: Порядковый номер страницы. Отсчет начинается с 0.
6. **Как текст** *[Boolean]*: Установите галочку, чтобы вставить значение как текст. **Если установлена, то свойство «Строгая типизация» нужно выключить!**
7. **Создавать лист**: Создавать лист в случае, если его не существует.
8. **Перезаписать** *[Boolean]*: Определите, нужно ли перезаписывать данные.
9. **Направление**: Направление сдвига ячеек.
10. **Раширять диапазон**: Автоматически расширять диапазон до размеров данных.
11. **Строгая типизация** *[Boolean]*: Признак строгой типизации таблиц. По умолчанию включено. Строгая типизация не дает изменять формат данных при записи в таблицу. При отключении параметра возможна ситуация, когда числовой формат ошибочно преобразуетсся в строку.
12. **Переменная (текст)** *[List\<List\<string>>]*: Переменная для хранения данных записи текстовых значений.
13. **Переменная (информация)** *[List\<List<[LTools.Office.Model.ExcelCellInfo](datatypes/excelcellinfo.md)>>]*: Переменная для хранения данных, содержащих информацию о ячейках.
14. **Переменная (таблица)** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-7.0)]*: Переменная для хранения данных текстовых значений.

 ## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.AppendRange(data, range, [overwrite], [sheet], [sheetIdx], [numFormat], [entireRow]);`  
`app.AppendRange(data_info, range, [overwrite], [sheet], [sheetIdx], [numFormat], [entireRow]);`    
`app.AppendRange(dataTable, range, [overwrite], [sheet], [sheetIdx], [numFormat], [entireRow]);`  

