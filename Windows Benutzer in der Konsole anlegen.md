

Account anlegen mit:

    net user
    z.B. net user /add cnm (legt den Benutzer cnm an)
    z.B. net user cnm 123 (erstellt das Passwort 123 für den Benutzer cnm)

Berechtigungen festlegen:

    net localgroup (für Standalone-PCs)
    net group (für DCs)

Benutzer in eine Gruppe hinzufügen

    net localgroup groupname username /add
    z.B. net localgroup Administratoren cnm /add

