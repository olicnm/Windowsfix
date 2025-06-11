Powershell


ms-settings:regionlanguage
Get-Command -Module LanguagePackManagement
Install-Language -Language en-US
Install-Language -Language de-DE
Set-SystemPreferredUILanguage -Language en-US
Restart-Computer
