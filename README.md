# Скрипт предварительной конфигурации OS Window & установки специаального программного обеспечения (СПО) ЗАО "ПЕЛЕНГ"
### АННОТАЦИЯ
#### Данный README описывет технологию работы с конфингурационным скриптом.
Скрипт предусматриваеи установку и настройку следующих устройств: 
+ блоки БРИ из состава изделия «СМАР-Т»;
+ блоки АРМВ из состава изделия «СМАР-Т»;
+ блоки БВЗ из состава изделия «СМАР-Т»;
+ блоки БОИ из состава изделия «Мастер»;
+ блоки БКДИ из состава изделия «АСК-РЛС»;
+ блоки БХС из состава изделия «Тахион»;
+ блоки БОИ из состава изделия КАПС ИС;
+ блоки БОИ из состава изделия Плановый сервер;
+ блоки БС из состава изделия ТДК «Мастер-Т».

### ТРЕБОВАНИЯ К ПЕРВРНАЧАЛЬНОМУ ЗАПУСКУ СКРИПТА
1. На поставочном блоке должна быть установлена операционная система MS Windows.
1. На установочном носителм в папке «X:\setup» должны находиться 3 подпапки: «script», «soft_environment» и «soft_install», содержащие необходимый системный и инсталяционный программный продукт.

### РАБОТА СО СКРИПТОМ
1. После загрузки ОС при помощи проводника зайти на съемный диск в папку «X:\setup» и запустить файл «run.cmd». Этот исполняемый файл запустит от имени администратора файл «main.cmd» и передаст ему все параметры с которыми был запущен сам. Допускается запустить файл «main.cmd» непосредственно из пвпки  «X:\setup\script», но тогда, если он был запущен не с правами администратора работа будет прервана с соответствующим сообщением.

1. Выбрать тип поставочного изделия из списка, нажав для этого соответствующую цифру:
    >  1. изделие СМАР‑Т;
    >  1. изделие Мастер;
    >  1. изделие АСК-РЛС;
    >  1. изделие Тахион;
    >  1. изделие КАПС ИС;
    >  1. изделие Плановый сервер;
    >  1. изделие ТДК «Мастер-Т».

1. Далее необходимо указать номер блока который будет конфигурироваться. Например, при конфигурировании блока для изделия  «Мастер» вводится цифра от 1 до 3.

1. Работа скрипта предусматривает интерактивный режим, когда оператор отвечает на вопросы, касающиеся особенносией установки, настройки и работы СПО. При этом пользователю предлагаются варианты ответов по умолчанию, которые хранятся в файле «X:\setup\script\main.xml». Для ускорения процесса конфигурации/установки предусмотрен "тихий" режим (опцмя -Y), в этом случае пользователю задается только вопрос о типе изделмя и порядковом номере блока. Дальнейшая работа проходит без участия пользователя. Полный перечень опций запуска скрипта приведен в конце документа.

1. В процессе работы "script" проводит настройку имени пользователя и пароля. В случае если новое имя пользователя не совпадает с текущим "script" выполнит команду "logoff". Псле чего опреатор должен зарегистрироваться в системе под новым пользователем с указанным ранее паролем. После загрузки OS MS Windows повторно запустить файл «X:\setup\script\main.cmd» (без указания опций).

1. По окончании успешного выполнения будет выполнена повторная  перезагрузка.

1. Настройка завершена.

1. Использование: run.cmd [args] или script\main.cmd [args]  
    > [args] могут принимать следующие значения:  
    >  - -D [1|..] : включить отладочный режим. Будет производится вывод дополнительной информации;  
    >  - -O [path\to\file.ext]: включить режим вывода информации в файл [по умолчанию - %PROGRAMDATA%\logfiles\install.log];  
    >  - -S on^|off  : если задан явно, то однозначно определяет режим вывода информации в консоль; если не задан, то вывод в консоль будет отключён при параметрах -E или -G [по умолчанию включён];  
    >  - -In : установить номер изделия, где n:  
    >>  1. СМАР-Т
    >>  1. Мастер
    >>  1. АСК
    >>  1. Тахион
    >>  1. Информационный сервер
    >>  1. Плановый сервер
    >>  1. ТДК [Блок Связи]
    >  - -Bn : установить номер блока [1, 2, и т.д];
    >  - -G  : разрешить графический интерфейс [GUI]. По умолчанию выбран режим командной строки [CLI];
    >  - -C  : сбросить все заданные ранее настройки [флаги] и выполнить скрипт с запросом всех параметров;
    >  - -F path\to\file.ext : использовать file.ext для конфигурирования процесса установки,если не задан, то ищется файл с именем main.xml;
    >  - -Y  : отвечать 'ДА' на все вопросы ['тихий' режим];
    >  - -H  : эта справочная информация.

1. Пример:
> main.cmd -i2 -b1 -y - будет выполнена 'тихая' установка СПО 'Мастер' на ПК с назначением ему имени 'BOI-1'
