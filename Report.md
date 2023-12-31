## Contents ##  
[Part 1. Инструмент ipcalc](#Part1)  
[Part 2. Статическая маршрутизация между двумя машинами](#Part2)  
[Part 3. Утилита iperf3](#Part3)  
[Part 4. Сетевой экран](#Part4)  
[Part 5. Статическая маршрутизация сети](#Part5)  
[Part 6. Динамическая настройка IP с помощью DHCP](#Part6)  
[Part 7. NAT](#Part7)

## Part 1. Инструмент ipcalc ##
<a name="Part1"></a>

**== Задание ==**

**Поднять виртуальную машину (далее -- ws1)**

**1.1. Сети и маски**  

  **Определить и записать в отчёт:**
  
  1) Адрес сети 192.167.38.54/13
  2) Перевод маски 255.255.255.0 в префиксную и двоичную запись, /15 в обычную и двоичную, 11111111.11111111.11111111.11110000 в обычную и
     префиксную
  3) Минимальный и максимальный хост в сети 12.167.38.4 при масках: /8, 11111111.11111111.00000000.00000000, 255.255.254.0 и /4
     
**1.2. localhost**  

Определить и записать в отчёт, можно ли обратиться к приложению, работающему на localhost, со следующими IP: 194.34.23.100, 127.0.0.2,
  127.1.0.1, 128.0.0.1
  
**1.3. Диапазоны и сегменты сетей**  

  Определить и записать в отчёт:
  
  1) какие из перечисленных IP можно использовать в качестве публичного, а какие только в качестве частных: 10.0.0.45, 134.43.0.2,
     192.168.4.2, 172.20.250.4, 172.0.2.1, 192.172.0.1, 172.68.0.2, 172.16.255.255, 10.10.10.10, 192.169.168.1
  2) какие из перечисленных IP адресов шлюза возможны у сети 10.10.0.0/18: 10.0.0.1, 10.10.0.2, 10.10.10.10, 10.10.100.1, 10.10.1.255

**== Выполнение ==**

**1.1. Сети и маски**  
  
  1) Адрес сети 192.167.38.54/13 - 192.167.38.54
  2) Перевод маски 255.255.255.0 в префиксную запись - /24, в двоичную 11111111.11111111.11111111.00000000.  
     /15 в обычной - 255.254.0.0, двоичной - 11111111.11111110.00000000.00000000,
     11111111.11111111.11111111.11110000 в обычной -  255.255.255.240, префиксной - /28.
  3) В сети 12.167.38.4 при маске /8 минимальный хост - 12.0.0.1, максимальный - 12.255.255.254,
     при маске 11111111.11111111.00000000.00000000 минимальный хост - 12.167.38.0, максимальный - 12.167.38.255,
     при маске 255.255.254.0 минимальный хост - 12.167.38.1, максимальный - 12.167.39.254,
     при маске /4 минимальный хост - 12.160.0.1, максимальный - 12.175.255.254.
     
**1.2. localhost**  

Определить и записать в отчёт, можно ли обратиться к приложению, работающему на localhost, со следующими IP: 194.34.23.100, 127.0.0.2,
  127.1.0.1, 128.0.0.1.
  
  194.34.23.100 - Destination Net Unreachable,  
  127.0.0.2 - OK,  
  127.1.0.1 - OK,  
  128.0.0.1 -Destination Net Unreachable.
  
**1.3. Диапазоны и сегменты сетей**  

  Определить и записать в отчёт:
  
  1) Публичные: 134.43.0.2, 172.0.2.1, 172.68.0.2,  192.169.168.1Б 192.172.0.1  
     Частные: 10.0.0.45, 10.10.10.10, 172.20.250.4, 172.16.255.255, 192.168.4.2
       
  3) У сети 10.10.0.0/18 адресом шлюза может быть - 10.10.0.2  
     Адреса 10.0.0.1,  10.10.10.10, 10.10.100.1 не подходят, т.к. не совпадают с первыми 18 битами сети  
     Адрес 10.10.1.255  не подходит, т.к. входит в диапазон широковещательных адресов и обычно не используется в качестве шлюза.

## Part 2. Статическая маршрутизация между двумя машинами ##
<a name="Part2"></a>

**== Задание ==**

**Поднять две виртуальные машины (далее -- ws1 и ws2)**

**С помощью команды ip a посмотреть существующие сетевые интерфейсы**  
* В отчёт поместить скрин с вызовом и выводом использованной команды.
  
**Описать сетевой интерфейс, соответствующий внутренней сети, на обеих машинах и задать следующие адреса и маски: ws1 - 192.168.100.10,
маска /16, ws2 - 172.24.116.8, маска /12**

* В отчёт поместить скрины с содержанием изменённого файла etc/netplan/00-installer-config.yaml для каждой машины.

**Выполнить команду netplan apply для перезапуска сервиса сети**

* В отчёт поместить скрин с вызовом и выводом использованной команды.
  
**2.1. Добавление статического маршрута вручную**

**Добавить статический маршрут от одной машины до другой и обратно при помощи команды вида ip r add**

**Пропинговать соединение между машинами**

* В отчёт поместить скрин с вызовом и выводом использованных команд.

**2.2. Добавление статического маршрута с сохранением**

**Перезапустить машины**

**Добавить статический маршрут от одной машины до другой с помощью файла etc/netplan/00-installer-config.yaml**

* В отчёт поместить скрин с содержанием изменённого файла etc/netplan/00-installer-config.yaml.

**Пропинговать соединение между машинами**

* В отчёт поместить скрин с вызовом и выводом использованной команды.

**== Выполнение ==**

**С помощью команды ip a смотрим существующие сетевые интерфейсы**  
* Сетевые интерфейсы ws1  
![Результат команды ip a на машине ws1](/screenshots/screenshot1.png)  
* Сетевые интерфейсы ws2  
![Результат команды ip a на машине ws1](/screenshots/screenshot2.png)  
  
**Описать сетевой интерфейс, соответствующий внутренней сети, на обеих машинах и задать следующие адреса и маски: ws1 - 192.168.100.10,
маска /16, ws2 - 172.24.116.8, маска /12**

* Содержание изменённых файлов etc/netplan/00-installer-config.yaml для каждой машины.  
![Изменённые файлы netplan](/screenshots/screenshot3.png)

**Выполнить команду netplan apply для перезапуска сервиса сети**

* Вызовы и выводы использованной команды  
![Изменённые файлы netplan](/screenshots/screenshot4.png)

**2.1. Добавление статического маршрута вручную**  
Tool -> preferences -> network -> создаем новую сеть Watermelon  
Settings -> network -> включаем адаптер, выбираем NAT network Watermelon у каждой виртуальной машины

**Добавляем статический маршрут от одной машины до другой и обратно при помощи команды вида ip r add**  
![Результаты команды ip r add](/screenshots/screenshot5.png)

**Пингуем соединение между машинами**  
![Результаты команды ping -c 4](/screenshots/screenshot6.png)

**2.2. Добавление статического маршрута с сохранением**

**Перезапуcкаем машины командой** 
    reboot

**Добавляем статический маршрут от одной машины до другой с помощью файла etc/netplan/00-installer-config.yaml**  
![Содержимое файла etc/netplan/00-installer-config.yaml](/screenshots/screenshot7.png)  
* Выполняем команду `sudo netplan apply` для перезапуска сети 

**Пингуем соединение между машинами**  
![Результаты команды ping на машинах](/screenshots/screenshot8.png)

## Part 3. Утилита iperf3 ##
<a name="Part3"/>

**== Задание ==**

**_В данном задании используются виртуальные машины ws1 и ws2 из [Части 2](#Part2)_**

**3.1. Скорость соединения**

Перевести и записать в отчёт: 8 Mbps в MB/s, 100 MB/s в Kbps, 1 Gbps в Mbps

**3.2. Утилита iperf3**

Измерить скорость соединения между ws1 и ws2

* В отчёт поместить скрины с вызовом и выводом использованных команд.

**== Выполнение ==**

**3.1. Скорость соединения**  
* 8 Mbps = 1 MB/s,  
* 100 MB/s = 800000 Kbps,   
* 1 Gbps = 1000 Mbps 

**3.2. Утилита iperf3**  
* Устанавливаем утилиту iperf3 командой sudo apt install iperf3 на обе машины.  
* На ws1 запускаем iperf3 в режиме сервера: iperf3 -s  
* Теперь к ws1 можно подключаться по порту 5201 клиентам iperf3:  
![Вывод](/screenshots/screenshot9.png)  
* На клиенте (ws2) запускаем iperf3 с указанием IP сервера к которому подключаемся iperf3 -c 192.168.100.10 -R, где  
* -с — адрес сервера с запущенным iperf3 на 5201 порту  
* -R — режим Reverse Mode для тестирования входящей скорости  
* Получаем скорость около 4.84 Gbits/sec  
![Вывод на ws2](/screenshots/screenshot10.png)  
Вывод на ws2  
![Вывод на ws1](/screenshots/screenshot11.png)  
Вывод на ws1

## Part 4. Сетевой экран ##
<a name="Part4"/>

**== Задание 4.1 ==**

**В данном задании используются виртуальные машины ws1 и ws2 из [Части 2](#Part2)**

**4.1. Утилита iptables**

Создать файл /etc/firewall.sh, имитирующий фаерволл, на ws1 и ws2:

    #!/bin/sh
    
    # Удаление всех правил в таблице "filter" (по-умолчанию).
    iptables –F
    iptables -X


**Нужно добавить в файл подряд следующие правила:**

**1) на ws1 применить стратегию когда в начале пишется запрещающее правило, а в конце пишется разрешающее правило (это касается пунктов 4 и 5)**

**2) на ws2 применить стратегию когда в начале пишется разрешающее правило, а в конце пишется запрещающее правило (это касается пунктов 4 и 5)**

**3) открыть на машинах доступ для порта 22 (ssh) и порта 80 (http)**

**4) запретить echo reply (машина не должна "пинговаться”, т.е. должна быть блокировка на OUTPUT)**

**5) разрешить echo reply (машина должна "пинговаться")**

* В отчёт поместить скрины с содержанием файла /etc/firewall для каждой машины.

**Запустить файлы на обеих машинах командами chmod +x /etc/firewall.sh и /etc/firewall.sh**

* В отчёт поместить скрины с запуском обоих файлов.
  
* В отчёте описать разницу между стратегиями, применёнными в первом и втором файлах.

**== Выполнение ==**

![Вывод на ws1](/screenshots/screenshot12.png)  
firewall.sh на ws1  
![Вывод на ws2](/screenshots/screenshot13.png)  
firewall.sh на ws2

* Запустить файлы на обеих машинах командами chmod +x /etc/firewall.sh и /etc/firewall.sh  
![Запуск firewall.sh на обеих машинах](/screenshots/screenshot14.png)  
* Пингуем машины  
![Итоги пинга](/screenshots/screenshot15.png)
* Разница между стратегиями: для того, чтобы одна машинга пинговалась, а вторая нет, не обязательно писать обе строки, так как правила обрабатываются в порядке их написания.

**== Задание 4.2 ==**

**4.2. Утилита nmap**

**Командой ping найти машину, которая не "пингуется", после чего утилитой nmap показать, что хост машины запущен
Проверка: в выводе nmap должно быть сказано: Host is up**

* В отчёт поместить скрины с вызовом и выводом использованных команд ping и nmap.

**Сохранить дампы образов виртуальных машин**

**== Выполнение ==**
* Пингуем с каждой машины себя и вторую машину  
![Итоги пинга](/screenshots/screenshot16.png)  
* Видим что не пингуется ws1(192.168.100.10)  
* Запускаем команду nmap ws1 с ws1, nmap 192.168.100.10 с ws2 и видим Host is up - хост запущен  
![Итоги пинга](/screenshots/screenshot17.png)  
* Делаем в VirtualBox снимок  
 
## Part 5. Статическая маршрутизация сети ##
<a name="Part5"/>

**== Задание 5.0 ==**

**Поднять пять виртуальных машин (3 рабочие станции (ws11, ws21, ws22) и 2 роутера (r1, r2))**

**== Выполнение ==**

* Добавляем каждой виртуальной машине адаптер "Внутренняя сеть" и запускаем  
![Запущенные виртуальные машины](/screenshots/screenshot18.png)  

**== Задание 5.1 ==**

**5.1. Настройка адресов машин**

**Настроить конфигурации машин в etc/netplan/00-installer-config.yaml согласно сети на рисунке.**  
* В отчёт поместить скрины с содержанием файла etc/netplan/00-installer-config.yaml для каждой машины.

**Перезапустить сервис сети. Если ошибок нет, то командой ip -4 a проверить, что адрес машины задан верно. Также пропинговать ws22 с
ws21. Аналогично пропинговать r1 с ws11.**

**== Выполнение ==**
* Содержание файла etc/netplan/00-installer-config.yaml у ws11  
![etc/netplan/00-installer-config.yaml у ws11](/screenshots/screenshot19.png)  
* Содержание файла etc/netplan/00-installer-config.yaml у ws21  
![etc/netplan/00-installer-config.yaml у ws21](/screenshots/screenshot20.png)  
* Содержание файла etc/netplan/00-installer-config.yaml у ws22  
![etc/netplan/00-installer-config.yaml у ws22](/screenshots/screenshot21.png)  
* Содержание файла etc/netplan/00-installer-config.yaml у r1  
![etc/netplan/00-installer-config.yaml у r1](/screenshots/screenshot22.png)  
* Содержание файла etc/netplan/00-installer-config.yaml у r2  
![etc/netplan/00-installer-config.yaml у r2](/screenshots/screenshot23.png)

* Использование команды sudo netplan apply  
![Ввод команды sudo netplan apply](/screenshots/screenshot24.png)  
* Пингуем w22 c ws 21 и r1 с ws11  
![Результат пинга](/screenshots/screenshot25.png)

**== Задание 5.2 ==**

**5.2. Включение переадресации IP-адресов.**

**Для включения переадресации IP, выполните команду на роутерах:**  
    sysctl -w net.ipv4.ip_forward=1 

**При таком подходе переадресация не будет работать после перезагрузки системы.**  
* В отчёт поместить скрин с вызовом и выводом использованной команды.

**Откройте файл /etc/sysctl.conf и добавьте в него следующую строку:**  
    net.ipv4.ip_forward = 1 

**При использовании этого подхода, IP-переадресация включена на постоянной основе.**  
* В отчёт поместить скрин с содержанием изменённого файла /etc/sysctl.conf.

**== Выполнение ==**

* Вводим команду sudo sysctl -w net.ipv4.ip_forward=1 на r1 и r2  
![Ввод и вывод вышеупомянутой команды](/screenshots/screenshot26.png)  
* Для включения IP-переадресации на постоянной основе раскомментируем в файле /etc/sysctl.conf следующую строку: net.ipv4.ip_forward = 1  
![Расскоментированная строка в файле](/screenshots/screenshot27.png)  
* Перезагружаем и выполняем команду sysctl net.ipv4.ip_forward для проверки:
![Проверка работы /etc/sysctl.conf с раскомментированной строкой](/screenshots/screenshot28.png)  
* Параметр ядра net.ipv4.ip_forward равен 1. Это означает, что переадресация включена.

**== Задание 5.3 ==**

**5.3. Установка маршрута по-умолчанию**

**Пример вывода команды ip r после добавления шлюза:**  
    default via 10.10.0.1 dev eth0  
    10.10.0.0/18 dev eth0 proto kernel scope link src 10.10.0.2

**Настроить маршрут по-умолчанию (шлюз) для рабочих станций. Для этого добавить default перед IP роутера в файле конфигураций**  
* В отчёт поместить скрин с содержанием файла etc/netplan/00-installer-config.yaml.

**Вызвать ip r и показать, что добавился маршрут в таблицу маршрутизации**  
* В отчёт поместить скрин с вызовом и выводом использованной команды.

**Пропинговать с ws11 роутер r2 и показать на r2, что пинг доходит. Для этого использовать команду:**  
    tcpdump -tn -i eth1  
* В отчёт поместить скрин с вызовом и выводом использованных команд.

**== Выполнение ==**

* Добавляем маршрут по-умолчанию в файле конфигураций etc/netplan/00-installer-config.yaml у ws11, ws21, ws22.  
![Содержимое файла 00-installer-config.yaml у ws11](/screenshots/screenshot29.png)  
_ws11_  
![Содержимое файла 00-installer-config.yaml у ws21](/screenshots/screenshot30.png)  
_ws21_  
![Содержимое файла 00-installer-config.yaml у ws22](/screenshots/screenshot31.png)  
_ws22_  

* Вызываем ip r и видим, что добавился маршрут в таблицу маршрутизации
![Результат команды на ws11, ws21, ws22](/screenshots/screenshot32.png)  
* Пингуем с ws11 роутер r2:  
![Результат пинга](/screenshots/screenshot33.png)  
_ws11_  
* Показываем на r2, что пинг доходит с помощью команды tcpdump -tn -i eth1  
![Вывод команды tcpdump -tn -i eth1](/screenshots/screenshot34.png)  
_r2_

**== Задание 5.4 ==**

**5.4. Добавление статических маршрутов**

**Добавить в роутеры r1 и r2 статические маршруты в файле конфигураций. Пример для r1 маршрута в сетку 10.20.0.0/26:**  
    # Добавить в конец описания сетевого интерфейса eth1:
    - to: 10.20.0.0
      via: 10.100.0.12  
* В отчёт поместить скрины с содержанием изменённого файла etc/netplan/00-installer-config.yaml для каждого роутера.

**Вызвать ip r и показать таблицы с маршрутами на обоих роутерах. Пример таблицы на r1:**  
    10.100.0.0/16 dev eth1 proto kernel scope link src 10.100.0.11  
    10.20.0.0/26 via 10.100.0.12 dev eth1  
    10.10.0.0/18 dev eth0 proto kernel scope link src 10.10.0.1  
* В отчёт поместить скрин с вызовом и выводом использованной команды.

**Запустить команды на ws11:**  
    ip r list 10.10.0.0/[маска сети] и ip r list 0.0.0.0/0  
* В отчёт поместить скрин с вызовом и выводом использованных команд.  
* В отчёте объяснить, почему для адреса 10.10.0.0/[маска сети] был выбран маршрут, отличный от 0.0.0.0/0, хотя он попадает под маршрут по-умолчанию.

**== Выполнение ==**

* Добавляем в роутеры r1 и r2 статические маршруты в файле конфигураций:  
![Содержимое файла конфигураций на r1](/screenshots/screenshot35.png)  
_r1_  
![Содержимое файла конфигураций на r2](/screenshots/screenshot36.png)  
_r2_

* Вызываем ip r чтобы показать таблицы с маршрутами на обоих роутерах:  
![Маршруты на r1](/screenshots/screenshot37.png)  
_r1_  
![Маршруты на r2](/screenshots/screenshot38.png)  
_r2_


**== Задание 5.5 ==**
  
**5.5. Построение списка маршрутизаторов**

**Пример вывода утилиты traceroute после добавления шлюза:**

    1 10.10.0.1 0 ms 1 ms 0 ms
    2 10.100.0.12 1 ms 0 ms 1 ms
    3 10.20.0.10 12 ms 1 ms 3 ms
    
**Запустить на r1 команду дампа:**

    tcpdump -tnv -i eth0

**При помощи утилиты traceroute построить список маршрутизаторов на пути от ws11 до ws21**

* В отчёт поместить скрины с вызовом и выводом использованных команд (tcpdump и traceroute).

* В отчёте, опираясь на вывод, полученный из дампа на r1, объяснить принцип работы построения пути при помощи traceroute.



**== Выполнение ==**

* Проверяем пинг ws21 c ws11  
![Маршруты на r2](/screenshots/screenshot39.png)  
* Запускаем на r1 команду дампа: tcpdump -tnv -i enp0s8  
![Маршруты на r2](/screenshots/screenshot40.png)  
* При помощи утилиты traceroute строим список маршрутизаторов на пути от ws11 до ws21:  
![Маршруты на r2](/screenshots/screenshot41.png)  
* Команда traceroute linux использует UDP пакеты. Она отправляет пакет с TTL=1 и смотрит адрес ответившего узла, дальше TTL=2,  
TTL=3 и так пока не достигнет цели. Каждый раз отправляется по три пакета и для каждого из них измеряется время прохождения.  
Когда утилита traceroute получает сообщение от целевого узла о том, что порт недоступен трассировка считается завершенной.

**== Задание 5.6 ==**

**5.6. Использование протокола ICMP при маршрутизации**
  
**Запустить на r1 перехват сетевого трафика, проходящего через eth0 с помощью команды:**  
    tcpdump -n -i eth0 icmp

**Пропинговать с ws11 несуществующий IP (например, 10.30.0.111) с помощью команды:**  
    ping -c 1 10.30.0.111

* В отчёт поместить скрин с вызовом и выводом использованных команд.

**Сохранить дампы образов виртуальных машин**

**== Выполнение ==**

* Запускаем на r1 перехват сетевого трафика, проходящего через eth0 с помощью команды: tcpdump -n -i enp0s8 icmp  
![Результат перехвата](/screenshots/screenshot42.png)  
* Пингуем с ws11 несуществующий IP с помощью команды: ping -c 1 10.30.0.111  
![Результат пинга несуществующего IP](/screenshots/screenshot43.png)  

## Part 6. Динамическая настройка IP с помощью DHCP ##
<a name="Part6"/>

**== Задание 6.1 ==**

**Для r2 настроить в файле /etc/dhcp/dhcpd.conf конфигурацию службы DHCP:**

**1) указать адрес маршрутизатора по-умолчанию, DNS-сервер и адрес внутренней сети. Пример файла для r2:**

    subnet 10.100.0.0 netmask 255.255.0.0 {}
    
    subnet 10.20.0.0 netmask 255.255.255.192
    {
        range 10.20.0.2 10.20.0.50;
        option routers 10.20.0.1;
        option domain-name-servers 10.20.0.1;
    }
    
**2) в файле resolv.conf прописать nameserver 8.8.8.8.**  
* В отчёт поместить скрины с содержанием изменённых файлов.

**Перезагрузить службу DHCP командой systemctl restart isc-dhcp-server. Машину ws21 перезагрузить при помощи reboot и через 
ip a показать, что она получила адрес. Также пропинговать ws22 с ws21.**  
* В отчёт поместить скрины с вызовом и выводом использованных команд.

**== Выполнение ==**

* Устанавливаем isc-dhcp-server командой sudo apt install isc-dhcp-server  
* Для r2 настраиваем в файле /etc/dhcp/dhcpd.conf конфигурацию службы DHCP: указываем адрес маршрутизатора по-умолчанию,  
DNS-сервер и адрес внутренней сети  
![Содержание файла /etc/dhcp/dhcpd.conf](/screenshots/screenshot44.png)  
_r2_  
* в файле /etc/resolv.conf прописать nameserver 8.8.8.8.  
![Содержание файла /etc/resolv.conf](/screenshots/screenshot45.png)  
_r2_  
* Через ip a показываем, что ws21 получила адрес:  
![Сетевые интерфейсы ws21](/screenshots/screenshot46.png)  
_ws21_  
* Пингуем ws22 с ws21:  
![Результаты пинга](/screenshots/screenshot47.png)  
_ws21

**== Задание 6.2 ==**

**Указать MAC адрес у ws11, для этого в etc/netplan/00-installer-config.yaml надо добавить строки: macaddress: 10:10:10:10:10:BA, 
dhcp4: true**  
* В отчёт поместить скрин с содержанием изменённого файла etc/netplan/00-installer-config.yaml.

**== Выполнение ==**

* Указываем MAC адрес у ws11: в etc/netplan/00-installer-config.yaml добляем строки: macaddress: 10:10:10:10:10:BA, dhcp4: true  
![Содержимое файла 00-installer-config.yaml](/screenshots/screenshot48.png)  
_ws11_

**== Задание 6.3 ==**

**Для r1 настроить аналогично r2, но сделать выдачу адресов с жесткой привязкой к MAC-адресу (ws11). Провести аналогичные тесты**  
* В отчёте этот пункт описать аналогично настройке для r2.

**== Выполнение ==**

* Для r1 настраиваем в файле /etc/dhcp/dhcpd.conf конфигурацию службы DHCP: указываем адрес маршрутизатора по-умолчанию,  
DNS-сервер и адрес внутренней сети:  
![Содержимое файла /etc/dhcp/dhcpd.conf](/screenshots/screenshot49.png)  
_r1 : /etc/dhcp/dhcpd.conf_  
![Содержимое файла /etc/resolv.conf](/screenshots/screenshot50.png)  
_r1 : /etc/resolv.conf_  
* Перезагружаем службу DHCP командой systemctl restart isc-dhcp-server  
![Вывод команды](/screenshots/screenshot51.png)  
_r1_  
* Через ip a показываем, что ws11 получила адрес:  
![Сетевые интерфейсы ws11](/screenshots/screenshot52.png)  
  _ws11_  
* Пингуем ws22 с ws11:  
![Результаты пинга на ws11](/screenshots/screenshot53.png)  
_ws11_

**== Задание 6.4 ==**

**Запросить с ws21 обновление ip адреса**  
* В отчёте поместить скрины ip до и после обновления.  
* В отчёте описать, какими опциями DHCP сервера пользовались в данном пункте.

**Сохранить дампы образов виртуальных машин**

**== Выполнение ==**

* Через ip a показываем текущий адрес ws21:  
![Сетевые интерфейсы ws21](/screenshots/screenshot54.png)  
_ws21_  
* Принудительного освобождаем IP-адрес DHCP-клиента с помощью команды  sudo dhclient -r  
* Получаем новый IP-адрес с помощью DHCP с помощью команды sudo dhclient  
![Получене нового адреса ws21](/screenshots/screenshot55.png)  
* Через ip a показываем что адрес ws21 сменился:  
![Сетевые интерфейсы ws21](/screenshots/screenshot56.png)  
_ws21_  
Я пользовался следующими опциями DHCP сервера пользовались в данном пункте:  
* Настройка конфигурации службы DHCP (адрес маршрутизатора по-умолчанию, DNS-сервер, адрес внутренней сети, привязка к MAC-адресу)  
* Клиент протокола динамической конфигурации хоста (команда dhclient) для обновления или освобождения IP-адреса  

## Part 7. NAT ##
<a name="Part7"/>

**== Задание 7.0 ==**

**В файле /etc/apache2/ports.conf на ws22 и r1 изменить строку Listen 80 на Listen 0.0.0.0:80, то есть сделать сервер Apache2 общедоступным**  
* В отчёт поместить скрин с содержанием изменённого файла.

**Запустить веб-сервер Apache командой service apache2 start на ws22 и r1**  
* В отчёт поместить скрины с вызовом и выводом использованной команды.

**== Выполнение ==**

* Устанавливаем сервер Apache2 командой sudo apt install apache2  
* В файле /etc/apache2/ports.conf на ws22 и r1 изменяем строку Listen 80 на Listen 0.0.0.0:80  
![Файл /etc/apache2/ports.conf на r1](/screenshots/screenshot57.png)  
_r1_  
![Файл /etc/apache2/ports.conf на ws22](/screenshots/screenshot58.png)  
_ws22_  
* Запускаем веб-сервер Apache командой service apache2 start на ws22 и r1  
![Запуск apache2 на r1](/screenshots/screenshot59.png)  
_r1_  
![Запуск apache2 на ws22](/screenshots/screenshot60.png)  
_ws22_

**== Задание 7.1 - 7.3 ==**

**Добавить в фаервол, созданный по аналогии с фаерволом из [Части 4](#Part4), на r2 следующие правила:**  
1\) Удаление правил в таблице filter - iptables -F  
2\) Удаление правил в таблице "NAT" - iptables -F -t nat  
3\) Отбрасывать все маршрутизируемые пакеты - iptables --policy FORWARD DROP

**Запускать файл также, как в [Части 4](#Part4)**  
* Проверить соединение между ws22 и r1 командой ping

**При запуске файла с этими правилами, ws22 не должна "пинговаться" с r1**  
* В отчёт поместить скрины с вызовом и выводом использованной команды.

**== Выполнение ==**

* Создаем на r2 файл /etc/firewall.sh, имитирующий фаервол  
* Добавляем в фаервол следующие правила:  
    iptables -F  
    iptables -F -t nat  
    iptables --policy FORWARD DROP  
![firewall.sh на r2](/screenshots/screenshot61.png)  
_r2_  
* Запускаем файл командами sudo chmod +x /etc/firewall.sh и sudo bash /etc/firewall.sh  
![Вывод команд](/screenshots/screenshot62.png)  
_r2_  
* Проверяем соединение между ws22 и r1 командой ping, ws22 не должна "пинговаться" с r1  
![Проверка соединения](/screenshots/screenshot63.png)  
_r1_  

**== Задание 7.4 ==**

**Добавить в файл ещё одно правило:**  
4) Разрешить маршрутизацию всех пакетов протокола ICMP

**Запускать файл также, как в [Части 4](#Part4)**  
* Проверить соединение между ws22 и r1 командой ping

**При запуске файла с этими правилами, ws22 должна "пинговаться" с r1**  
* В отчёт поместить скрины с вызовом и выводом использованной команды.

**== Выполнение ==**

* Добавляем в фаервол следующие правила:  
    iptables -A INPUT -p icmp --icmp-type 8 -j ACCEPT  
    iptables -A OUTPUT -p icmp --icmp-type 8 -j ACCEPT  
![firewall.sh на r2](/screenshots/screenshot64.png)  
_r2_  
* Запускаем файл командами sudo chmod +x /etc/firewall.sh и sudo bash /etc/firewall.sh  
![Вывод команд](/screenshots/screenshot65.png)  
_r2_  
* Проверяем соединение между ws22 и r1 командой ping, ws22 должна "пинговаться" с r1  
![Проверка соединения](/screenshots/screenshot66.png)  
_r1_  

**== Задание 7.5 - 7.6 ==**

**Добавить в файл ещё два правила:**  
5) Включить SNAT, а именно маскирование всех локальных ip из локальной сети, находящейся за r2 (по обозначениям из Части 5 - сеть 10.20.0.0)  
6) Включить DNAT на 8080 порт машины r2 и добавить к веб-серверу Apache, запущенному на ws22, доступ извне сети

* В отчёт поместить скрин с содержанием изменённого файла.

**Запускать файл также, как в [Части 4](#Part4)**  
**Перед тестированием рекомендуется отключить сетевой интерфейс NAT (его наличие можно проверить командой ip a) в 
VirtualBox, если он включен**

**Проверить соединение по TCP для SNAT, для этого с ws22 подключиться к серверу Apache на r1 командой:**

    telnet [адрес] [порт]

**Проверить соединение по TCP для DNAT, для этого с r1 подключиться к серверу Apache на ws22 командой telnet (обращаться по адресу r2 и порту 8080)**  
* В отчёт поместить скрины с вызовом и выводом использованных команд.

**Сохранить дампы образов виртуальных машин**

**== Выполнение ==**

* Добавляем в фаервол следующие правила:  
![Содержимое файла firewall.sh](/screenshots/screenshot67.png)  
_r2_  
* Отключаем сетевой интерфейс NAT  
* Запускаем файл командами sudo chmod +x /etc/firewall.sh и sudo bash /etc/firewall.sh  
![Результат выполнения команд](/screenshots/screenshot68.png)  
_r2_  
* Проверить соединение по TCP для SNAT, для этого с ws22 подключаемся к серверу Apache на r1 командой: telnet 10.10.0.1 80  
![Проверка соединения SNAT](/screenshots/screenshot69.png)  
_ws22_  
* Проверяем соединение по TCP для DNAT, для этого с r1 подключаемся к серверу Apache на ws22 командой telnet 10.20.0.20 80  
![Проверка соединения DNAT](/screenshots/screenshot70.png)  
_r1_

