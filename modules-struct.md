## Структура модулей BAS

Приветствую всех.
Это первая статья в моём курсе. В данной мы рассмотрим структуру модулей для Browser Automation Studio.

Все модули BAS расположены по пути _apps\Номер.Версии\modules_.
В данной папке вы найдёте стандартные плагины, которые использует программа, а так же, в будущем, и свои личные.

## Структура

У каждого модуля своя отдельная папка, внутри которой расположены все основные файлы, требуемые для его работы.
Название папки с модулем, в принципе, может быть любое, но удобнее всего называть её так же, как и сам плагин, чтобы избежать путаницы и быстро найти его среди остальных.

В Browser Automation Studio, в верхнем контекстном меню вы можете найти опцию _Менеджер модулей_.
С помощью него вы можете:
- Просмотреть все существующие модули.
- Отключить/Включить модуль с помощью комбобокса справа от названия.
- Открыть папку с модулем, кликнув по заголовку модуля.
- Увидеть версию, название и описание модуля.
- Перегрузить модули, чтобы синхронизировать изменения основной папки.

Минимальный набор файлов следующий:
- Картинка модуля
- Файл манифеста

Остальное зависит от случая.

### Первый пример
Если мы используем только Браузер и действие у нас по сути одно, то логика размещается в файле _.js_ формата.
Типичный для данного случая модуль **AjaxReCaptcha**.

Основной файл - _browser.js_. Экшенов тут нет, т.е весь процесс происходит без использования конструктора действий.
Этот файл подключается к модулю через манифест, в разделе **browser**. 

### Второй пример
Если мы используем C++, то, кроме прочего, мы должны добавить _.dll_ файл, библиотеку, в которой содержится вся основная логика.
Типичный для данного случая модуль **CurlWrapper**.

Основной файл здесь - _curlwrapper.dll_. Экшенов тут так же нет.
Этот файл подключается к модулю через манифест, в разделе **dll**.

### Третий пример
Если мы используем логику, которая базируется на JS, то удобнее всего размещать код в отдельном файле, если действий очень много.
А в действиях уже вызывать нужный код из этого файла.
Типичный для данного случая модуль **ReCaptcha2**.

Основной файл здесь - _engine.js_. В данном модуле уже присутствуют экшены, которые возможно будет увидеть через конструктор.
Этот файл подключается к модулю через манифест, в разделе **engine**.

### Итог
Случаи могут быть самыми разными, каждый зависит от ситуации.
Прелесть модульной системы в том, что мы можем создавать как простые функции, работающие по принципу одного из примеров, а так же комбинировать все эти примеры и создавать высоконагруженные, сложные системы.

## Файлы

### **Картинка модуля** - файл в формате _.png_ размером _32x32_. Имя файла обязательно должно быть равно названию модуля.
Её мы будем видеть в разделе конструктора, на экшенах в виде маленькой иконки, в поиске по действиям и так далее.

### **Файл манифеста** - файл с именем _manifest.json_.
Данный файл отвечает за общие настройки модуля, его локализацию.
Именно через него подключаются все зависимости, о которых мы говорили выше.
Именно он содержит конечную информацию об используемых действиях.
То есть, даже если мы создали все файлы действия, но не добавили его в манифест - его мы в BAS не увидим

### **Файлы действий** - данные файлы содержат в себе всю основную логику работы каждого конкретного действия.
Отвечают следующей стандартной структуре:
#### _имя_действия_code.js_ - содержит код, который будет добавлен в ваш скрипт при использовании действия
#### _имя_действия_select.js_ - содержит код, который связывает интерфейс и конечные действия, а так же проверки для переменных и многое другое.
#### _имя_действия_interface.js_ - содержит код интерфейса, т.е. именно то, что мы с вами видим в конструкторе.

### **Файл движка JS** - файл с именем _engine.js_ и ему подобные.
Данный файл отвечает за логику JS кода, который будет выполняться в разных экшенах.
Его структуру мы рассмотрим в следующих статьях.

### **Файл движка C++** - файл библиотеки формата _.dll_
Данный файл отвечает за логику С++ кода, который будет выполняться в разных экшенах.
Его структуру мы рассмотрим в следующих статьях.

### Заключение
На этом мы закончим.
Статья получилась компактной, но для начала, я думаю, этого достаточно.
При поступлении новой информации я буду редактировать все статьи, поэтому следите за обновлениями.
