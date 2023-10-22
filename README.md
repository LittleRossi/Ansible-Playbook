# Ansible Librarys
Die Playbooks benötigen einige Ansible Librarys. Diese werden in der requirements.yml gesammelt.
Installiert werden sie mit dem folgenden Befehl:

<code> sh bootstrap </code>

# Docker-Container
- [X] Portainer 
- [X] Heimdall
- [X] NGINX (webserver)
- [X] NGINX (webspace)
- [X] Changedetection
- [X] littleLink (aboutMe Page)
- [X] Uptime-kuma
- [ ] Guacamole


# SSL Zertifikate

aktuell werden alle SSL-Zertifikate per http-Challenge von Traefik generiert.

# Ansible-Vault / Secrets

Secrets können sicher über den Ansible-Vault abgelegt werden.
In diesem Repo haben aktuell alle Vaults das selbe Passwort "Ansible Vault" in Bitwarden

Beispiel:

- erstellen einer vault-datei: `ansible-vault create traefik.vault.yml`
- bearbeiten einer vault-datei: `ansible-vault edit traefik.vault.yml`
- anschauen einer vault-datei: `ansible-vault view traefik.vault.yml`

Um ein Playbook auszuführen, dass auf den Vault zugreift muss `--ask-vault-pass` an den `ansible-playbook` Befehl angehängt werden.
