Ursache war die Software im ISDN Wandler: Die hat einen Fehler.

Man gehe wie folgt vor:

1. Speedport ISDN Wandler an das LAN Kabel anschließen.
2. über das Verzeichnis im Router die IP des ISDN Wandlers im LAN rausfinden.
3. Den Zugriff auf den ISDN Wandler via LAN erlauben:
  A. Schritt 1: RESET TASTE und KONFIGURATIONS - TASTE mindestens 10 Sekunden drücken
  B. Schritt 2: erst RESET TASTE und dann KONFIGURATIONS - TASTE lösen.
4. Zugriff mit dem Web - Browser auf die IP nach Punkt 2, also etwa http://192.168.0.3
5. es erscheint ein Status - Fenster , 8 - stelliges Passwort eingeben (Rückseite Speedport ISDN Wandler)
6. man landet bei einem firmware - update auf der Seite http://192.168.0.3/hidden/upgrade_firm_browse.stm
7. man ändert die Adreßleiste auf http://192.168.0.3/voip_index.stm
8. man klickt auf VOIP oben links
9. unter VoIP account kann man dann die einzelnen Nummern editieren.
10. Es gibt irgendwo ein Feld, wo man die Ortsvorwahl einträgt - das muß man tun
11. hier geht es wenn ich BEI JEDER Rufnummmer
  A. bei "authID" statt anonymous@t-online.de die Adresse reinschreibe mit der ich mich im Telekom - Kundencenter anmelde
  B. bei "Password" das Passwort eintrage mit dem ich mich im Telekom Kundencenter anmelde
  C. bei "use Outbound Proxy" den Haken setze
  D. bei Outbound Proxy" tel.t-online.de eintragen


Viel Erfolg Euch. Keine Gewähr für die Richtigkeit der Angaben.

https://administrator.de/forum/voip-nach-isdn-speedport-isdn-adapter-bzw-wandler-sendet-stets-falsche-erste-msn-des-anschlusses-firmware-581610.html#comment-1468203
https://www.ip-phone-forum.de/threads/isdn-endger%C3%A4te-an-7590-ax-ohne-s0.314936/
