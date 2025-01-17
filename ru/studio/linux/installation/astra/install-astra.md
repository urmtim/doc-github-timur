# Установка Primo RPA Studio Linux на Astra Linux

На экране **Настройка учётных записей пользователей и паролей** создайте пользователя-администратора (далее – primo-admin) машины Студии.

![](<../../../.gitbook/assets1/Astra-Linux.png>)

## Настройка дополнительного ПО

Выполните подключение машины студии к репозиториям main, update, base и extended. Сами репозитории описаны в статье [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882) . 
Настройка локальных зеркал этих репозиториев описана в статье [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426).

**!!ВАЖНО!! Локальные репозитории необходимо выгружать на машину, имеющую доступ в Интернет.**

Рекомендуется выделить одну машину под управлением Astra Linux 1.7 для размещения на ней сервера репозиториев.

Проверьте доступность репозиториев, используя следующую команду:

`[primo-admin@astra-studio ~]$ sudo apt update`

Репозитории main, update, base и extended должны присутствовать в выводе команды.

Установите необходимое для работы студии ПО:

`[primo-admin@astra-studio ~]$ sudo apt -y install xsel at xvfb python3 python3-pyatspi python3-numpy xdotool imagemagick python3-opencv wmctrl`

## Установка браузера Chrome

Для регистрации репозиториев в качестве источников пакетов указанные ниже строки должны быть добавлены в файл `/etc/apt/sources.list`
```
deb [trusted=yes] https://deb.debian.org/debian/ buster main contrib non-free
deb https://security.debian.org/debian-security/ buster/updates main contrib non-free
```
Скачайте дистрибутив браузера; для этого необходимо из домашней папки выполнить
```
[primo-admin@astra-studio ~]$ sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```
Откройте домашнюю папку в проводнике и двойным щелчком на файле `google-chrome-stable_current_amd64.deb` выполните установку браузера. После установки файл `google-chrome-stable_current_amd64.deb` можно удалить.

Проверка: выполните указанную ниже команду. Если браузер запустится, установка прошла успешно:
```
[primo-admin@astra-studio ~]$ google-chrome
```

## Установка браузера Яндекс
Для установки браузера выполните команду:
```
[primo-admin@astra-studio ~]$ sudo apt-get install yandex-browser-stable
```

Проверка: выполните указанную ниже команду. Если браузер запустится, установка прошла успешно:
```
[primo-admin@astra-studio ~]$ yandex-browser-stable
```
## Установка Студии
Распакуйте архив Primo.Studio.Linux.zip в удобный каталог, например: `/home/user`. 

Создайте каталог:
```
[primo-admin@astra-studio ~]$ sudo mkdir /opt/Primo/
```
Содержимое папки linux-x64 перенесите в `/opt/Primo/Studio`:
```
[primo-admin@astra-studio ~]$ sudo mv /home/user/linux-x64/ /opt/Primo/Studio/`
```
Распакуйте содержимое архива `/opt/Primo/Studio/x64/AstraOCRx64.zip` в папку `/opt/Primo/Studio/`

## Создание группы пользователей
Для работы пользователя необходима общая группа:
```
[primo-admin@astra-studio ~]$ sudo groupadd primo-rpa
```
Задайте вновь созданную группу для всех элементов папки Студии:
```
[primo-admin@astra-studio ~]$ sudo chgrp -R primo-rpa /opt/Primo/Studio/
```
Задайте права:
```
[primo-admin@astra-studio ~]$ sudo chmod -R 770 /opt/Primo/Studio/
```
## Настройка учетной записи пользователя
Создание учётной записи пользователя `<any_user>`: 
```
[primo-admin@astra-studio ~]$ sudo useradd -g primo-rpa -m -s /bin/bash <any_user>
```
Установка пароля учётной записи пользователя `<any_user>`:
```
[primo-admin@astra-studio ~]$ sudo passwd <any_user>`
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```
После создания учётной записи пользователя на машине Студии войдите в графический сеанс этой учётной записи для инициализации графического окружения и дальнейшей настройки.

Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте:  
**ПКМ на рабочем столе -> Свойства -> Обои, удалить обои и логотип**.

## Установка расширения для браузера Chrome для текущего пользователя
Откройте браузер Chrome, выберите пункт меню **Настройки и управление Google Chrome > Расширения > Управление расширениями**, далее на странице **Расширения** установите настройку **Режим разработчика**:  
![](<../../../.gitbook/assets1/DeveloperMode.png>)  
Выполните перетаскивание файла `/opt/Primo/Studio/Extensions/Chrome/chrome.crx` в браузер Хром на страницу **Расширения**. В результате на странице должно появится расширение Primo RPA Extension:  
![](<../../../.gitbook/assets1/ChromeExtension.png>)

## Установка расширения для браузера Яндекс
Откройте браузер Яндекс, в строке адреса укажите browser://extensions/, нажмите Enter, далее на странице **Расширения** установите настройку **Режим разработчика**:  
![](<../../../.gitbook/assets1/DeveloperMode.png>)  

Выполните перетаскивание файла `/opt/Primo/Studio/Extensions/Chrome/chrome.crx` в браузер Яндекс на страницу **Расширения**. В результате на странице должно появиться расширение Primo RPA Extension:  
![](<../../../.gitbook/assets1/YandexExtension.png>)


## Настройка браузеров Chrome и Яндекс для текущего пользователя

Скрипт `browsers.sh` выполняет регистрацию расширения, установленного для браузеров Хром и Яндекс, для текущего пользователя. 

Запустите скрипт: 

`./opt/Primo/Studio/browsers.sh`

Вывод консоли должен содержать повторяющуюся два раза строчку: 

"Расширение успешно установлено. Перезапустите браузер."

Проверьте регистрацию расширения:

После перезапуска браузера Chrome или Яндекс должен появиться активный процесс LTools.WebBrowser.Native, который должен закрыться сразу после закрытия браузера. Процесс можно увидеть в утилите Системный монитор.

## Запуск Студии

Запустите:

`/opt/Primo/Studio/Primo.Studio`

## Дополнительные настройки

1. **Проблема**: «Отсутствие альфа канала при работе селектора с браузерами». Проблема проявляется как отображения черного экрана во время работы селектора для браузера.  
**Решение**: включите прозрачность в композит-менеджер (по умолчанию ВЫКЛ).  
fly-admin-theme -> «Эффекты» -> «Композитинг» -> «Прозрачность»

![](<../../../.gitbook/assets1/AlphaChannel-Setup.png>)

В случае, если настройка Композит-менеджер не доступна в текущей конфигурации, откройте Студию и в настройках «Общие» установите настройку **Принудительная прозрачность окон**:  

![](<../../../.gitbook/assets1/TransparentWindow-Setup1.png>)

2. **Проблема**: «Смещение элементов в браузере Яндекс». Проблема проявляется во время выбора элемента страницы при помощи пикера браузера, при этом границы выбранного элемента не совпадают с самим элементом.  
**Решение**: В настройках «Интерфейс» -> «Боковая панель» отключите настройку «Показывать боковую панель»

![](<../../../.gitbook/assets1/Sidebar1.png>)

3. **Проблема**: «При запуске браузера Яндекс восстанавливаются закрытые вкладки страниц».  
**Решение**: В настройках «Интерфейс»-> «Вкладки и группы» выключите настройку «При запуске восстанавливать вкладки окон и список закрепленных групп»

![](<../../../.gitbook/assets1/PageRestore.png>)