# README — setup_LAMP.yml und index.php.j2

Kurzbeschreibung
- Dieses Verzeichnis enthält ein Ansible-Playbook `setup_LAMP.yml`, das einen einfachen LAMP-Stack (Linux, Apache, MySQL/MariaDB, PHP) auf Zielhosts installiert und konfiguriert.
- Die Datei `index.php.j2` ist eine Jinja2-Template für die Standard-Website (`/var/www/html/index.php`) und wird vom Playbook mit Host-spezifischen Variablen gerendert.

Voraussetzungen
- Ansible
- Zielhosts mit SSH-Zugriff und sudo-Rechten
- Inventory-Datei (`inventory`), evtl. Group/Host-Variablen

Inhalt
- setup_LAMP.yml — Haupt-Playbook
    - Installiert Apache (httpd/apache2), PHP (inkl. benötigter Module) und MySQL/MariaDB-Server.
    - Legt Root Passwort, Application User und Berechtigungen an.
    - Deployt das gerenderte `index.php` aus `index.php.j2`.
    - Startet/aktiviert Dienste (apache2/httpd, mysql/mariadb).
- index.php.j2 — Template
    - Enthält Platzhalter wie {{ mysql_database }}
    - Wird nach /var/www/html/index.php kopiert.

Beispiel: Playbook ausführen
```sh
ansible-playbook -i inventory setup_LAMP.yml
```