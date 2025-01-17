# Клик OCR-текста мышью

![](../../resources/basic/ocr/ocr-text-screenshot2.png)

Компонент сканирует экран компьютера и производит клик мышью на искомом тексте. Для корректной работы требуется, чтобы текст для клика был полностью виден и не перекрывался окнами других приложений, в том числе Студией (например, при [отладке процесса](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug) она должна быть свернута). 

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип                | Описание                                           |
| --------------- | ------------------ | -------------------------------------------------- |
| ***Настройки OCR:*** | | |
| Переменная\*    | LTools.OCR.OCRInst | Переменная со ссылкой на ядро OCR. Свойство заполняется, только если элемент используется вне контейнера Microsoft OCR/Tesseract OCR/Yandex Vision OCR. Например, если соединение с OCR в вашем процессе было установлено ранее и сохранено в переменную - тогда нужно указать ее в этом свойстве, чтобы подключиться к ядру |
| ***Процесс:*** | | |
| Искомый текст\* | String             | Искомый текст на экране. Пример: `"text"`                    |
| Кнопка мыши\*   | -                  | Кнопка мыши для клика. По умолчанию **INVOKE** - программный клик левой кнопкой мыши через Win32 (осуществляется без наведения курсора). Cуществуют приложения, которые не поддерживают программный клик - в этом случае нужно изменить значение. <p>Доступные варианты: 1) **BUTTON_LEFT** - одинарный щелчок левой кнопкой, который имитирует действие человека: наводит курсор и кликает; 2) **BUTTON_LEFT_DOUBLECLICK** - двойной щелчок левой кнопкой; 3) **BUTTON_RIGHT** - одинарный щелчок правой кнопкой; 4) **BUTTON_MIDDLE** - колесико</p> |
| Индекс          | Int32              | Индекс вхождения искомого текста. При наличии нескольких строк, попадающих под условие поиска, позволяет указать индекс (порядковый номер) нужного текста. По умолчанию `0` - робот кликнет по первой подходящей строке |
| Таймаут\*       | Int32              | Предельное время ожидания завершения процесса (мс). По умолчанию `10000` |
| ***OCR:*** | | |
| Смещение X      | Int32              | Смещение по оси X относительно центра искомого слова/фразы. По умолчанию `0` - клик по центру текста. Значение указывается в пикселях: допустимы положительные и отрицательные значения. При положительном числе смещение будет производиться вправо, при отрицательном - влево. Пример: `10` (клик на 10 пикселей вправо относительно центра) |
| Смещение Y      | Int32              | Смещение по оси Y относительно центра искомого слова/фразы. По умолчанию `0` - клик по центру текста. Значение указывается в пикселях: при положительном числе смещение будет производиться вниз, при отрицательном - вверх |

### Рекомендации

Инструмент OCR-распознавания не обладает 100%-ной точностью, поэтому при неудачном поиске строки пробуйте использовать разные слова из одной искомой фразы (если ищете текст из нескольких слов). 

Также следует проверить, что язык искомого текста и язык, указанный в подключении к ядру OCR, совпадают. Например, вы используете элемент в контейнере [Microsoft OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_ocr/el_ocr_microsoft), и вам нужно найти на экране русский текст. В этом случае убедитесь, что в свойстве **Язык** в Microsoft OCR указано значение `"ru-RU"`.

### Сделать скриншот

Команда **Сделать скриншот**, расположенная на элементе, является информационной и предназначена для пользователя, а не для обработки роботом: 

![](../../resources/basic/ocr/ocr-text-screenshot2.png)

Например, можно сделать скриншот текста на экране, чтобы при просмотре процесса быстрее понять, какой элемент требовалось найти и кликнуть. 

![](../../resources/basic/ocr/ocr-text-screenshot1.png)


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
app.ClickText("text", 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
app.ClickText("text", 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
app.ClickText("text", 10000, 0, 0, _lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}
{% endtabs %}

