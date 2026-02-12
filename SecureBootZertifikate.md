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

---------------------------------------------

Methode 2: 
Installieren des PowerShell-Moduls

    Install-Module -Name UEFIv2
    
Geben Sie Y (für "Ja") auf Fragen zur Installation des NuGet-Anbieters und zur Installation von PSGallery

    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    Import-Module -Name UEFIv2

Überprüfen der aktiven DB:

    (Get-UEFISecureBootCerts db).signature 

Überprüfen Sie die Standarddatenbank:

    (Get-UEFISecureBootCerts dbdefault).signature 

---------------------------------------

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
 
https://www.dell.com/support/kbdoc/de-de/000385747/anleitung-zum-%C3%BCberpr%C3%BCfen-von-secure-boot-zertifikaten#:~:text=Betroffene%20Betriebssysteme:&text=Die%20Secure%20Boot%2DZertifikate%20k%C3%B6nnen,ausf%C3%BChren%2C%20um%20Zugriffsprobleme%20zu%20vermeiden.&text=Hinweis:%20Die%20Active%20DB%20ist,um%20den%20Computer%20zu%20starten.
