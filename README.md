# Piscord – Releases

Selbst gehostete Plattform für Sprach-, Text- und Bildschirmübertragung. Hier liegen die veröffentlichten Pakete; der Quellcode ist privat.

**Neueste Version:** <https://github.com/PatrickAmann/piscord-releases/releases/latest>

## Client

| System              | Datei                              | Updates                    |
| ------------------- | ---------------------------------- | -------------------------- |
| Windows 10/11       | `Piscord-Setup-X.Y.Z.exe`          | automatisch                |
| Linux (alle)        | `Piscord-X.Y.Z-x86_64.AppImage`    | automatisch                |
| Debian/Ubuntu       | `Piscord-X.Y.Z-linux-amd64.deb`    | Hinweis, neu herunterladen |

Der Windows-Installer ist nicht code-signiert. Beim ersten Start zeigt Windows deshalb „Der Computer wurde durch Windows geschützt“ an (→ _Weitere Informationen → Trotzdem ausführen_).

Zum Beitreten im Client nur die Adresse des Servers eingeben, z. B. `meinserver.example.org`.

## Server

Linux x86_64 mit systemd (Debian 12/13, Ubuntu 22.04+). Docker wird nicht gebraucht.

```bash
wget https://github.com/PatrickAmann/piscord-releases/releases/latest/download/piscord-server-linux-x64.tar.gz
tar -xzf piscord-server-linux-x64.tar.gz
sudo ./piscord-server-*/bin/piscordctl install --base-domain example.org --email admin@example.org
sudo piscordctl create meinserver --title "Mein Server"
```

`create` gibt die Adresse, die freizugebenden Medienports und einen Privilege Key aus. Mit dem Key wird man im Client Admin (Server-Einstellungen → Privilege Key). Weitere Befehle: `piscordctl help`. Updates: `sudo piscordctl update`.

Nötige Ports: 80/tcp und 443/tcp, dazu pro Instanz zwei Medienports (erste Instanz 7881/tcp und 7882/udp, jede weitere +10).

## Signaturen

Die Update-Beschreibungen (`latest*.yml`) und das Server-Archiv sind mit Ed25519 signiert (`*.sig`). Client und `piscordctl update` installieren nur Dateien mit gültiger Signatur.

Öffentlicher Schlüssel (raw, Base64): `KBlNzBhMBkKR35RTbcxZThC1Zd+Ne8JOn6+0+z1no8g=`
