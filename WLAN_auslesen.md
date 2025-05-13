- Powershell starten
- Befehl: "netsh wlan show profile" ausführen
- Es werden die gespeichertern WLANs angezeigt
- Befehl: "netsh wlan show profile „DEIN_WLAN_NAME“ key=clear" ausführen.
- Einstellungen und Passwort für das WLAN werden angezeigt

====================
WLAN Daten exportieren
- Powershell starten
- Befehl: "netsh wlan export profile key=clear folder=.\wlanprofiles" ausführen. Der Ordner muss schon angelegt worden sein!
- Es wird eine XML DAtei im Ordner abgelegt

WLAN Daten an neuen PC importieren
- Die XML auf den neuen PC kopieren
- Powershell startem
- Befehl: "netsh wlan add profile filename="<Name-XML-Datei>" user=current"


