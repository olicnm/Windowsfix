Automatische Antwort Outlook mit Powerautomate

- im Outlook Kalender einen Eintrag erstellen (Titel egal) wichtig: eine Kategorie mit dem Namen AutomatischeAntwort erstellen


in PowerAutomate einen "Automatisierter Cloud-Flow" erstellen und den Assistenten über überspringen verlassen
- Auslöser hinzufügen - nach Outlook suchen und den Eintrag "Wenn ein anstehender Termin in Kürze startet (V3)
	- eventuell Powerautomate mit Outlook verbinden. Zugangsdaten eintragen
	- Kalender-ID: passenden Kalender auswählen
	- Lookaheaddauer: 15
	Oben im Reiter Einstellungen bei Auslösebendingen auf hinzufügen klicken
		Folgednes eintragen @contains(triggerOutputs()?['body/categories'], 'AutomatischeAntwort')
		=> hier steht auch die Kategorie, bitte das eintragen, was als Kategorie verwendet wurde
somit ist diese Aktion fertig eingerichtet

- Auf das Plus + Zeichen unterhalb des Auslösers klicken, wieder nach Outlook suchen und "Automatische Antworten einrichten (V2) anwählen
	- Auf den Knopf "Alle anzeigen" auswählen
	- Status: Geplant (erst mit X alles löschen und dann im Dropdwon Menü auswählen)
	- Externe Zielgruppe: alle (erst mit X alles löschen und dann im Dropdwon Menü auswählen)
	- Startzeit DateTime ins Feld klicken und das Blitzsymbol auswählen. Im Kontextmenü "Startzeit" auswählen
	- Endzeit DateTime ins Feld klicken und das Blitzsymbol auswählen. Im Kontextmenü "Endzeit" auswählen
	=> Es werden die Zeiten aus dem Kalender Eintrag verwendet!
	- Interne Antwortnachricht
	- Externe Antwortnachricht
