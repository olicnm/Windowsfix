

CC und BCC dauerhaft einblenden

Thunderbird: im Benutzerprofil Ordner den Ordner Chrome erstellen und in den ordner die Datei userChrome.css erstellen
Datei öffnen und den code hinzufügen
<code>
@-moz-document url-prefix("chrome://messenger/content/messengercompose/messengercompose.xhtml") {
#addressRowCc.address-row.hidden,
#addressRowBcc.address-row.hidden {
    display: flex !important;
}
}
</code>
Datei speichern
Im Thunderbird Kofig Editor den Wert von:
toolkit.legacyUserProfileCustomizations.stylesheets auf TRUE setzten

Konfig Editor unter Einstellungen - Allgemein - ganz unten auf den Knopf "Konfiguration bearbeiten..."


Links: https://www.thunderbird-mail.de/forum/thread/85012-benutzeroberfl%C3%A4che-per-userchrome-css-anpassen/
Links: https://www.thunderbird-mail.de/lexicon/entry/45-benutzeroberfl%C3%A4che-per-userchrome-css-anpassen/
