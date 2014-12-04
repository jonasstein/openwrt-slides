OpenWRT ersetzt Firmware des Herstellers
----------------------------------------

* Produktunabhängige, einheitliche Bedienung

* mehr Funktionen

* leicht erweiterbar

* geräteunabhängige Konfiguration (UCI)

* Möglich durch GPL


DSL-Splitter
------------

* Frequenzweiche

* Alterung


Unterstützte Router
-------------------

* http://wiki.openwrt.org/toh/start

* mindestens 16 MB RAM

* sehr verbreitet: TP-LINK

* DD-WRT 54 GL wird nicht mehr unterstützt


Passende Firmware finden
------------------------
* Hersteller, Bauserie
* Hardwareversion oft auf Geräterückseite


Erste Anmeldung
---------------
.. code-block:: bash 

    telnet 192.168.1.1


Passwort setzen
---------------
.. code-block:: bash

    $ passwd
    Password for root changed by root
    root@(none):/# reboot -f

* Deaktiviert telnet 
* ab jetzt login per ssh


DSL Zugangsdaten
----------------
.. code-block:: bash

    uci set network.wan.proto=pppoe
    uci set network.wan.username='user@example.com'
    uci set network.wan.password='asdf'
    uci commit network
    ifup wan


DHCP-Server
-----------

Port forwarding
---------------


Zeitdienst per ntp
------------------
.. code-block:: bash

    uci set system.ntp.server='ptbtime1.ptb.de'
    uci set system.ntp.enable_server=1



Fehlersuche
-----------
Hardwarestatus der Netzwerkkarte abfragen
.. code-block:: bash

    $ mii-tools eth0


lokale IP
---------
.. code-block:: bash

     $ ifconfig



externe IP
----------
.. code-block:: bash

     $ cat ~/.bash_aliases
     [..]
     alias myip='dig +short myip.opendns.com @resolver1.opendns.com'




Konfiguration zurücksetzen
--------------------------



Paketlaufzeiten Ping
--------------------
.. code-block:: bash

    $ ping example.com


DNS Server
----------
.. code-block:: bash

    $ emerge net-analyzer/namebench-1.3.1-r1


Übertragungsgeschwindigkeit
---------------------------
* suchen nach "dsl speedtest" etc.
* zuverlässiger, aber weniger bunt: Zufallsdatei von eigenem Provider mit wget herunterladen

.. code-block:: bash

    # NetCologne
    $ wget --report-speed=bits http://speedtest.netcologne.de/test_10mb.bin






Dank
---- 
* Diese Folien wurden mit rst2pdf erstellt

.. code-block:: bash

    $ rst2pdf openwrt.rst -b1 -s slides.style


* Roberto Alsina für http://ralsina.me/stories/BBS52.html
 



.. header::

        OpenWRT - Freie Firmware für Router

.. footer::

        2014-12-04 Jonas Stein, TroLUG http://trolug.de/
