TroLUG 2014-12-04
-----------------

* Aktuelle Mitteilungen
* OpenWRT Teil 1
* 15 Min. Pause, Mate, Dose
* OpenWRT Teil 2
* Dinner

OpenWRT ersetzt Firmware des Herstellers
----------------------------------------

* Produktunabhängige, einheitliche Bedienung

* mehr Funktionen

* leicht erweiterbar

* geräteunabhängige Konfiguration (UCI)

* möglich durch GPL


DSL-Splitter
------------

* Frequenzweiche

* Alterung

* Typen: ADSL2+ (< 25 MBit), VDSL


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
* Fehlerquelle: Zwei konkurrierende DHCP Server
* praktisch: Statisches DHCP: IP zu MAC zuordnen

.. code-block:: bash

    dhclient eth0


Port forwarding
---------------
* per Menü in OpenWRT


Zeitdienst per ntp
------------------
.. code-block:: bash

    uci set system.ntp.server='ptbtime1.ptb.de'
    uci set system.ntp.enable_server=1

SSH-Schlüssel in Router laden
-----------------------------
.. code-block:: bash 
    
    $ sshkeygen

* upload von id_rsa.pub in LUCI

Fehlersuche
-----------
Hardwarestatus der Netzwerkkarte abfragen

.. code-block:: bash
    # alte Methode
    $ mii-tools eth0

    # neue Metode
    $ ethtool eth0


lokale IP / Route
-----------------
.. code-block:: bash

     $ ifconfig
     $ route -n
     $ ip -4 addr 
     $ ip -6 addr

Nachbarschaft
-------------
.. code-block:: bash

     # zeigt benachbarte Netzwerkteilnehmer
     $ ip neigh
     $ ip nei

     # mit Filter für IPv4 / IPv6
     $ ip -4 nei
     $ ip -6 nei


Client IP im Internet
---------------------
.. code-block:: bash

     $ cat ~/.bash_aliases
     [..]
     alias myip='dig +short myip.opendns.com @resolver1.opendns.com'



Konfiguration zurücksetzen
--------------------------
* TP-Link AC-1200 
* Einschalten 
* warten bis grüner Stern langsam blinkt 
* RESET einige Male tippen
* Stern blinkt schnell: Failsafe bootet


Überleben im Failsafe mode
--------------------------
.. code-block:: bash

    $ telnet 192.168.1.1
    # mount_root
    # firstboot
    # uci
    # passwd
    # reboot -f

Paketlaufzeiten Ping
--------------------
.. code-block:: bash

    $ ping meinprovider.de


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


Tipps
-----
* IP 192.168.1.1 für andere Router reservieren, FF-Router, Reparatur anderer Router...
* Kabel bis DSL Modem kurz halten
* Konfiguration des Routers dokumentieren/sichern
* jede Einstellungsänderung dokumentieren
* Verbindungen auf verdächtige Aktivitäten hin überwachen
* SSH nur mit Passwort ist out

Dank
---- 
* Diese Folien wurden mit rst2pdf erstellt

.. code-block:: bash

    $ rst2pdf openwrt.rst -b1 -s slides.style


* Roberto Alsina für http://ralsina.me/stories/BBS52.html
* Johannes Hubertz für Korrekturen 



.. header::

        OpenWRT - Freie Firmware für Router

.. footer::

        2014-12-04 Jonas Stein, TroLUG http://trolug.de/
