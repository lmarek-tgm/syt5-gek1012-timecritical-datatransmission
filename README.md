# Embedded Devices "Time-critical data-transmission"

## Aufgabenstellung
Die detaillierte [Aufgabenstellung](TASK.md) beschreibt die notwendigen Schritte zur Realisierung.

## Recherche
- Was ist ein SPI-Bus und wie ist dieser aufgebaut?

Ein SPI-Bus (Serial Peripheral Interface) ist ein synchroner, serieller Bus. Es besteht aus drei Leitungen die Datenübertragung zwischen verschiedenen ICs regelt. 

Es gibt folgende Leitungen

- MOSI (**M**aster **O**ut -> **S**lave **I**n) auch SDO (**S**erial **D**ata **O**ut) oder DO
- MISO (**M**aster **I**n <- **S**lave **O**ut) auch SDI (**S**erial **D**ata **I**n) oder DI
- SCK (Serial Clock) - Schiebetakt, hier wird direkt über den Master ausgegeben 

 **SPI** ist ein Bus nach dem Master-Slave-Prinzip, somit werden die Slaves immer vom Master angewählt, auch wird die Datenübertragung von ihm angeführt. Jeder einzelne Slave hat ein meist Low-Aktives Slave Select Signal. Das bedeutet, dass, solange ein Slave noch nicht vom Master gewählt wurde, die Taktsignale sowie Datensignale im TriState Modus verbleiben. Dabei sind sie sehr hochohmig, zur **SPI-Verbindung** selber werden also weder Daten noch Takte durchgelassen. 

[SPI]( https://www.mikrocontroller.net/articles/Serial_Peripheral_Interface )

[SPI2]( https://www.kunbus.de/die-spi-schnittstelle.html  )

- Welche Vorteile ergeben sich bei der Verwendung eines Kommunikationsbusses?



- Welche Möglichkeiten der Beschaltung sind beim SPI-Bus möglich und wie wirkt sich die Clock darauf aus?

 Wie schon angesprochen gibt es für das SPI verschiedene Möglichkeiten Polarität und Phase des Taktes einzustellen. Folgende vier Modi sind möglich: 

| Mode | CPOL | CPHA |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 1    | 0    | 1    |
| 2    | 1    | 0    |
| 3    | 1    | 1    |

- CPOL (Clock Polarity)

  0: Takt ist in Ruhe LOW, ein Wechsel auf HIGH zählt als steigende Taktflanke

  1: Takt ist invertiert: in Ruhe HIGH, ein Wechsel auf LOW zählt als steigende Taktflanke

- CPHA (Clock Phase)

  0: Daten werden bei steigender Taktflanke (=abh. von CPOL) eingelesen, bei fallender ausgegeben

  1: Daten werden bei fallender Taktflanke eingelesen, bei steigender ausgegeben

Man sieht, dass Mode 0 und Mode 3 bzw. Mode 1 und Mode 2 jeweils fast identisch sind. Der einzige Unterschied ist der Pegel des Taktes in Ruhe. In der Regel sind diese Modi deshalb austauschbar.

Es ist problemlos möglich ICs mit verschiedenen SPI-Modi an einem Bus zu betreiben, man muss nur vor dem Aktivieren des Chip Select den jeweils richtigen Modus einstellen.

[Beschaltung]( https://www.mikrocontroller.net/articles/Serial_Peripheral_Interface )

- Wie werden zeitkritische Anwendungen (real-time) eingeteilt?



- Wie kommt ein Watchdog bei zeitkritischen Anwendungen zum Einsatz?



- Wie kann man Interrupts priorisieren?



- Was sind Real-Time Operating-Systems (RTOS) und wie kann man diese auf Mikrokontrollern einsetzen?


## Implementierung

## Quellen

