# Hintergrund

Dieses Playbook wird von mit verwendet um alle Docker Anwendungen, die ich verwende zu verwalten. Aktuell laufen Docker Container auf einem bei Hetzner gemieteten Server, sowie auf einem mini-PC in meinem lokalen Netzwerk. Alle Container, die öffentlich erreichbar sind, laufen auf dem Hetzner Server. Alles was nur lokal verwendet wird auf dem mini-PC.

# Ansible Librarys

Die Playbooks benötigen einige Ansible Librarys. Diese werden in der requirements.yml gesammelt.
Installiert werden sie mit dem folgenden Befehl:

<code> sh bootstrap </code>

# Docker-Container

- [x] Changedetection
- [x] NGINX (webserver)
- [x] NGINX (webspace)
- [x] Portainer
- [x] Heimdall
- [x] IT-Tools
- [x] Minecraft
- [x] Netdata
- [x] Retrogames Emulator
- [x] Traefik
- [x] littleLink (aboutMe Page)
- [x] Uptime-kuma
- [x] MySQL-Datenbank
- [x] Teamspeak 3 Server

# SSL Zertifikate

aktuell werden alle SSL-Zertifikate per http-Challenge von Traefik generiert.

# Ansible-Vault / Secrets

Secrets können sicher über den Ansible-Vault abgelegt werden.

Die vault Dateien werden im Ordner _host_vars_ mit dem Namenschema: **NAME.vault.yml** abgelegt. In den Vault Dateien werden die verschlüsselten Variablen wie folgt angegeben:

- vault_NAME_DER_VARIABLE: ' '

In den host_vars werden die Variablen dann wie folgt referenziert:

- NAME_DER_VARIABLE: '{{ vault_NAME_DER_VARIABLE }}'

Beispiel:

- erstellen einer vault-datei: `ansible-vault create traefik.vault.yml`
- bearbeiten einer vault-datei: `ansible-vault edit traefik.vault.yml`
- anschauen einer vault-datei: `ansible-vault view traefik.vault.yml`

Um ein Playbook auszuführen, dass auf den Vault zugreift muss `--ask-vault-pass` an den `ansible-playbook` Befehl angehängt werden.
