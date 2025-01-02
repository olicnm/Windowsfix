Ab Windows 10 muss man folgenden Befehl verwenden
wmic shadowcopy call create Volume="C:\"
statt
vssadmin create shadow /for=C:
In Windows 10 kann man keine Scahttenkopie mehr damit erstellen. Der Befehl create fehlt


Links: [[https://www.windowspro.de/andreas-kroschel/schattenkopien-mit-vssadmin-verwalten]]

Links: [[https://agix.com.au/create-list-and-delete-windows-shadow-copy-vss-on-windows-10/]]
