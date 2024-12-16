Im (alten) Outlook den Schalter "Testen Sie das neue Outlook" ausblenden

Registry Editor öffnen und zu dem Pfad gehen:
<ode>HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Options\General</code>
- neuen DWORD-Wert (32-Bit) hinzufügen
- Name: HideNewOutlookToggle
- Wert: 1

Download der Reg Datei: https://github.com/olicnm/Windowsfix/blob/main/HideNewOutlookToggle.zip



Quelle: https://itv4.de/outlook-365-button-testen-sie-das-neue-outlook-ausblenden-so-gehts/


**__Zwangsupdate von Microsoft deaktivieren__**

Den ganzen Text im Codeblock in eine Textdatei kopieren und als datei.reg abspeichern

```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Policies\Microsoft\office]

[HKEY_CURRENT_USER\Software\Policies\Microsoft\office\16.0]

[HKEY_CURRENT_USER\Software\Policies\Microsoft\office\16.0\outlook]

[HKEY_CURRENT_USER\Software\Policies\Microsoft\office\16.0\outlook\options]

[HKEY_CURRENT_USER\Software\Policies\Microsoft\office\16.0\outlook\options\general]
"DoNewOutlookAutomigration"=dword:00000000
"NewOutlookAutomigrationUserSettingPolicy"=dword:00000002

[HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Outlook\Preferences]
"NewOutlookMigrationUserSetting"=dword:00000000

[HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Outlook\Preferences]
"UseNewOutlook"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Options\General]
"HideNewOutlookToggle"=dword:00000001
```
