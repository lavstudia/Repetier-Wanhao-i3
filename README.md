# Repetier-Wanhao-i3
Repetier Firmware v0.92.9 для Wanhao Duplicator i3 v2 (плата управления Melzi).

# Особенности
**Все действия вы делаете на свой страх и риск. Автор не несёт ответственности за возможные последствия!!!**

# Состав

 * Папка `Repetier-929/Repetier` - содержит в себе адаптированные исходники Repetier Firmware v0.92.9 + уже сконфигурированный файл Configuration.h (настройки соответствуют требованиям Wanhao Duplicator i3 v2)
 * Файл `config-dupi3.json` - настройки Repetier Firmware, для Wanhao Duplicator i3 v2

# Установка
1) Включить принтер

2) Подключить компьютер к блоку управления Wanhao Duplicator i3, через USB

3) Экспортировать настройки из EEPROM. Лучше всего это сделать с помощью программы Reperier Host - https://github.com/repetier/Repetier-Host/wiki/EEPROM-settings

4) Скачать Arduino IDE (**ВНИМАНИЕ!!!** проверено на версии: 1.6.9) для исправления и загрузки прошивки в Wanhao Duplicator i3 - https://www.arduino.cc/en/Main/Software

5) Установить Arduino IDE

6) Запустить Arduino IDE

7) Обеспечить поддержку платы Melzi в Arduino IDE: для этого необходим Sanguino в меню (на старых версиях Arduino IDE не работает) -

  * Меню - `Файл -> Настройки`
  * В поле ввода `Additional Boards manager URLs`: вставить адрес - `https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json`
  * Нажать **OK**
  * Меню - `Инструменты -> Плата -> Boards Manager...`
  * В окне **Boards Manager** - найти `Sanguino`, выбрать его и появится кнопка `Install`, которую нужно нажать для установки поддержки плат Melzi
  * После установки появиться надпись `INSTALLED`
  * Необходимо выбрать Плату - `Sanguino`, Процессор - `ATmega1284 or ATmega1284P (16 MHz)` и Порт

8) Скачать ZIP файл данного репозитория и распаковать (в удобное для вас место на диски)

9) Открыть файл `Repetier.ino` - папка `Repetier-929/Repetier`, из Arduino IDE

10) Меню - `Файл -> Скетч -> Загрузка`

11) После удачной прошивки - импортировать настройки в EEPROM (заранее экспортированные на "2)" этапе)

12) Hажать **OK** (Repitier Host посылает настройки в принтер)

13) **НА САМОМ ПРИНТЕРЕ!** зайти в меню `Configuration` и выполнить пункт `Store to EEPROM`

# Модификация
Если необходимо внести собственные изменения в настройку принтера, необходимо:

 * Проделать этапы 1-3 из пункта "Установка"
 * Проделать этапы 4-8 из пункта "Установка" - опционально, **если до этого не выполняли!!!**
 * Открыть конфигуратор Repetier Firmware: https://www.repetier.com/firmware/v092/
 * Загрузить настройки принтера: `Start -> Upload old configuration -> Выберите файл` - выбрать файл `config-dupi3.json` из корня папки скаченного репозитория
 * Произвести собственную модификацию, пользуясь конфигуратором
 * Скачать полученные настройки: `Download -> Download config.json`
 * Скачать полученный конфигурационный файл: `Download -> Download Configuration.h`
 * Заменить конфигурационный файл `Configuration.h` на новый (скаченный), в папке `Repetier-929/Repetier` из корня папки скаченного репозитория
 * Проделать этапы 9-13 из пункта "Установка"
