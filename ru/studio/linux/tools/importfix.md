# ВЕРСИЯ ПОД WINDOWS

# PrimoImportFix

PrimoImportFix - встроенная в Студию утилита, которая позволяет корректировать \*.ltw файлы Primo Studio, сформированные после процедуры [импорта](https://docs.primo-rpa.ru/primo-rpa/primo-studio/instrumenty/import) из проекта UiPath. Инструмент доступен на вкладке **Инструменты > Открыть PrimoImportFix**:

![](<../../.gitbook/assets/tools-open-fix.png>)

Корректировка представляет собой замену участков кода с помощью последовательного применения регулярных выражений (RegExp) к содержимому файлов \*.ltw. Целью корректировки является исправление типовых ошибок импорта, связанных с различиями синтаксиса кода UiPath Studio и Primo Studio. Такие ошибки могут встречаться в импортируемом проекте многократно, поэтому использование приложения существенно экономит время при переносе проекта с UiPath на платформу Primo.

Исправления могут включать в себя:
* замену синтаксиса скриптов внутри модулей;
* добавление/корректировку самих модулей и их свойств.

Для корректировки достаточно открыть программу, выбрать все или несколько файлов  \*.ltw в папке **Primo** импортированного проекта и нажать кнопку **Старт**. В результате более 70% ошибок будут исправлены автоматически.

Дополнительные возможности программы позволяют изменять существующий набор операций исправления кода (набор регулярных выражений), добавлять новые, сохранять и восстанавливать индивидуальные настройки. Перечисленные функции открываются по кнопке **Настройки**.

Файлы перед исправлением программой PrimoImportFix сохраняются как резервные копии в подпапке **Backup** проекта, с отметкой времени изменения в имени файла. Они легко могут быть восстановлены в случае каких-либо некорректных правил редактирования. Таким образом, пользователь, обладая знаниями синтаксиса RegExp, может экспериментировать с настройками, максимально оптимизируя автоматическое исправление ошибок и не опасаясь повредить свой проект.

## Быстрый старт

После запуска PrimoImportFix появится диалог с предложением выбрать один или несколько \*.ltw файлов проекта для преобразования. Выбрать одновременно несколько файлов можно, используя кнопку мышки и клавишу `Ctrl`:

![](<../../.gitbook/assets/importfix_start1.png>)

После этого вы перейдете в основное окно программы. Здесь, в разделе файлов проекта, будут отмечены выбранные файлы. Выбор можно скорректировать путем установки или снятия флажков напротив имен файлов:

![](<../../.gitbook/assets/importfix_start2.png>)

В дальнейшем папку с проектом можно изменить, исправив путь в верхнем левом поле редактирования или вызвав диалог открытия файлов кнопкой с изображением папки:

![](<../../.gitbook/assets/importfix_start3.png>)

Нажатие на кнопку **Старт** запустит преобразование выбранных слева файлов.

Если в ходе обработки какой-то из файлов не подвергнется изменению (не будет найдено ошибок, удовлетворяющих списку правил исправления), то программа выдаст сообщение: **"Исправлений для файла *** не найдено"**.

![](<../../.gitbook/assets/importfix_start.gif>)

В конце преобразования всех файлов появится информационное сообщение об успешном завершении операции:

![](<../../.gitbook/assets/importfix_start4.png>)

После чего утилиту можно закрыть и вернуться в Primo Studio для дальнейшей работы.

## Описание интерфейса программы

![](<../../.gitbook/assets/importfix_interface3.png>)

1. Папка с Primo Studio проектом. Путь к проекту можно изменить вручную или с помощью кнопки диалога, справа от поля ввода. Программа при этом контролирует наличие \*.ltw файлов в выбранной папке.
2. Раздел выбора файлов для конвертации. После выбора папки с проектом в этом поле отобразятся все \*.ltw файлы из данной папки. Выбрать файлы для конвертации можно с помощью кнопки мыши, двойным кликом или клавишей пробела.
3. Раздел, соответствующий подпапке **Backup** в папке с проектом. Тут отображаются резервные копии \*.ltw файлов, которые создаются при нажатии на кнопку **Старт** до процедуры изменения. Названия файлов состоят из начального имени, символа минус `-` и последующей метки даты-времени. Если до этого преобразование файла не проводилось, то метка времени будет пустой, что соответствует начальному состоянию файла (импортированного средствами программы Primo Studio).
4. Кнопка запуска преобразования выбранных \*.ltw файлов. Преобразуются не выделенные файлы, а выбранные галочкой. После успешного преобразования галочка у этих файлов снимается. В конце преобразования всех выбранных файлов появится информационное сообщение об успешном завершении операции.
5. Кнопка восстановления файлов. Она становится активной только после того, как в разделе резервных копий файлов будет выбран хоть один файл. Восстанавливаются не выделенные файлы, а выбранные галочкой. Например, если выделен файл `Main-220603105118.ltw`, то после нажатия кнопки **Восстановить** соответствующий файл из подпапки .\Backup скопируется с перезаписью в файл `Main.ltw`. **При этом желательно, чтобы соответствующий файл `Main.ltw` не был открыт в Primo Studio!**
6. Кнопка **Настройки** открывает или закрывает нижнюю панель настроек, содержащую список операций, которые последовательно выполняются при нажатии на кнопку **Старт**.
7. Выбор оформления программы (скина) из раскрывающегося списка. Выбранное оформление сохраняется при закрытии и восстанавливается при открытии программы. Настройки программы хранятся в профиле пользователя Windows – папке `%APPDATA%\PrimoImport\`.
8. Галочка **Режим разработчика** включает или отключает расширенный режим настроек.
9. Таблица последовательности производимых изменений, которые происходят при нажатии на кнопку **Старт**. Галочкой **Активно** можно отключать или включать выбранное действие. Вид таблицы меняется в зависимости от состояния галки **Режим разработчика**.
10. Кнопка диалога загрузки настроек таблицы изменений из файла в бинарном формате \*.fds или текстовом \*.xml.
11. Кнопка диалога сохранения текущей таблицы изменений в бинарный формат \*.fds или текстовый \*.xml.
12. Кнопка восстановления таблицы изменений по умолчанию, которая хранится внутри программы и меняется с каждой версией программы.

## Восстановление исходных файлов из резервных копий
Перед каждым изменением файла происходит его резервное копирование. Файл копируется в подпапку Backup, расположенную рядом с файлом \*.ltw. При этом к имени файла добавляется постфикс, начинающийся с символа минус и с последующей метки даты и времени вида `-YYMMDDhhmmss`.

Например, выбран файл `D:\Projects\FiscalizationPays_Primo\Main.ltw`. Перед преобразованием он скопируется с именем `D:\Projects\FiscalizationPays_Primo\Backup\Main-220601170530.ltw`, если запуск был произведен 01.06.2022 в 17:05:30. Если соответствующих резервных копий не было найдено в папке Backup, то файл `Main.ltw` будет скопирован с именем `Main-.ltw` (без отметки времени). Такие файлы будут соответствовать исходным файлам, получившимся сразу после импорта. При восстановлении файла происходит его обратное преобразование с перезаписью файла `Main.ltw` (из данного примера).

Чтобы восстановить файл, необходимо отметить нужные файлы резервных копий и нажать кнопку **Восстановить**:

![](<../../.gitbook/assets/importfix_backup1.png>)

Удалить резервные копии из списка и, соответственно, из папки Backup можно при помощи команды контекстного меню **Удалить резервный файл**:

![](<../../.gitbook/assets/importfix_backup2.png>)

## Настройки программы
При нажатии на кнопку **Настройки** появится нижняя панель с таблицей последовательности настроек исправлений (настроек поиска и замены текстовых фрагментов \*.ltw файлов). Если пользователь знаком с синтаксисом регулярных выражений (RegExp), то он может включить режим разработчика соответствующей галочкой в нижнем левом углу, чтобы увидеть скрытые столбцы таблицы, соответствующие RegExp-выражению поиска (столбец  **Выражение**) и столбец с шаблоном замены (столбец **Замена**). Дополнительно отобразятся кнопки сохранения/восстановления таблицы настроек (см. раздел [Описание интерфейса программы](https://docs.primo-rpa.ru/primo-rpa/primo-studio/tools/importfix#opisanie-interfeisa-programmy)):

![](<../../.gitbook/assets/importfix_settings1.png>)

С помощью регулярных выражений можно не только исправить ошибки, связанные с разницей в синтаксисе команд Visual Basic и C#, но и изменять свойства модулей Primo. Например, в операции 17 производится установка параметра **DBConnect** во все модули работы с базой данных, такие как [**Вставка данных**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_insertdata) или [**Выполнить запрос**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_exec):

![](<../../.gitbook/assets/import-regex-17.png>)

К сожалению, после штатного импорта UiPath проекта этот параметр теряется. Если у вас присоединение к базе данных имеет другое имя, то можно его переименовать в `DBConnect` или совсем отказаться от выполнения подстановки `DBConnect`, сняв галочку активности с операции №17 перед нажатием на кнопку **Старт**. Также можно изменить в поле **Замена** имя `DBConnect` на другое имя подключения, соответствующее проекту, например на `Connect1`, тогда поле **Замена** изменится следующим образом:

Старое значение: `$1$2<Value xsi:type="xsd:string">DBConnect</Value>$2$3`\
Новое значение: `$1$2<Value xsi:type="xsd:string">Connect1</Value>$2$3`

В программе есть возможность выборочно выполнять отдельные правила замены на нужных файлах. Это можно сделать, выбрав пункт контекстного меню **Выполнить текущую операцию с выбранным файлом**, вызванный на любой строке регулярного выражения. При этом не нужно нажимать кнопку **Старт**. Выделенная команда замены выполнится независимо от положения флажка активности. Резервная копия файла будет создана так же, как если бы вы нажали на кнопку **Старт**.

![](<../../.gitbook/assets/importfix_settings2.png>)

Добавляя или изменяя строки регулярных выражений, можно значительно расширить автоматизацию исправления ошибок импорта, анализируя разницу между исходными файлами, полученными после Primo-импорта, и файлами, исправленными вручную. Такое сравнение можно проводить, например, используя плагин **Compare** программы [Notepad++](https://notepad-plus-plus.org/downloads/):

![](<../../.gitbook/assets/importfix_settings3.png>)

![](<../../.gitbook/assets/importfix_settings4.png>)

Таким же образом можно тестировать новые регулярные выражения, проверяя корректность преобразования. Справочник по регулярным выражениям можно просмотреть [здесь](https://docs.microsoft.com/ru-ru/dotnet/standard/base-types/regular-expression-language-quick-reference) или [здесь](https://regex.sorokin.engineer/ru/latest/regular_expressions.html).


## Внешний вид интерфейса

Утилита PrimoImportFix позволяет менять внешний вид с помощью выбора скинов. Настройки выбора сохраняются в профиле пользователя:

![](<../../.gitbook/assets/importfix_skin.gif>)
