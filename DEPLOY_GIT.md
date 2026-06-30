# Git-Deployment für Ritterlager Manager

## Zielstruktur auf Plesk/Netcup

Das Repository wird in den Projektordner deployed, nicht direkt in `public/`.

```text
/var/www/vhosts/.../app.ritterlager.com/httpdocs/
  app/
  config/
  database/
  docs/
  public/
  routes/
  scripts/
  storage/
```

Der Document Root der Domain bleibt:

```text
httpdocs/public
```

## Nicht aus Git deployen

Diese Dateien und Ordner gehören nicht ins Repository:

```text
config/database.php
storage/logs/
storage/backups/
storage/uploads/
storage/imports/
storage/documents/
storage/import_sources/
storage/setup.lock
public/setup.php
public/migration.php
```

## Erstpush vom lokalen Rechner

1. Das GitHub-Ready-ZIP lokal entpacken.
2. Im entpackten Ordner ausführen:

```bash
git init
git add .
git commit -m "Initial Ritterlager Manager v0.14.11"
git branch -M main
git remote add origin https://github.com/matzeisda/rttr.git
git push -u origin main
```

Falls schon Dateien im Repository liegen:

```bash
git pull origin main --allow-unrelated-histories
git add .
git commit -m "Import Ritterlager Manager v0.14.11"
git push
```

## Nach jedem Deploy

Migrationen ausführen:

```bash
php scripts/maintenance/migrate.php
```

Oder temporär per Browser:

```text
https://app.ritterlager.com/migration.php
```

Danach `public/migration.php` wieder löschen.
