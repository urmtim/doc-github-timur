# Документ ODF

![](../../../resources/basic/myoffice/text/Cropped-DocumentODF.png)

Компонент, производящий подключение к приложению ODF Документы. 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Путь к файлу** *[String]*: Путь к файлу документа Word (c:\folder\file.docx).
2. **Пароль** *[String]*: Пароль документа.
3. **Пароль (зашифрованный)** *[SecureString]*: Пароль документа.
4. **Массив байтов** *[byte[]]*: Массив байтов документа.

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`
