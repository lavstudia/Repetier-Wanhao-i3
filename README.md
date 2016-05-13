# Repetier-Wanhao-i3
Repetier Firmware v0.92.7 для Wanhao Duplicator i3 V2 (плата управления Melzi).

# Особенности
**Внимание!!!** Более позднии версии Repetier Firmware загружаться в плату Melzi - **НЕ БУДУТ (из-за нехватки памяти)!!!**

**Все действия вы делаете на свой страх и риск. Автор не несет ответственности за возможные последствия!!!**

# Установка
1) Подключить компьютер к блоку управления Wanhao Duplicator i3, через USB

2) Экспортировать настройки из EEPROM. Лучше всего это сделать с помощью программы Reperier Host - https://github.com/repetier/Repetier-Host/wiki/EEPROM-settings

3) Скачать Arduino IDE (проверено на версиях: 1.6.7, 1.6.8, 1.6.9) для исправления и загрузки прошивки в Wanhao Duplicator i3 - https://www.arduino.cc/en/Main/Software

4) Установить Arduino IDE

5) Запустить Arduino IDE

6) Обеспечить поддержку платы Melzi в Arduino IDE: для этого необходим Sanguino в меню (на старых версиях Arduino IDE не работает) -

  * Меню - `Файл -> Настройки`
  * В поле ввода `Additional Boards manager URLs`: вставить адрес - `https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json`
  * Нажать **OK**
  * Меню - `Инструменты -> Плата -> Boards Manager...`
  * В окне **Boards Manager** - найти `Sanguino`, выбрать его и появится кнопка `Install`, которую нужно нажать для установки поддержки плат Melzi
  * После установки появиться надпись `INSTALLED`
  * Необходимо выбрать Плату - `Sanguino`, Процессор - `ATmega1284 or ATmega1284P (16 MHz)` и Порт

7) Скачать ZIP файл данного репозитория и распаковать (в удобное для вас место на диски)

8) Открыть файл `Repetier.ino` - папка `Repetier-927`, из Arduino IDE

9) Меню - `Файл -> Скетч -> Загрузка`

10) После удачной прошивки - импортировать настройки в EEPROM (заранее экспортированные на "2)" этапе)
