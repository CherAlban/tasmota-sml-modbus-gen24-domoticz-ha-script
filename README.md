# tasmota-sml-modbus-gen24-domoticz-ha-script

Das Script emuliert ein Fronius Smart Meter TCP, indem es per SML den Stromzähler des Netzbetreibers ausliest und die drei von meinem Stromzähler auslesbaren Messwerte: aktuelle Leistung, total_WH_exp und total_Wh_Imp per Modbus TCP nach SunSpec Standard zur Verfügung stellt.

![pasted-from-clipboard](https://github.com/user-attachments/assets/5423f0b8-385f-4604-bcb6-16871295c6d1)

Das ganze funktioniert mit angepassten Tasmota Images ab V13.3.0 (inkl. der Optionen USE_TCP_Server und USE_SCRIPT_TASK), wie sie der User Ottello freundlicherweise stets aktuell auf seinem Blog zur Verfügung stellt: https://ottelo.jimdofree.com/s…slesen-tasmota/#Downloads


Die Fronius MODBUS Register Referenz gibt es direkt bei Fronius zum Downlaod: http://www.fronius.com/QR-link/0024
In dem .zip gibt es " Smart_Meter_Register_Map_Float.xlsx", darin sind alle Register beschrieben.

Die Reihenfolge und Gruppierung der Registerabfragen habe ich nur für den Fronius Gen24 ermittelt und im Script emuliert, für andere Wechselrichter die auch den SunSpec Standard nutzen muss man das wahrscheinlich anpassen.

Getestet habe ich mit einem Wechselrichter Fronius Gen24 ab Firmware 1.28.7-1 (aktuell 1.34.6-1)

Alle Credits gehen an gemu2015, er hat Tasmota entsprechend erweitert und mir sehr viel mit dem Script geholfen.

Zusätzlich fragt das Script per seriellem Modbus acht 1-Phasen Wechselstromzähler ab (2x EASTRON SDM120 und 6x Saia ALD1D5F), und stellt swohl die SML-Messwerte als auch die 1-Phasenzähler-Messwerte über MQTT für DOMOTICZ und Home Assistent zur Verfügung.

Die serielle Abfrage der Saia ALD1D5F ist hier beschrieben:
https://www.photovoltaikforum.com/thread/199292-sonoff-shelly-bessere-alternativen-f%C3%BCr-tasmota/?postID=3594224#post3594224

![image](https://github.com/user-attachments/assets/2929b252-0a70-4c63-9da4-44cbdb79cd03)

