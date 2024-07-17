NVME nachträglich aktivieren

Hat man von SATA nach NVME geklont, kann es sein, dass das System auf dern neuen NVME nicht hochfährt. Es kommt ein Bluescreen mit Inacessible Boot Device. Dann ist der storenvme im Windows System nicht aktiviert. Um das zu beheben folgendes durchführen:

- Vom Windows 10/11 Stick booten
- Kommandzeile öffnen (Shift + F10 drücken)
- in der Kommandozeile eingeben:

 <code>regedit</code>

- Im Registrierungs-Editor auf HKEY_LOCAL_MACHINE klicken
- Dann auf Datei und Struktur laden auswählen
- Suche das Windows Verzeichnis der Windows Installation. Gehe in folgendes Verzeichnis: X:\Windows\System32\config und wähle die SYSTEM Datei aus. (X: ist ein belieber Laufwerksbuchstabe)
- Wähle einen Namen für die geöffnete Struktur ein (ich nehme immer 111)
- Im Registrierungs-Editor gehe in folgenden Pfad Computer\HKEY_LOCAL_MACHINE\111\ControlSet001\Services\storenvme (Wenn du als Namen 111 eingegeben hast)
- den Wert bei START auf 0 stellen
- Falls vorhanden den Unterordner Override löschen
- fertig, nun noch die Struktur wieder entfernen. Zum entfernen auf den eigenen Namen (111) klicken, dass dieser markiert ist. Dann auf Datei und Struktur entfernen auswählen. Es können alle Fenster geschlossen werden und das System neu gestartet werden. Stick entfernen. Es sollte jetzt Windows hochfahren.

