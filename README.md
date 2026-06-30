# Ritterlager Manager

PHP 8.3 / MySQL-Webapp zur Verwaltung eines Ritterlagers beziehungsweise Zeltlagers. Die Anwendung bündelt Lagerjahre, Orden/Zelte, Personen, Mitarbeiter, Programm, Essen, Dienste, Punkte, Rangsystem, Importe, Backups und Betriebsfunktionen in einer webbasierten Oberfläche.

Aktueller Paketstand in dieser Unterhaltung: **v0.14.11**.

## Ziel der Anwendung

Der Ritterlager Manager ersetzt mehrere Excel-, Word- und Papierlisten durch eine zentrale Webapp. Er ist für die praktische Lagerorganisation gedacht: Lagerleitung, Bereichsleitungen und Mitarbeiter sollen auf dem Smartphone oder Desktop schnell sehen, was heute ansteht, welche Dienste offen sind, welche Teilnehmer zu welchem Orden/Zelt gehören und welche Punkte oder Bewertungen erfasst werden müssen.

Die App ist bewusst keine allgemeine Vereinsverwaltung. Sie ist auf ein jährliches Lager mit festen Lagerjahren, Teilnehmern, Mitarbeitern, Orden/Zelten, Programmpunkten, Speiseplan, Diensten und einem eigenen Rang-/Punktesystem zugeschnitten.

## Wichtige Fachbegriffe

**Lagerjahr**  
Ein Lagerjahr bildet eine konkrete Lagerdurchführung ab, zum Beispiel 2025 oder 2026. Viele Daten hängen am Lagerjahr: Teilnehmerstatus, Orden/Zelte, Programm, Essen, Dienste, Punkte und Auswertungen.

**Aktives Lagerjahr**  
Die meisten Ansichten beziehen sich automatisch auf das aktive Lagerjahr. Alte Lagerjahre bleiben für Historie, Import und Rangentwicklung erhalten.

**Orden/Zelt**  
Orden und Zelt sind in dieser App fachlich dasselbe Objekt. Beispiele sind Johanniter, Falkner, Samariter, Petrusker, Morgensternritter und Malteser. Ein Orden/Zelt kann Farbe, Kurzname, Teilnehmer und Mitarbeiterzuordnungen haben.

**Person**  
Eine Person kann Teilnehmer, Mitarbeiter oder beides sein. Personen enthalten Stammdaten wie Name, Geburtstag, Beiname, Kontaktdaten, Notfallkontakte, Hinweise, Allergien und Lagerstatus.

**Lagerstatus**  
Der Lagerstatus beschreibt die Rolle einer Person in einem bestimmten Lagerjahr: aktiv, Teilnehmer, Mitarbeiter, Orden/Zelt-Zuordnung, aktueller Rang, Folgerang und weitere lagerjahrbezogene Informationen.

**Rangsystem**  
Die App kennt Ritterlager-Ränge wie Knappe, Ritter, Freiherr, Graf, Markgraf, Landgraf, Fürst, Herzog und Großherzog. Ein erreichter Rang soll nicht durch spätere leere oder niedrigere Excel-Werte zurückgestuft werden.

## Hauptfunktionen im Überblick

- Login per Personenauswahl und PIN.
- Rollen- und Rechteverwaltung für Admin, Lagerleitung, Bereichsleitung, Mitarbeiter und Lesen.
- Mobile-first Oberfläche mit Sidebar auf Desktop und Bottom-Navigation auf Mobilgeräten.
- PWA-Grundstruktur mit Manifest, Service Worker und Offline-Hinweis.
- Verwaltung mehrerer Lagerjahre mit aktivem Lagerjahr.
- Verwaltung von Orden/Zelten inklusive individueller Farben.
- Personenverwaltung mit Teilnehmerdaten, Mitarbeiterstatus, Geburtsdaten, Beinamen, Notfallkontakten und sensiblen Hinweisen.
- Programmplanung mit Tagesansicht, Kategorien, Orten, Verantwortlichen und wiederkehrenden Programmpunkten.
- Speiseplan mit Mahlzeiten, Zutaten, Allergie-/Ernährungshinweisen und Küchenteam.
- Dienste mit Diensttypen, Dienstzuordnungen und Dienstrotationen.
- Punkteerfassung für Ordnung, Spiele, Zeltbewertung, Geschirr und Dienste.
- Rang-, Prüfungs- und Lerneinheiten-Grundlage.
- Import vorhandener Lagerdaten aus bereitgestellten Excel-/ODS-/DOCX-Dateien.
- Backup-, WebDAV-, Cron- und Log-Grundfunktionen.
- Öffentliche Setup- und Migrationshelfer für Plesk/Shared Hosting, die nach Nutzung wieder gelöscht werden müssen.

## Seiten und Funktionen

### Login

Die App besitzt keinen klassischen E-Mail-Login. Benutzer melden sich über eine Personenauswahl und eine 4- bis 6-stellige PIN an. Das ist für den Lagerbetrieb auf Smartphones schneller und einfacher als ein normaler Benutzername/Passwort-Login.

Funktionen:

- Auswahl eines Benutzers aus der Benutzerliste.
- PIN-Prüfung mit gehashten PINs.
- Session-Rotation beim Login.
- Schutz gegen wiederholte Fehlversuche.
- Rollenbasierte Weiterleitung in die App.

### App-Shell und Navigation

Die Oberfläche ist für Desktop und Mobilgeräte optimiert. Auf großen Bildschirmen wird eine Sidebar verwendet, auf mobilen Geräten eine Bottom-Navigation.

Typische Hauptbereiche:

- Übersicht
- Programm
- Essen
- Dienste
- Ordnung/Punkte
- Personen
- Auswertungen/Ränge
- Importe
- System

Die Navigation richtet sich nach den Rechten des angemeldeten Benutzers. Ein normaler Mitarbeiter sieht weniger Funktionen als Admin oder Lagerleitung.

### Übersicht / Dashboard

Die Übersicht ist der operative Startpunkt für den Lagertag. Sie zeigt die wichtigsten Informationen zum aktiven Lagerjahr komprimiert an.

Funktionen:

- Kennzahlen zum aktiven Lagerjahr.
- Aktive Orden/Zelte mit Farbe und Teilnehmerzahlen.
- Heutige beziehungsweise nächste Programmpunkte.
- Essen des Tages.
- Offene oder aktuelle Dienste.
- Hinweise auf Geburtstage im Lagerzeitraum.
- Schneller Einstieg in Tagesmodule.

Ziel: Die Lagerleitung soll morgens sofort sehen, was ansteht, ohne mehrere Listen öffnen zu müssen.

### Lagerjahre

Lagerjahre bilden die zeitliche Klammer der App. Jedes Lagerjahr hat Start- und Enddatum. Viele Module filtern automatisch auf diesen Zeitraum.

Funktionen:

- Lagerjahr anlegen und verwalten.
- Aktives Lagerjahr setzen.
- Zeitraum des Lagers definieren.
- Standardorden für neue Lagerjahre vorbereiten.
- Tagesmodule auf den Lagerzeitraum begrenzen.

Wichtig: Programm, Essen, Dienste und Punkte sollen nicht versehentlich außerhalb des Lagerzeitraums erfasst werden.

### Orden / Zelte

Orden und Zelte werden als eine fachliche Einheit behandelt. Diese Einheiten strukturieren Teilnehmer, Dienste, Punkte und Auswertungen.

Funktionen:

- Orden/Zelt anlegen, bearbeiten und aktivieren/deaktivieren.
- Namen, Kurzzeichen und Farben pflegen.
- Farbe in Dashboard, Personenlisten, Punkten und Auswertungen verwenden.
- Mitarbeiter oder Verantwortliche einem Orden/Zelt zuordnen.
- Standardorden automatisch für neue Lagerjahre anlegen.

Standardorden:

- Johanniter
- Falkner
- Samariter
- Petrusker
- Morgensternritter
- Malteser

### Personen & Lagerstatus

Die Personenverwaltung ist der zentrale Datenbereich für Teilnehmer und Mitarbeiter. Personen sind lagerjahrübergreifend. Der Lagerstatus beschreibt, welche Rolle die Person in einem bestimmten Jahr hat.

Funktionen:

- Personen suchen und filtern.
- Stammdaten verwalten: Name, Anzeigename, Geburtstag, Beiname, Adresse, Telefon, E-Mail.
- Lagerstatus verwalten: aktiv, Teilnehmer, Mitarbeiter, Orden/Zelt, Rang, Folgerang.
- Alter zum Lagerstart berechnen.
- Geburtstage im Lagerzeitraum erkennen.
- Notfallkontakte und Sorgeberechtigte erfassen.
- Essenshinweise, Allergien, medizinische Hinweise und interne Bemerkungen pflegen.
- Sensible Informationen nur mit passendem Recht anzeigen.
- Personen aus Importen wiedererkennen und Dubletten vermeiden.

Besondere Logik:

- Personen können gleichzeitig in der Stammliste stehen und zusätzlich Benutzer/Mitarbeiter sein.
- Der aktuelle Rang wird aus dem höchsten bekannten beziehungsweise letzten plausiblen Rang abgeleitet, wenn das aktive Lagerjahr fehlerhaft oder leer ist.
- Ein höher erreichter Rang soll nicht durch einen niedrigeren späteren Wert verdeckt werden.

### Programm

Das Programmmodul verwaltet den Tagesablauf des Lagers. Programmpunkte können global oder einzelnen Orden/Zelten zugeordnet sein.

Funktionen:

- Programmpunkte pro Tag erfassen.
- Uhrzeit, Titel, Beschreibung, Ort und Kategorie pflegen.
- Verantwortliche Mitarbeiter hinterlegen.
- Programmpunkte einzelnen Orden/Zelten zuordnen.
- Wiederkehrende Programmpunkte markieren.
- Timeline pro Lagertag anzeigen.
- Nächsten Programmpunkt auf der Übersicht darstellen.
- Import aus dem Word-Programm 2026.

Beispiele für Kategorien:

- Morgenprogramm
- Essen/Pause
- Ausbildung/Lerneinheit
- Spiel
- Freizeit
- Abendprogramm
- Dienst/Organisation

### Essen / Speiseplan

Das Essensmodul bildet den Speiseplan des Lagers ab. Es unterstützt Frühstück, Mittagessen, Abendessen und weitere Mahlzeiten.

Funktionen:

- Mahlzeiten pro Lagertag erfassen.
- Mahlzeittyp, Uhrzeit, Beschreibung und Portionen verwalten.
- Zutaten und Hinweise pflegen.
- Vegetarische oder allergierelevante Hinweise erfassen.
- Küchenteam oder Zuständigkeit dokumentieren.
- Tagesessen auf der Übersicht anzeigen.
- Import aus dem vorhandenen Speiseplan.

Ziel: Küche und Lagerleitung sollen schnell sehen, was wann geplant ist und welche Hinweise relevant sind.

### Dienste

Das Dienstmodul verwaltet Aufgaben und Verantwortlichkeiten im Lageralltag.

Typische Dienstarten:

- Küchendienst
- Spüldienst
- Platzdienst
- Nachtwache
- Lagerfeuerdienst
- Materialdienst
- Kiosk
- Feuerwart
- Flaggenwart
- Zeltwart
- Sanitätsdienst
- Lagerwart

Funktionen:

- Diensttypen verwalten.
- Dienste pro Tag und Zeitbereich erfassen.
- Personen oder Orden/Zelte zuordnen.
- Dienstrotationen vorbereiten.
- Offene Dienste anzeigen.
- Von Diensten direkt in passende Punktebewertungen wechseln.
- Import aus Aufgabenverteilung und Programm.

Besondere Logik:

- Platzdienst und Nachtwache können aus Programmdaten entstehen.
- Die Aufgabenverteilung 2026 erzeugt Diensttypen und organisatorische Grundlage, aber nicht blind falsche Tagesdienste.

### Ordnung / Punkte

Das Punktesystem bildet die Lagerwertung ab. Es unterscheidet persönliche Punkte und Punkte für Orden/Zelte.

Funktionen:

- Punkte erfassen.
- Punkte stornieren statt hart löschen.
- Kategorien und Zielobjekte unterscheiden.
- Punkte pro Person oder pro Orden/Zelt buchen.
- Tages- und Gesamtauswertungen vorbereiten.

Punktearten:

- Ordnung Zelt: global pro Orden/Zelt.
- Ordnung persönlich: persönliche Punkte.
- Sauberkeit Geschirr: persönliche Punkte.
- Prüfung: persönliche Punkte.
- Spiele: global pro Orden/Zelt.
- Platzdienst: global pro Orden/Zelt.
- Küchendienst: global pro Orden/Zelt.
- Bonus Freizeit: persönlich, begrenzt pro Mitarbeiter, Teilnehmer, Tag und Freizeit-Slot.

### Punkte: Spielwertung

Die Spielwertung ist für Wettbewerbe zwischen Orden/Zelten gedacht.

Funktionen:

- Platzierungen erfassen.
- Mehrere Orden/Zelte je Platz erlauben.
- Punkte je Platz vergeben, zum Beispiel 1. Platz = 5 Punkte, 2. Platz = 4 Punkte.
- Spielpunkte als globale Ordens-/Zeltwertung speichern.

### Punkte: Zeltbewertung

Die Zeltbewertung dient der Ordnung oder Sauberkeit eines Zelts beziehungsweise Ordens.

Funktionen:

- Orden/Zelt auswählen.
- Bewertung mit voreingestelltem Wert erfassen.
- Plus/Minus-Anpassungen vornehmen.
- Punkte für den Orden/das Zelt speichern.

### Punkte: Geschirrbewertung

Die Geschirrbewertung wird personenbezogen innerhalb eines Ordens/Zelts erfasst.

Funktionen:

- Orden/Zelt auswählen.
- Kinder/Teilnehmer dieses Ordens anzeigen.
- Voreinstellung pro Kind, zum Beispiel 5 Punkte.
- Plus/Minus-Anpassung pro Kind.
- Persönliche Punkte speichern.

### Punkte: Dienstpunkte

Dienstpunkte werden für Zusatzdienste oder besondere Dienstleistungen vergeben.

Funktionen:

- Dienstart auswählen.
- Orden/Zelt oder beteiligte Personen bewerten.
- Voreinstellung, zum Beispiel 3 Punkte.
- Plus/Minus-Anpassungen erfassen.

### Ränge, Lerneinheiten und Prüfungen

Die App bereitet ein Rangsystem mit Punkteschwellen, Lerneinheiten und Prüfungsergebnissen vor.

Ränge:

- Knappe
- Ritter
- Freiherr
- Graf
- Markgraf
- Landgraf
- Fürst
- Herzog
- Großherzog

Beispielhafte Rangwechsel-Logik:

- Knappe zu Ritter ab 310 Punkten.
- Ritter zu Freiherr ab 320 Punkten.
- Freiherr zu Graf ab 330 Punkten.
- Graf zu Markgraf ab 340 Punkten.
- Markgraf zu Landgraf ab 345 Punkten.
- Landgraf zu Fürst ab 350 Punkten.
- Fürst zu Herzog ab 280 Punkten.
- Großherzog ist eine Ernennung und keine normale Punkteschwelle.

Wichtige Regel:

Ein erreichter Rang soll im Folgejahr nicht verloren gehen oder zurückgestuft werden. Das gilt besonders für hohe Ränge wie Herzog und Großherzog.

Lerneinheiten sind vorbereitet, zum Beispiel:

- Knappe: Knoten, Natur, Waldläufer.
- Ritter: Wappen, Waffen, Feuer.
- Freiherr: Küche, Lageraufbau, Erste Hilfe.

### Auswertungen

Die Auswertungen dienen dazu, Punktestände, Personen, Orden/Zelte und Ränge zusammenzuführen.

Funktionen:

- Punkteübersichten vorbereiten.
- Rangentwicklung sichtbar machen.
- CSV-Export-Grundlage.
- Personen- und Ordens-/Zeltwertungen auswerten.
- Grundlage für spätere Lagerabschluss-Auswertungen.

### Importe

Die App enthält Importfunktionen, um bestehende Lagerdaten aus alten Dateien zu übernehmen.

Unterstützte Importquellen aus dem Projektkontext:

- Zeltlager Manager 2025 als Excel-Datei.
- Speiseplan 2026 als ODS-Datei.
- Ritterlagerprogramm 2026 als DOCX-Datei.
- Aufgabenverteilung 2026 als DOCX-Datei.

Funktionen:

- Importlauf starten.
- Importfehler protokollieren.
- Quellzeilen und Fehler nachvollziehbar speichern.
- Standardorden anlegen.
- Dummy-Lagerjahr aus 2025 erzeugen.
- Programm 2026 importieren.
- Speiseplan 2026 importieren.
- Dienste und Aufgabenverteilung vorbereiten.

Besondere Importlogik:

- Namen werden normalisiert, um Dubletten zu vermeiden.
- Vertauschte Namensreihenfolgen können bei vorhandenem Geburtsdatum erkannt werden.
- Geburtsdaten werden plausibilisiert.
- Leere oder fehlerhafte Excel-Datumswerte werden nicht als echte Geburtstage übernommen.
- Ranghistorien werden über mehrere Jahre gelesen.
- Der letzte beziehungsweise höchste plausible bekannte Rang wird übernommen.
- Niedrigere spätere Werte dürfen höhere erreichte Ränge nicht überschreiben.

### Backup

Das Backup-Modul ist für den Betrieb auf Shared Hosting/Plesk vorbereitet.

Funktionen:

- Backup-Läufe protokollieren.
- Lokale Ablage unter `storage/backups`.
- SQL-Dump und Dateisicherung vorbereiten.
- Integration in geplante Aufgaben/Cron vorbereiten.
- WebDAV-Sync nach Backup optional anstoßen.

Wichtig: Backups gehören nicht ins Git-Repository.

### WebDAV

WebDAV dient zur externen Ablage beziehungsweise Synchronisation von Backups.

Funktionen:

- WebDAV aktivieren/deaktivieren.
- URL, Benutzername, Passwort und Zielordner konfigurieren.
- Verbindung testen.
- Letztes Backup manuell senden.
- Automatischen Sync nach Backup aktivieren.
- Sync-Läufe protokollieren.

WebDAV-Zugangsdaten gehören nicht in Git.

### Geplante Aufgaben / Cron

Die App bereitet geschützte geplante Aufgaben vor. Das ist wichtig für Shared Hosting, bei dem echte CLI-Crons nicht immer bequem nutzbar sind.

Funktionen:

- Aufgabenliste mit Status.
- Empfohlenes Intervall.
- Letzte Ausführung, Dauer, Rückgabecode, Ausgabe und Fehler.
- Token-geschützte HTTP-Cron-URLs.
- Locking gegen parallele Ausführung.
- Manuelles Testen einzelner Aufgaben.

### System / Einstellungen

Der Systembereich bündelt administrative Funktionen.

Funktionen:

- Grundeinstellungen.
- Lagerjahr-Konfiguration.
- WebDAV-Konfiguration.
- Backup-Verwaltung.
- Importverwaltung.
- Rollen- und Rechtebasis.
- Audit-/Log-Grundlage.
- Setup- und Migrationshilfen.

### Setup und Migration

Für einfache Erstinstallation auf Plesk/Shared Hosting gibt es temporäre öffentliche Helferdateien.

Typische Dateien:

- `public/setup.php`
- `public/migration.php`

Diese Dateien dürfen nur temporär auf dem Server liegen und müssen nach der Nutzung gelöscht werden. Sie sind deshalb in `.gitignore` ausgeschlossen.

Migrationen liegen unter:

```text
database/migrations/
```

Nach einem Deploy müssen offene Migrationen ausgeführt werden.

## Rollen und Rechte

Die App verwendet Rollen und Rechte, damit nicht jeder Benutzer alle Bereiche sieht oder ändern kann.

Typische Rollen:

- Admin
- Lagerleitung
- Bereichsleitung
- Mitarbeiter
- Lesen

Typische Rechte:

- Dashboard ansehen.
- Programm ansehen oder verwalten.
- Essen ansehen oder verwalten.
- Dienste ansehen oder verwalten.
- Personen ansehen oder verwalten.
- Sensible Personendaten ansehen.
- Ordnungspunkte erfassen.
- Punkte verwalten.
- Prüfungen ansehen oder verwalten.
- Importe verwalten.
- Backups verwalten.
- WebDAV verwalten.
- Audit/Logs ansehen.
- Einstellungen verwalten.

Normale Mitarbeiter sollen zunächst vor allem schnelle operative Funktionen nutzen, zum Beispiel Ordnungspunkte oder Dienstbewertungen erfassen. Admin und Lagerleitung sehen die vollständige Verwaltung.

## Technischer Aufbau

Technologie:

- PHP 8.3
- MySQL/MariaDB
- PDO
- UTF-8
- HTML/CSS/JavaScript ohne großes Framework
- PWA-Grundlage mit Manifest und Service Worker
- Mobile-first Design

Projektstruktur:

```text
app/          PHP-Anwendungscode, Controller, Services, Views, Support
config/       Konfiguration, ohne produktive database.php im Repository
database/     Migrationen und Datenbankgrundlagen
docs/         Projektdokumentation und Release-Notizen
public/       Einziger öffentlicher Webroot
routes/       Webrouten
scripts/      Wartungs- und CLI-Skripte
storage/      Laufzeitdaten, Backups, Logs, Uploads, Imports
```

Der Ordner `public/` ist der einzige Webroot. Alle anderen Ordner dürfen nicht direkt öffentlich erreichbar sein.

## Sicherheit und Betriebsregeln

Wichtige Regeln:

- `public/` ist der einzige Document Root.
- `config/database.php` wird nicht in Git gespeichert.
- `storage/` enthält produktive Daten und bleibt außerhalb von Git.
- `setup.php` und `migration.php` werden nach Nutzung gelöscht.
- Uploads, Logs, Backups und Importquellen werden nicht veröffentlicht.
- CSRF-Schutz ist zentral vorgesehen.
- Sessions werden beim Login rotiert.
- PINs werden gehasht gespeichert.
- Fehler werden geloggt, aber nicht unnötig öffentlich ausgegeben.

## Repository-Regeln

Dieses Repository soll nur Quellcode und technische Dokumentation enthalten. Produktive Daten und Secrets bleiben außerhalb von Git:

- `config/database.php`
- `storage/logs/`
- `storage/backups/`
- `storage/uploads/`
- `storage/imports/`
- `storage/documents/`
- `storage/import_sources/`
- `storage/setup.lock`
- `public/setup.php`
- `public/migration.php`

## Serverstruktur

Der Projektordner liegt vollständig im Hosting-Verzeichnis. Der öffentliche Document Root muss auf `public/` zeigen.

```text
httpdocs/
  app/
  config/
  database/
  docs/
  public/
  routes/
  scripts/
  storage/
```

Der Domain-Document-Root muss sein:

```text
httpdocs/public
```

Nicht korrekt wäre:

```text
httpdocs
```

und ebenfalls nicht korrekt wäre ein Upload nur in:

```text
httpdocs/public
```

## Deployment

Nach Code-Updates müssen offene Migrationen ausgeführt werden:

```bash
php scripts/maintenance/migrate.php
```

Alternativ temporär per Browser:

```text
https://app.ritterlager.com/migration.php
```

Danach `public/migration.php` wieder löschen.

## Git-Deployment auf Plesk

Empfohlen ist ein Deployment in den kompletten Projektordner, nicht direkt in `public/`.

Deployment-Ziel:

```text
/var/www/vhosts/.../app.ritterlager.com/httpdocs
```

Document Root:

```text
/var/www/vhosts/.../app.ritterlager.com/httpdocs/public
```

Nach dem Git-Deploy müssen produktive Dateien auf dem Server bestehen bleiben, insbesondere:

```text
config/database.php
storage/
```

Diese dürfen nicht durch Git überschrieben oder gelöscht werden.

## Lokale Entwicklung

Für lokale Entwicklung wird eine lokale Datenbankkonfiguration benötigt. Da `config/database.php` nicht im Repository liegt, muss diese Datei lokal selbst angelegt werden.

Empfohlen:

```text
config/database.php
```

mit lokalen Zugangsdaten. Diese Datei bleibt durch `.gitignore` privat.

## Aktueller Stand und bekannte Grenzen

Der Stand v0.14.11 enthält viele operative Grundfunktionen und mehrere Korrekturen rund um Import, Ränge, Dubletten, Geburtstage und Personensuche.

Bekannte fachliche Grenze:

Wenn eine Person in keiner importierten Datei einen korrekten Rang, Geburtstag oder Lagerstatus hat, kann die App diese Information nicht erraten. Solche Fälle müssen manuell gepflegt werden.

Bekannte technische Grenze:

Die App ist auf den beschriebenen Projektkontext zugeschnitten. Sie ist keine generische Vereins-, Schul- oder Eventverwaltungssoftware. Erweiterungen sollten immer anhand der bestehenden Fachlogik für Lagerjahre, Orden/Zelte, Personen, Dienste und Punkte erfolgen.
