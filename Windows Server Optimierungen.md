Hyper-V Server
Im Gerätemanager die Netzwerkkarten auswählen und unter Reiter Erweitert folgendes deaktiveren:
- Large-Send-Offload V2 (IPv4)
- Large-Send-Offload V2 (IPv6)
- Recv Segment Coalescing (IPv4)
- Recv Segment Coalescing (IPv6)
- Enerigeeffizientes Ethernet: Aus (Andere Namen: AdvanvedEEE, Green Ethernet, Energy Efficient Ethernet, Power Saving Mode, reduced Ehternet Speed, WOL Link)
Im Reiter Energieverwaltung deaktivieren
- Computer kann das Gerät ausschalten
Gerätemanager USB Controller Energieverwaltung deaktivieren
- Computer kann das Gerät ausschalten, um Energie zu sparen

Energieoptionen - Erweiterte Energieeinstellungen
- Enegie Sparen: deaktiveren
- Festplatte ausschalten: Nie


Der Name des Switches kann mit diesem Befehle ermittelt werden
- Get-VMSwitch

RSC deaktiveren: In der Powershell folgenden Befehl eingeben.
- Set-VMSwitch -Name Name-des-VM-Switches - EnableSoftwareRSC $false

Um es wieder zu aktiveren
- Set-VMSwitch -Name Name-des-VM-Switches - EnableSoftwareRSC $True



Virtuelle Maschinen
Im Gerätemanager die Netzwerkkarten auswählen und unter Reiter Erweitert folgendes deaktiveren:
- Large-Send-Offload V2 (IPv4)
- Large-Send-Offload V2 (IPv6)
- Recv Segment Coalescing (IPv4)
- Recv Segment Coalescing (IPv6)


Computer / Laptops
Im Gerätemanager die Netzwerkkarten
- Enerigeeffizientes Ethernet: Aus (Andere Namen: AdvanvedEEE, Green Ethernet, Energy Efficient Ethernet, Power Saving Mode, reduced Ehternet Speed, WOL Link)
Im Reiter Energieverwaltung deaktivieren
- Computer kann das Gerät ausschalten
Gerätemanager USB Controller Energieverwaltung deaktivieren
- Computer kann das Gerät ausschalten, um Energie zu sparen

Energieoptionen - Erweiterte Energieeinstellungen
- Enegie Sparen: deaktiveren
- Festplatte ausschalten: Nie
