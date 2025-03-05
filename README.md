Log Management Script
Этот скрипт предназначен для управления лог-файлами в указанной директории. Он выполняет следующие действия:

Очищает лог-файлы, которые не изменялись более 30 дней.

Перемещает лог-файлы, которые изменялись менее 7 дней, в резервную директорию.

Создает архив резервной директории и удаляет её после архивации.

Логирует все действия в файл log_log.log и отправляет уведомления по электронной почте (если установлен msmtp).

ТРЕБОВАНИЯ
ОС: Скрипт работает в Unix-подобных системах (Linux, macOS).

УТИЛИТЫ:

- find — для поиска файлов.

- date — для работы с датами.

- tar — для создания архивов.

- msmtp (опционально) — для отправки уведомлений по электронной почте.

Использование
Скачайте скрипт:

git clone https://github.com/ZZZHUKKK/Checklogs.git
cd Checklogs

Сделайте скрипт исполняемым:

chmod +x script.sh

Запустите скрипт:

./script.sh /path/to/logs /path/to/backup

#/path/to/logs — путь к директории с лог-файлами.
#/path/to/backup — путь к директории для резервных копий.

ФУНКЦИОНАЛЬНОСТЬ
1. Очистка старых лог-файлов
Лог-файлы, которые не изменялись более 30 дней, очищаются (содержимое удаляется).

2. Перемещение недавних лог-файлов
Лог-файлы, которые изменялись менее 7 дней, перемещаются в резервную директорию.

3. Архивация резервной директории
Резервная директория архивируется в файл с именем в формате YYYY_MM_DD_HH_MM_SS.tar.gz.

4. Логирование
Все действия логируются в файл log_log.log.

Если установлен msmtp, уведомления отправляются на электронную почту.

Пример вывода логов
Файл log_log.log будет содержать записи в формате:


||  File /path/to/logs/example.log has been cleared   ||  2023-10-02 12:34:56   ||
||  Backup directory /path/to/backup/2023_10_02_123456_backup has been created   ||  2023-10-02 12:35:00   ||
||  File 2023_10_02_123456.tar.gz has been created   ||  2023-10-02 12:35:10   ||
||  Dir /path/to/backup/2023_10_02_123456_backup has been removed   ||  2023-10-02 12:35:15   ||
Настройка отправки уведомлений
Для отправки уведомлений по электронной почте:

Установите msmtp:

sudo apt install msmtp  # Для Debian/Ubuntu
brew install msmtp     # Для macOS

Настройте msmtp, указав SMTP-сервер и учетные данные в файле конфигурации ~/.msmtprc.

Автор: ZZZHUKKK
GitHub: ZZZHUKKK

