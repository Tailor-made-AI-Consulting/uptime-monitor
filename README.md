# uptime-monitor

Externe Verfügbarkeitsprüfung.

Der Workflow `Uptime` prüft alle 10 Minuten, ob die überwachten Endpunkte mit HTTP 200 antworten. Antwortet ein Endpunkt nach drei Versuchen nicht, schlägt der Lauf fehl und GitHub verschickt eine Benachrichtigung.

## Einrichtung

- Repository-Secret `HOSTS`: die geprüften Hostnamen, durch Leerzeichen oder Zeilenumbrüche getrennt. Im Log erscheinen sie nur als Nummer, in der Reihenfolge des Secrets.
- Benachrichtigungen zu geplanten Läufen gehen an die Person, die die Cron-Zeile in `uptime.yml` zuletzt geändert hat.

## Keepalive

GitHub schaltet geplante Workflows in öffentlichen Repositories nach 60 Tagen ohne Aktivität ab. Der Workflow `Keepalive` schreibt deshalb einmal im Monat einen Zeitstempel in `.github/keepalive`.
