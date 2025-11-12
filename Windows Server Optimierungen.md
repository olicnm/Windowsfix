Hyper-V Server
Im Gerätemanager die Netzwerkkarten auswählen und unter Reiter Erweitert folgendes deaktiveren:
- Large-Send-Offload V2 (IPv4)
- Large-Send-Offload V2 (IPv6)

Der Name des Switches kann mit diesem Befehle ermittelt werden
- Get-VMSwitch

RSC deaktiveren: In der Powershell folgenden Befehl eingeben.
- Set-VMSwitch -Name Name-des-VM-Switches - EnableSoftwareRSC $false

Um es wieder zu aktiveren
- Set-VMSwitch -Name Name-des-VM-Switches - EnableSoftwareRSC $True

Virtuellen Maschinen
Im Gerätemanager die Netzwerkkarten auswählen und unter Reiter Erweitert folgendes deaktiveren:
- Large-Send-Offload V2 (IPv4)
- Large-Send-Offload V2 (IPv6)Recv Segment Coalescing (IPv4)
- Large-Send-Offload V2 (IPv6)Recv Segment Coalescing (IPv6)
