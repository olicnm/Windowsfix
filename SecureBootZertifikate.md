Anleitung zum Überprüfen von Secure Boot-Zertifikaten 

Betroffene Betriebssysteme:

   - Windows 11
   - Windows 10

Überprüfen Sie die aktive DB:

    ([System.Text.Encoding]::ASCII.GetString((Get-SecureBootUEFI db).bytes) -match 'Windows UEFI CA 2023')
