# Заменить текст

![](../../../resources/basic/myoffice/text/Cropped-ReplaceText.png)

Заменяет все вхождения исходного текста на новый.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Исходный текст** *[String]*: Текст, подлежащий замене.
2. **Новый текст\*** *[String]*: Новый текст.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`  
`app.ReplaceText(oldText, newText);`
