---
description: Save attachment
---

# Сохранить вложение

Элемент позволяет сохранить вложение письма.

![](../../../resources/basic/mail/exchange/image-(773).png)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                                                     | Описание                           |
| ------------ | ----------------------------------------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                                                  | Путь к файлу. Пример: `"C:\\folder\\files.ext"` |
| Вложение     | [LTools.Office.Model. OMailAttachment](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailattachment) | Название переменной, хранящей вложение письма. Например, фото, документ, а с версии 1.23.11 вложением может быть и другое письмо (в виде файла \*.eml) |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.SaveAttachment(att, "C\\file");
```
{% endtab %}

{% tab title="Python" %}
```python
app.SaveAttachment(att, "C\\file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SaveAttachment(att, "C\\file");
```
{% endtab %}
{% endtabs %}
