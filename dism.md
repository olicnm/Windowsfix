Windows Partitionierung
SYSTEMSICHERUNG MIT DISM

Der Computer wird vom WinPE-Live-System (CD oder USB-Stick) gestartet.

dism /capture-image /capturedir:<Quelle> /imagefile:<Ziel> /name:<Beschreibung>
dism /capture-image /capturedir:D:\ /imagefile:Win10.wim /name:Win10

VORBEREITUNG EINER MBR-FESTPLATTE (BIOS-MODUS)

Die Festplatte (disk 0) wird komplett gelöscht und neu eingerichtet:

    Partition 1 500 MB Systempartition
    Partition 2 Rest - 1GB für die Windows-Startpartition
    Partition 3 Recovery Partition
    Partition 4 weitere Datenpartition(en)

diskpart
DISKPART> list disk
DISKPART> select disk 0
DISKPART> clean
**1. System Partition anlegen**
DISKPART> create partition primary size=500
DISKPART> format fs=ntfs quick label="System"
DISKPART> active
DISKPART> assign letter=s
**2. Windows Partition anlegen**
DISKPART> create partition primary size= Größe - 1GB für Recovery Partition
DISKPART> format fs=ntfs quick label="Windows 10"
DISKPART> assign letter=w
**3. Recovery Partition anlegen**
DISKPART> create partition primary size=1024
DISKPART> format fs=ntfs quick label="Recovery"
DISKPART> set id=27
DISKPART> exit

Hier kann eine TXT heruntergeladen werden, die das erstellen der Laufwerk für einen übernimmt: createpartitions-bios.txt

Die beiden „assign“-Befehle und die zugewiesenen Laufwerksbuchstaben haben nur eine temporäre Bedeutung, damit man sofort nach dem Einrichten (ohne Neustart) auf die Laufwerke zugreifen kann
VORBEREITUNG EINER GPT-FESTPLATTE (UEFI-MODUS)

Die Festplatte (disk 0) wird komplett gelöscht und neu eingerichtet:

    Partition 1 100 MB Systempartition
    Partition 2 16 MB MSR-Partition (Microsoft Reserved)
    Partition 3 Windows-Partition
    Partition 4 Recovery Tools
    Partition 5 Daten Partition(en)

Auf eine Windows-Recovery-Partition kann beim Klonen verzichtet werden.

diskpart
DISKPART> list disk
DISKPART> select disk 0
DISKPART> clean
DISKPART> convert gpt
**1. System Partition anlegen**
DISKPART> create partition efi size=100
DISKPART> format fs=fat32 quick label="System"
DISKPART> assign letter=s
**2. MSR Partition anlegen**
DISKPART> create partition msr size=16
**3. Windows Partition anlegen**
DISKPART> create partition primary (es sollte eine Größe angegeben werden, da noch die Recovery Tools Partition ca. 1 GB benötigt. Ist die Festplatte 1 TB groß, sollte die Größe für Laufwerk C: size=998000 sein)
DISKPART> format fs=ntfs quick label="Windows"
DISKPART> assign letter=w
**4. Recovery Partition anlegen**
DISKPART> create partition primary size=1024
DISKPART> format fs=ntfs quick label="Recovery"
DISKPART> assign letter="r"
DISKPART> set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
DISKPART> gpt attributes=0x8000000000000001
**Wenn benötigt, können weitere Partitionen angelegt werden, oder später in Windows**
DISKPART> exit

INSTALLATION MIT DISM

dism /apply-image /imagefile:<Quelle> /applydir:<Ziel> /Index:1
dism /apply-image /imagefile:z:\win10.wim /applydir:w:\ /Index:1

Hier kann eine TXT heruntergeladen werden, die das erstellen der Laufwerk für einen übernimmt: createpartitions-uefi.txt
BCDBOOT

Die Laufwerksbuchstaben im WinPE-Live-System und im laufenden Windows-System müssen nicht identisch sein. Das nachfolgende Beispiel geht davon aus, dass die Partition in der das Wim-Image installiert wurde, mit dem Laufwerksbuchstaben w: angesprochen wird und die Systempartition bzw. ESP-Partition ggf. mit dem Laufwerksbuchstaben s: angesprochen werden kann. bcdboot w:\windows Das Einrichten des Bootmanagers läuft üblicherweise problemlos ab, wenn WinPE im gleichen Modus (BIOS oder UEFI) gestartet wurde, wie das später zu startende System. Wenn dies nicht der Fall ist, kann man durch Zusatzopitionen den richtigen Bootmanager einrichten.

bcdboot w:\windows /s s: Angabe der Systempartition bzw. ESP-Partition
bcdboot w:\windows /s s: /f UEFI Angabe des Firmware-Typs
bcdboot w:\windows /s s: /f BIOS
bcdboot w:\windows /s s: /f ALL

