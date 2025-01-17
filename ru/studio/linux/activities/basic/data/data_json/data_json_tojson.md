# Объект к JSON

![](../../../resources/basic/data/data_json/image-(100)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(1)-(14).png)

![](../../../resources/basic/data/data_json/image-(285).png)

Компонент преобразует объект к JSON.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип     | Описание                                                                                                                                                                                          |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _**Обработка:**_ |         |                                                                                                                                                                                                  |
| Данные\*        | Object  | Исходный объект                                                                                                                                                                                   |
| _**Вывод:**_     |         |                                                                                                                                                                                                  |
| Переменная\*    | String  | Переменная, получающая результирующую строку JSON                                                                                                                                                 |
| Форматировать   | Boolean | Определите, нужно ли форматировать строку JSON, добавив отступы для комфортного чтения. Если галочка установлена, JSON отформатируется. Если нет, то данные будут отображаться в одну JSON-строку |

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
string ret = Newtonsoft.Json.JsonConvert.SerializeObject(obj);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = Newtonsoft.Json.JsonConvert.SerializeObject(obj)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.Newtonsoft.Json.JsonConvert.SerializeObject(obj);
```
{% endtab %}
{% endtabs %}
