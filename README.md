# TLGRM - комбинированный скрипт оповещения в Телеграм и удалённого запуска функций, скриптов и команд RouterOS.

В скрипте использованы идеи и часть кода by Sertik, Virtue, Pepelxl, Dimonw, Jotne, Alice Tails, drPioneer.
Для работы скрипта должны быть заранее известны и указаны BotID и ChatID.
Скрипт необходимо добавить в System/Sheduler и установить запуск с нужной периодичностью.
Суть работы скрипта сводится к выполнению двух основных задач:
 - Чтение последнего сообщения в Телеграм-группе на предмет наличия адресованного послания. При наличии такого послания скрипт пытается его разобрать и исполнить.
 - Поиск в журнале устройства сообщений о подозрительных событиях и их пересылка в Телеграм-группу.

Для отправки команды конкретному роутеру в Телеграм-группе, необходимо сформировать текстовое сообщение. Начало сообщения обозначается символом "/", затем указывается имя роутера (должно соответствовать записи в /system identity, при этом регистр букв имеет значение и не должно содержать пробелов), далее через пробел пишется команда.
Для отправки команды всем роутерам в Телеграм-группе вместо имени указывается 'forall'.
В качестве команды могут выступать: имя глобальной функции, имя скрипта или команда RouterOS. Например:

/forall log warning [/system identity get name]

/Mikrotik1 wol

Особенности работы скрипта:
 - поддерживается отправка сообщений в Телеграм-группу с кириллицей
 - непечатные символы при отправке в Телеграм-группу обрезаются
 - сообщение длиной более 4096 перед отправкой в Телеграм-группу обрезается до 4096 символов
 - скрипт читает только ПОСЛЕДНЕЕ сообщение в Телеграм-группе. По этой причине не имеет смысла накидывать сразу много команд, в любом случае будет выполнена только последняя.
 - поддерживается индивидуальная и групповая адресация команд
 - при запуске скрипта в терминале можно наблюдать за ходом его выполнения

Для корректного отображения скриптом 'username' отправителя, в настройках Телеграм должно быть заполнено поле "Имя пользователя", бот должен быть подключен к ГРУППЕ (групповому чату), а не к КАНАЛУ.

https://forummikrotik.ru/viewtopic.php?p=83858#p83858

https://habr.com/ru/post/650563/
