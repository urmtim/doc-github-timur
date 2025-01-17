# ВЕРСИЯ ПОД WINDOWS

# Импорт

Плагин **Импорт** служит для трансформации RPA-проектов, изготовленных на базе технологии MS Workflow Foundation, в проект Primo. Используется для импорта проектов с платформы UiPath.

Процедура импорта состоит из двух шагов:
1. **Импорт проекта и его активностей из UiPath**. На выходе получаем импортированный проект, который может содержать ошибки из-за разницы синтаксиса платформ.
2. **Преобразование синтаксиса в получившемся проекте**. Конвертация из VB в C#, а также исправление возможных ошибок с помощью утилиты PrimoImportFix.

## Запуск импорта

Для импорта проекта или его части в Primo Studio:

1\. Выберите раздел меню **Инструменты > Импорт**, чтобы открыть диалог импорта:

![](<../../.gitbook/assets/tools-import.png>)

2\. В открывшемся окне перейдите в настройки импорта (цифра 1 на рисунке ниже):
   * **Convert VB to C#** - запускает автоматическое преобразование синтаксиса Visual Basic в C# с помощью инструмента PrimoImportFix сразу после импорта проекта. Установите отметку, если требуется включить параметр.
   * **Omit commented** - исключает закомментированные строки. Установите отметку, если требуется включить параметр.
   * **Import virtual Foreach variable** - импортирует переменную ForEach виртуально. Установите отметку, чтобы виртуальная переменная в цикле For Each не заместилась локальной.

Нажмите **ОК**, чтобы применить настройки.

![](<../../.gitbook/assets/import-settings-2.png>)

3\. В поле **Source** укажите путь до файла проекта в формате \*.json и нажмите кнопку **Refresh**:

![](<../../.gitbook/assets/image (347).png>)

4\. В случае успеха в таблице появится список файлов проекта. Проставьте отметки рядом с теми файлами, которые нужно импортировать, либо нажмите кнопку **Check all** ![](<../../.gitbook/assets/import-check-all.png>), чтобы выбрать сразу весь список.

5\. В поле **Destination** введите путь до папки, в которую будет помещен созданный проект Primo. Он сохранится с изначальным именем импортируемого проекта:

![](<../../.gitbook/assets/import-destination.png>)

6\. Для запуска процедуры нажмите кнопку **Import**. Все успешно импортированные файлы будут помечены зеленой галочкой.

7\. В конце появится окно с результатом успешно импортированных файлов и процент найденных ошибок:

![](<../../.gitbook/assets/диалог-импорт.png>)

После чего окно импорта закроется, а созданный проект будет открыт в Студии.


## Конвертация синтаксиса

Если при импортировании проекта не была включена настройка **Convert VB to C#**, то преобразовать его синтаксис можно постфактум. Для этого закройте все процессы проекта, оставив открытым только сам проект, и выберите пункт меню **Инструменты > Преобразовать синтаксис**:

![](<../../.gitbook/assets/tools-convert.png>)

В результате будет запущен инструмент PrimoImportFix, который начнет конвертировать все файлы текущего проекта, включая вложенные папки.

## PrimoImportFix

Существует возможность отдельно открыть утилиту PrimoImportFix, и уже через нее выбрать нужный файл для:
* преобразования синтаксиса;
* восстановления из папки Backup (хранит исходные файлы проекта после импорта);
* изменения правил конвертации, включая добавление собственных правил в формате RegExp.

Чтобы это сделать, воспользуйтесь пунктом меню **Инструменты > PrimoImportFix**:

![](<../../.gitbook/assets/tools-open-fix.png>)

И далее работайте с утилитой [по этой инструкции](https://docs.primo-rpa.ru/primo-rpa/primo-studio/tools/importfix).
