# Задача №1 Сборка собственного ядра для CenOS 7

## 1. Информачия о системе.

```
   sudo -i
   cat /etc/*rel*
   uname -r
```   

## 2. Подготовка системы. Установка необходимых пакетов для компиляции ядра.

#### Загружаем необходимые пакеты.
```
   yum groupinstall "Development Tools"
   yum install ncurses-devel
   yum install hmaccalc zlib-devel binutils-devel elfutils-libelf-devel
```
#### Переходим в директорию для сборки и загружаем исходники ядра.
```
   cd /usr/src/kernels
```   
#### Переходим на [www.kernel.org](https://www.kernel.org) нажимаем правой клавишей на *Latest Stable Kernel* и копируем адрес ссылки

#### Загружаем исходники ядра
```
   wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.0.10.tar.xz
```
#### Распаковываем архив с помощью утилиты tar:
```
   tar xf linux*
```  
## 3. Сборка ядра

#### Копируем файл текущей конфигурации ядра
```
   cp -v /boot/config-3.10.0-693.el7.x86_64 .config
```
#### Запускаем меню настроек ядра
```
   make menuconfig
```
Эта команда запустит текстовый конфигуратор настроек. При необходимости можно внести изменения.
Параметры могут иметь следующие значения:

[ * ] - опция включена жёстко

[M] - опция включена модульно

[ ] - опция отключена

Вы можете воспользоваться поиском по параметрам ядра, для этого нажмите "/" (слеш) и введите искомое. Также не забывайте о справке: остановитесь на параметре, подробное описание которого вам хотелось бы видеть, и выбирайте "Help" внизу экрана.
