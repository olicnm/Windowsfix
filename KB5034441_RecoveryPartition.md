

Fehlermeldung Windows Update 0x80070643

Das Update installiert eine aktuelle Version der Windows Recovery Environment. Da der Platz auf der Partition zu klein ist, kommt es zur Fehlermeldung.
manuelle Reparatur in Windows: (viele Befehle lassen sich in Diskpart verkürzt mit den ersten 3 Buchstaben schreiben, so z.B. Statt „delete“ reicht es „del“ zur schreiben oder statt „partition“ nur „par“.)

CMD mit Admin Rechten ausführen und Befehl

    reagentc /info

ausführen. Es zeigt den Win-RE Status an. Wenn der Status auf Enabled steht muss dieser vorher deaktivert werden. Das wird mit dem Befehl

    reagentc /disable

ausgeführt
Im nächsten Schritt die Windows Partition verkleinern, die alte Widerherstellungspartition löschen und neu erstellen.
DISKPART

    diskpart

aufrufen
Festplatten anzeigen:

    list disk

Festplatte mit Windows auswählen

    select disk X

X = Zahl der Windows Partition
Partitionen anzeigen:

    lis par

Windows Partition auswählen:

    sel par X

X = Zahl der Windows Partition
Befehl zum Verkleinern:

    shrink desired=500 minimum=500

Es können auch andere Größen verwendet werden
Recovery Partition auswählen:

    sel par X

 X = Zahl der WinRE Partition
 (alte) Recovery Partition löschen:

     del par override

Neue Recovery Partition erstellen
für GPT Partitionen:

    create par primary id=de94bba4-06d1-4d40-a16a-bfd50179d6ac

zusätzlich für GPT Partitionen Befehl für die Attribute:

    gpt attributes=0x8000000000000001

für MBR Partitionen:

    create partition primary id=27

für alle, Partition formatieren:

    format quick fs=ntfs label=”WinRE”
    assign letter=r

Anschließend noch mal (für MBR)

    SET ID=27 override

Diskpart beenden:

    exit

Aktivieren der neuen WinRE Partition:

    reagentc /enable

WinRE Image

Fehlt die WinRE auf dem System, kann als erstes danach gesucht werden

    dir /a /s c:\winre.wim

Oft liegt noch eine winre.wim Datei in einem Verzeichnis. Bei mir war es C:\$WinREAgent\Backup.
Dateiattribute anpassen:

    attrib -h -s C:\$WinREAgent\Backupwinre.wim

Datei kopieren:

    xcopy /h C:\$WinREAgent\Backup\winre.wim C:\Windows\System32\Recovery

Dem System mitteilen, wo sich das Image der Wiederherstellungsumgebung befindet:

    reagentc /setreimage /path C:\Windows\System32\Recovery
    reagentc /setreimage /path R:\Recovery\WindowsRE (wenn das Laufwerk zuvor in Diskpart einen Laufwerksbuchstaben bekommen hat)

Wiederherstellungsumgebung aktivieren:

    reagentc /enable
---
Copy install.wim to C:\Images\

Mount install.wim file with the required edition say 6 for professional to C:\Mount\ folder

commands

    Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /index:6 /MountDir:"C:\mount" /Optimize /Checkintegrity

    attrib -h -r -s C:\Mount\Windows\System32\Recovery\*.* /s /d

    copy winre.wim file to desktop from this location C:\Mount\Windows\System32\Recovery\

    Dism.exe /UnMount-Image /MountDir:C:\mount /Commit
    
    Reagentc.exe /Disable /target C:\windows

    Md R:\Recovery\WindowsRE

    attrib -h -r -s R:\*.* /s /d

    attrib -h -r -s R:\Recovery\WindowsRE\*.* /s /d

    Copy winre.wim file to R:\Recovery\WindowsRE\

    Reagentc.exe /SetReImage /path R:\Recovery\WindowsRE /Target C:\Windows

    Reagentc.exe /enable

    Reagentc.exe /enable /target C:\windows

    Reagentc.exe /info /target C:\windows



---
How to Fix: Windows 11 weißt der Recovery Partition wiederholt einen Laufwerkbsuchstaben zu
- in der Kommandozeile die Wiederherstellungsinformationen deaktiveren

        reagentc /disable
      
- Die Recovery Partition in Diskpart auswählen
- die Partitions ID zu einer Basispartition umwandeln und GPT Atribute entfernen

        set id="ebd0a0a2-b9e5-4433-87c0-68b6b72699c7"
        gpt attributes=0x0000000000000000

- Laufwerksbuchstaben entfernen

      remove letter=X
- die Partitions ID wieder zur Wiederhrestellungspartition umwandeln und GPT Atribute hinzufügen

        set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
        gpt attributes=0x8000000000000001
- Wiederherstellungsumgebung aktivieren:

      reagentc /enable



Link (https://www.der-windows-papst.de/2024/01/10/windows-wiederherstellungspartition-loeschen-vergroessern-und-wiederherstellen/)

Link 2: (https://support.microsoft.com/de-de/topic/kb5028997-anweisungen-zum-manuellen-%C3%A4ndern-der-partitionsgr%C3%B6%C3%9Fe-zum-installieren-des-winre-updates-400faa27-9343-461c-ada9-24c8229763bf)

