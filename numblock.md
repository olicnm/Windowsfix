Num Lock schon vor der Anmeldung aktivieren (Logon-Screen)

    Registry-Editor (regedit.exe) mit Adminrechten starten.
    Zu folgendem Schlüssel wechseln:
    HKEY_USERS\.DEFAULT\Control Panel\Keyboard
    Den Zeichenfolgenwert InitialKeyboardIndicators anpassen.

In vielen Installationen steht dort standardmäßig 2147483648. Wenn Sie Num Lock von Beginn an aktivieren wollen, setzen Sie den Wert auf:

    2147483650 (entspricht „Standardwert + 2“) → Num Lock EIN

Danach Windows neu starten. So lässt sich z. B. bereits die PIN-Eingabe am Login über den Ziffernblock nutzen.
