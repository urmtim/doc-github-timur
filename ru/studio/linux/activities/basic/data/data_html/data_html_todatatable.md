# HTML к DataTable

Преобразовывает HTML-код в коллекцию таблиц. Элемент полезно применять в случаях, когда требуется извлечь таблицы из HTML-кода, например, из тела письма. При этом код может содержать одну и более таблиц. 
 
Важно отметить, что элемент работает исключительно с таблицами. Любой другой контент в HTML-коде, не являющийся таблицей, в результате преобразования отображаться не будет.

![](../../../resources/basic/data/data_html/data_table9.png)


## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Processing:**
-  **HTML\*** *[System.String]*: Переменная, содержащая строку с HTML-кодом. Пример: `<table><tr><th>текст заголовка1</th><th>текст заголовка2</th></tr><tr><td>данные1</td><td>данные2</td></tr></table>`.

![](../../../resources/basic/data/data_html/processing.png)

**Группа Output:**
-  **Tables\*:** *[System.Collections.Generic.List<System.Data.DataTable>]*: Переменная с результатами выполнения элемента, содержащая коллекцию таблиц.

  ![](../../../resources/basic/data/data_html/1.png)



## Пример использования


Вы можете скачать RPA-проект, в котором используется элемент **HTML к DataTable**, в нашем публичном репозитории на [GitHub](https://github.com/PrimoRPA/Learning). 

1. Скачайте архив с обучающими материалами по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте проект `StudioActivities` в вашей среде разработки.
3. Выберите процесс `StudioActivities/En/Data/HTML/HtmlToDataTable.ltw`для просмотра.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Element that extracts DataTables from HTML document.  Properties
//html - HTML: [String] HTML document
List<System.Data.DataTable> ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html);
```
{% endtab %}

{% tab title="Python" %}
```python
#Element that extracts DataTables from HTML document.  Properties
#html - HTML: [String] HTML document
ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html) #List<System.Data.DataTable>
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Element that extracts DataTables from HTML document.  Properties
//html - HTML: [String] HTML document
var ret = LTools.Data.Helpers.HTMLHelper.ParseTable(html) #List<System.Data.DataTable>
```
{% endtab %}
{% endtabs %}
