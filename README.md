# Repetier-Wanhao-i3
Repetier Firmware v0.92.9 для Wanhao Duplicator i3 v2 (плата управления Melzi).

# Особенности
**Все действия вы делаете на свой страх и риск. Автор не несёт ответственности за возможные последствия!!!**

# Состав

 * Папка `Repetier_929/Repetier` - содержит в себе адаптированные исходники Repetier Firmware v0.92.9 + уже сконфигурированный файл Configuration.h (настройки соответствуют требованиям Wanhao Duplicator i3 v2)
 * Файл `config-dupi3.json` - настройки Repetier Firmware, для Wanhao Duplicator i3 v2

# Установка
1) Извлечь MicroSD карту из принтера

2) Включить принтер

3) Подключить компьютер к блоку управления Wanhao Duplicator i3, через USB

4) Экспортировать настройки из EEPROM. Лучше всего это сделать с помощью программы Reperier Host - https://github.com/repetier/Repetier-Host/wiki/EEPROM-settings

5) Скачать Arduino IDE (**ВНИМАНИЕ!!!** проверено на версии: 1.6.9) для исправления и загрузки прошивки в Wanhao Duplicator i3 - https://www.arduino.cc/en/Main/Software

6) Установить Arduino IDE

7) Запустить Arduino IDE

8) Обеспечить поддержку платы Melzi в Arduino IDE: для этого необходим Sanguino в меню (на старых версиях Arduino IDE не работает) -

  * Меню - `Файл -> Настройки`
  * В поле ввода `Additional Boards manager URLs`: вставить адрес - `https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json`
  * Нажать **OK**
  * Меню - `Инструменты -> Плата -> Boards Manager...`
  * В окне **Boards Manager** - найти `Sanguino`, выбрать его и появится кнопка `Install`, которую нужно нажать для установки поддержки плат Melzi
  * После установки появиться надпись `INSTALLED`
  * Необходимо выбрать _Плату_ - `Sanguino`, _Процессор_ - `ATmega1284 or ATmega1284P (16 MHz)` и _Порт_

9) Скачать ZIP файл данного репозитория и распаковать (в удобное для вас место на диски)

10) Открыть файл `Repetier.ino` - папка `Repetier_929/Repetier`, из Arduino IDE

11) Меню - `Файл -> Скетч -> Загрузка`

12) После удачной прошивки - импортировать настройки в EEPROM (заранее экспортированные на "2)" этапе)

13) Hажать **OK** (Repitier Host посылает настройки в принтер)

14) **НА САМОМ ПРИНТЕРЕ!** зайти в меню `Configuration` и выполнить пункт `Store to EEPROM`

# Модификация
Если необходимо внести собственные изменения в настройку принтера, необходимо:

 * Проделать этапы 1-3 из пункта "Установка"
 * Проделать этапы 4-8 из пункта "Установка" - опционально, **если до этого не выполняли!!!**
 * Открыть конфигуратор Repetier Firmware: https://www.repetier.com/firmware/v092/
 * Загрузить настройки принтера: `Start -> Upload old configuration -> Выберите файл` - выбрать файл `config-dupi3.json` из корня папки скаченного репозитория
 * Произвести собственную модификацию, пользуясь конфигуратором
 * Скачать полученные индивидуальные настройки: `Download -> Download config.json`
 * Скачать полученный конфигурационный файл: `Download -> Download Configuration.h`
 * Заменить конфигурационный файл `Configuration.h` на новый (скаченный), в папке `Repetier_929/Repetier` из корня папки скаченного репозитория
 * Проделать этапы 9-13 из пункта "Установка"
 
# Возможные проблемы и их решения
Основная проблема, которая может возникнуть - невозможность прошивки в следствие ошибки: `avrdude: stk500_recv(): programmer is not responding`

 Если есть полная уверенность в работоспособности кабеля USB, то - необходимо обновить Bootloader Melzi: http://reprap.org/wiki/Melzi#Bootloader_Upload
 
 **Инструкция по обновлению Bootloader Melzi**
 
 _Общая подготовительная процедура:_
 
  * Проделать этапы 4-7 из пункта "Установка" - опционально, **если до этого не выполняли!!!**
  
_Подготовка программатора Arduino SPI:_
 
  * Подключить плату Arduino (проверено на платах: UNO, MEGA и NANO) к компьютеру по USB
  * Перейти в запущенный Arduino IDE или открыть
  * Меню - `Файл -> Примеры -> ArduinoISP -> ArduinoISP`
  * В открывшимся окне скетча необходимо выбрать _Плату_ - в зависимости от типа платы Arduino, _Процессор_ - если необходимо и _Порт_
  * Меню - `Файл -> Скетч -> Загрузка`
  * После загрузки скетча - отключить плату Arduino от компьютера
 
_Подготовка к загрузке Bootloader:_
 
  * Выключить принтер
  * Разобрать блок управления принтера
  * Извлечь плату управления Melzi (отвинтить 4 винта)
  * **Важно!!!** Переключить перемычку на USB
 ![alt text](https://github.com/lavstudia/Repetier-Wanhao-i3/blob/master/img/SW_USB.png "USB перемычка")
  * Соединить плату Arduino c платой Melzi по 4-м проводам (ICSP/SPI):
 ![alt text](https://github.com/lavstudia/Repetier-Wanhao-i3/blob/master/img/ICSP.png "ICSP интерфейс")
    - Arduino UNO и NANO:
     
 			pin 1 MISO (Melzi) on pin 12 (Arduino)
 			  
  			pin 3 SCK  (Melzi) on pin 13 (Arduino)
 
  			pin 5 Reset(Melzi) on pin 10 (Arduino)
  				
  			pin 4 MOSI (Melzo) on pin 11 (Arduino)
  				
  	- Arduino MEGA:
  		
 			pin 1 MISO (Melzi) on pin 50 (Arduino)
 				 
  			pin 3 SCK  (Melzi) on pin 52 (Arduino)
  				
  			pin 5 Reset(Melzi) on pin 53 (Arduino)
  				
  			pin 4 MOSI (Melzo) on pin 51 (Arduino)
  				
_Загрузка Bootloader в Melzi:_
 
 * Подключить плату Melzi к компьютеру по USB
 * Подключить плату Arduino к компьютеру по USB
 * Перейти в запущенный Arduino IDE или открыть
 * Меню - `Инструменты ->` :: _Плата_ - Sanguino, _Процессор_ - ATmega1284 or ATmega1284P (16 MHz)
 * Меню - `Инструменты -> Порт` - выбрать порт к которому подключена плата Arduino
 * Меню - `Инструменты -> Программатор -> Arduino as ISP`
 * Меню - `Инструменты -> Записать загрузчик`
 * **Важно!!!** Дождаться завершения процесса
 * Меню - `Инструменты -> Программатор -> USBasp`
 
_Завершение процесса:_
 
 * Отключить плату Arduino от компьютера
 * Отключить плату Melzi от компьютера
 * Отсоединить плату Arduino от платы Melzi
 * **Важно!!!** Переключить перемычку на PWR (плата Melzi)
 ![alt text](https://github.com/lavstudia/Repetier-Wanhao-i3/blob/master/img/SW_PWR.png "PWR перемычка")
 * **_Перед дальнейшей сборкой, желательно проверить загрузку прошивки_**
 * Установить плату Melzi в блок управления принтером (завинтить 4 винта)
 * Собрать блок управления принтером
