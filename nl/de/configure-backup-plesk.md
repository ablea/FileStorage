---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-24"

---
{:new_window: target="_blank"}
{:pre: .pre}
 
# {{site.data.keyword.filestorage_short}} für Sicherung mit Plesk konfigurieren

In diesem Artikel werden Anweisungen zum Konfigurieren von {{site.data.keyword.blockstoragefull}} für Ihre Sicherungen in Plesk bereitgestellt. Dabei wird angenommen, dass root- oder sudo SSH- sowie ein vollständiger Plesk-Zugriff auf Administratorebene verfügbar ist. Das vorliegende Beispiel basiert auf einem CentOS 7-Host.

**Hinweis**: Die Dokumentation von Plesk zur Sicherung und Wiederherstellung finden Sie [hier](https://docs.plesk.com/en-US/12.5/administrator-guide/backing-up-and-restoration.59256/){:new_window}.

1. Stellen Sie über SSH eine Verbindung zum Host her.

2. Stellen Sie sicher, dass ein Mountpunktziel vorhanden ist.<br />
   **Anmerkunge**: Plesk bietet zwei Optionen zum Speichern von Sicherungen. Die eine ist der interne Plesk-Speicher, ein Sicherungsspeicher auf Ihrem Plesk-Server. Die andere ist ein externer FTP-Speicher – ein Sicherungsspeicher auf einem externen Server im Web oder in Ihrem lokalen Netz. In der Regel werden interne Sicherungen in Plesk-Fenstern im Pfad `/var/lib/psa/dumps` gespeichert und verwenden `/tmp` als temporäres Verzeichnis. Im vorliegenden Beispiel wird das temporäre Verzeichnis lokal beibehalten, das Speicherauszugsverzeichnis jedoch auf das STaaS-Ziel (`/backup/psa/dumps`) verschoben. Es sind keine FTP-Benutzerberechtigungsnachweise erforderlich.
   
3. Konfigurieren Sie Ihre {{site.data.keyword.filestorage_short}}-Instanz. Eine Beschreibung hierzu finden Sie in [Zugriff auf {{site.data.keyword.filestorage_short}} unter Red Hat Enterprise Linux](accessing-file-storage-linux.html) und [Mount für NFS/{{site.data.keyword.filestorage_short}} in CentOS](mounting-nsf-file-storage.html). Hängen Sie den Datenträger an `/backup` an und konfigurieren Sie ihn in der Dateisystemtabelle `/etc/fstab`, um den Mount während des Bootvorgangs zu ermöglichen. <br />
   **Anmerkung**: Standardmäßig stuft NFS alle Dateien, die mit Rootberechtigung erstellt wurden, auf den Benutzer 'nobody' herab. Damit Root-Clients die Rootberechtigung für die gemeinsam genutzte NFS-Ressource behalten können, muss `no_root_squash` zu `/etc/exports` hinzugefügt werden. <br />
   **Anmerkung**: Anweisungen zum [Mount für NFS/{{site.data.keyword.filestorage_short}} unter CoreOS](mounting-storage-coreos.html) stehen ebenfalls zur Verfügung. <br />

4. **Optional**: Kopieren Sie die vorhandenen Sicherungen in den neuen Speicher. Verwenden Sie `rsync`. Beispiel:
   ```
   rsync -avz /var/lib/psa/dumps /backup/psa/dumps
   ```
   {:pre}
    
    **Anmerkung**: Dieser Befehl überträgt Ihre Daten in komprimierter Form, wobei möglichst viel beibehalten wird (außer festen Verbindungen). Außerdem werden Informationen zu den zu übertragenden Dateien sowie am Ende eine kurze Zusammenfassung bereitgestellt.
    
5. Bearbeiten Sie `/etc/psa/psa.conf` so, dass der Wert für `DUMP_D` auf das neue Ziel verweist. 
    - Es sollte wie folgt aussehen: `DUMP_D /backup/psa/dumps`. 

6. **Optional**: Entfernen Sie je nach Ihrem konkreten Anwendungsfall und Ihren Geschäftsanforderungen den alten Speicher vom Server und löschen Sie ihn im Konto.

