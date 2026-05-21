Unsere Standardprogramme 
- winget install -e --id Mozilla.Thunderbird.de
- winget install -e --id Mozilla.Firefox.de
- winget install -e --id Adobe.Acrobat.Reader.64-bit
- winget install -e --id TheDocumentFoundation.LibreOffice
- winget install -e --id Google.Chrome

Weniger wichtige Programme
- winget install -e --id AngusJohnson.PDFTKBuilder
- winget install -e --id SoftMaker.Office.NX
- winget install -e --id 7zip.7zip
- winget install -e --id Notepad++.Notepad++
- winget install -e --id Microsoft.VisualStudioCode
- winget install -e --id Microsoft.PowerToys
- winget install -e --id GIMP.GIMP.3

Prüfen welche Pakte aktualisiert werden können
- winget update

Einzelen Programme aktualisieren. Nimm die ID nicht den Namen des Programm (2. Spalte bei winget -update)
- winget update <Paketname> z.B. winget update notepad++.notepad++ aktualisiert nur das Programm mit der ID notepad++.notepad++

Alle Pakete aktualisieren 
- winget upgrade --all

Paket deinstallieren (hier Thunderbird)
- winget uninstall --id Mozilla.Thunderbird.de

Wenn es Probleme mit den Zertifikaten vom Microsoft Store gibt, diese Befehle ausführen. Die Überprüfung der Zertifikate wird übersprungen, AppInstallier wird installiert, Überprüfung der Zertifikate wird wirder aktiviert
- WINGET SETTINGS --ENABLE BypassCertificatePinningForMicrosoftStore
- WINGET UPGRADE Microsoft.AppInstaller --accept-source-agreements --accept-package-agreements
- WINGET PIN ADD --ID myapp.id
- WINGET SETTINGS --DISABLE BypassCertificatePinningForMicrosoftStore
- WINGET UPGRADE --all --include-unknown --accept-source-agreements --accept-package-agreements
- oder die Quelle winget auswählen ohne Microsoft Store:  Some poeple have success using --source winget

App auf eine Version festlegen. Mit winget pin add verhindern Sie, dass bestimmte Anwendungen durch winget upgrade --all` aktualisiert werden, was besonders für festgelegte Versionen nützlich ist. Der Befehl fixiert die App-Version, erlaubt aber weiterhin manuelle Updates
- WINGET PIN ADD --ID myapp.id
