Sysmon auf PC installiert, hinterlässt nach deinstallation einen verstecketen Ordner, der sich nicht löschen lässt. Grund: Ordnerberechtigung nur für Dienst SYSTEM
hier habe ich eine Lösung gefunden: https://learn.microsoft.com/en-us/answers/questions/4170373/how-do-i-delete-a-hidden-sysmon-folder
CMD als Admin starten und zum Pfad der PsExec gehen und über PsExec die Kommandozeile CMD mit dem Dienst SYSTEM starten:
<code>C:\Software\PSTolls\psexec.exe -sid c:\windows\System32\cmd.exe</code>
in der neuen Konsole <code>rd /s /q c:\sysmon</code> eingeben

Link: https://www.winhelponline.com/blog/run-program-as-system-localsystem-account-windows/#psexec
