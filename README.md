# Ritterlager Manager

PHP 8.3 / MySQL Webapp zur Verwaltung des Ritterlagers.

Aktueller Paketstand in dieser Unterhaltung: v0.14.11.

## Wichtig

Dieses Repository soll nur Quellcode enthalten. Produktive Daten und Secrets bleiben außerhalb von Git:

- `config/database.php`
- `storage/logs/`
- `storage/backups/`
- `storage/uploads/`
- `storage/imports/`
- `storage/documents/`
- `storage/import_sources/`
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
