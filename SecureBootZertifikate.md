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


Methode 2 
Installieren des PowerShell-Moduls

    Install-Module -Name UEFIv2
    
Geben Sie Y (für "Ja") auf Fragen zur Installation des NuGet-Anbieters und zur Installation von PSGallery

    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    Import-Module -Name UEFIv2

Überprüfen der aktiven DB:

    (Get-UEFISecureBootCerts db).signature 

Überprüfen Sie die Standarddatenbank:

    (Get-UEFISecureBootCerts dbdefault).signature 

alte Secure Boot-Zertifikate:

2011 Zertifikate (CAs) 	                    
- Microsoft Corporation KEK CA 2011 	         
- Microsoft Windows Produktion PCA 2011 	     
- Microsoft Corporation UEFI CA 2011 	         
                                             

neue Zertifikate 2023 (CAs)
- Microsoft Corporation KEK 2K CA 2023
- Windows UEFI CA 2023
- Microsoft UEFI CA 2023
- Microsoft Option ROM UEFI CA 2023
 
