Anleitung zum Überprüfen von Secure Boot-Zertifikaten 

Betroffene Betriebssysteme:

   - Windows 11
   - Windows 10

Überprüfen Sie die aktive DB:
Dies sind die Zertifikate, die das Betriebssystem verwendet, um den Computer sicher zu starten.
Dieses Beispiel zeigt, dass das Windows UEFI CA 2023-Zertifikat (CA) nicht in der aktiven Datenbank vorhanden ist:


    ([System.Text.Encoding]::ASCII.GetString((Get-SecureBootUEFI db).bytes) -match 'Windows UEFI CA 2023')


Überprüfen Sie die Standarddatenbank:

    ([System.Text.Encoding]::ASCII.GetString((Get-SecureBootUEFI dbdefault).bytes) -match 'Windows UEFI CA 2023')

Dieses Beispiel zeigt, dass das Windows UEFI CA 2023-Zertifikat (CA) in der Standarddatenbank vorhanden ist:
