---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}

# {{site.data.keyword.filestorage_short}} unter CoreOS anhängen

CoreOS ist eine leistungsfähige Linux-Distribution, die darauf ausgerichtet ist, die Verwaltung umfangreicher und skalierbarer Bereitstellungen auf verschiedenartiger Infrastruktur zu vereinfachen. Basierend auf einem Build von Chrome OS verwaltet CoreOS ein schlankes Hostsystem und verwendet Docker-Container für alle Anwendungen.

## Portierbaren Speicher anhängen

Alle sekundären Mountdateien werden in das Verzeichnis `/etc/systemd/system` verlegt, da sich die Mounts der Systemebene in einem Verzeichnis befinden, das in CoreOS schreibgeschützt ist. Sie erstellen die Datei `MOUNTPOINT.mount`. Der **Where**-Abschnitt in der Mountdatei (.mount) muss mit dem Dateinamen übereinstimmen. Wenn der Mountpunkt nicht direkt an `/` anschließt, müssen Sie die Datei mithilfe der folgenden Syntax angeben: `pfad-zum-mount.mount`. Im folgenden Beispiel soll das portierbare Speicherlaufwerk an `/mnt/www` angehängt werden, deshalb erhält die Datei den Namen `mnt-www.mount`.

Sie müssen `fdisk` oder `parted` zum Erstellen der Partition verwenden und sicherstellen, dass
das erstellte Dateisystem mit dem in der Datei `.mount` aufgelisteten Dateisystem übereinstimmt, da andernfalls das Starten
des Service fehlschlägt.


```
[Unit]
Description = Mount for Portable Storage

[Mount]
What=/dev/xvdc1
Where=/mnt/www
Type=ext4

[Install]
WantedBy = multi-user.target
```
{:codeblock}


Da CoreOS `systemd` verwendet, müssen Sie die Datei `*.mount` aktivieren, damit der Mountpunkt auch nach einem Neustart noch verfügbar ist.
Wenn Sie das Flag `--now` verwenden, wird die Partition sofort angehängt und auf Starten nach dem Startvorgang (Boot) eingestellt.

```
$ systemctl enable --now mnt-www.mount
```
{:pre}

## NFS/{{site.data.keyword.filestorage_short}} anhängen

Der Prozess zum Anhängen eines {{site.data.keyword.filestorage_short}}-Speichers bleibt im Wesentlichen gleich. Da das Anhängen (Mount) jedoch mit NFS erfolgt, können einige weitere Optionen in der Zeile 'Options=' in der Mountdatei angegeben werden. Im folgenden Beispiel wird für NFS festgelegt, dass das Anhängen an `/data/www` erfolgt. Anmerkung: Der NFS-Mountpunkt der {{site.data.keyword.filestorage_short}}-Instanz kann auf der {{site.data.keyword.filestorage_short}}-Listenseite oder über den API-Aufruf `SoftLayer_Network_Storage::getNetworkMountAddress()` abgerufen werden.

```
$ cat data-www.mount
[Unit]
Description = Mount for Container Storage

[Mount]
What=<NFS-Mountpunkt>
Where=/data/www
Type=nfs
Options=vers=4,sec=sys,noauto

[Install]
WantedBy = multi-user.target
```
{:codeblock}

Jetzt kann die Mountoperation aktiviert und geprüft werden, ob das Anhängen ordnungsgemäß erfolgt.

```
systemctl enable --now /etc/systemd/system/data-www.mount

cluster1 ~ # mount |grep data
<NFS-Mountpunkt> on /data/www type nfs4 (rw,relatime,vers=4.0,rsize=65536,wsize=65536,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.81.x.x,local_lock=none,addr=10.1.x.x)
```
{:codeblock}
 
## NAS/CIFS anhängen

Das Anhängen einer CIFS-Freigabe wird in CoreOS nicht nativ unterstützt, jedoch ist eine einfache Ausweichlösung verfügbar, mit der NAS-Freigaben an das Hostsystem angehängt werden können. Sie können einen Container verwenden, um die Moduldatei `mount.cfis` zu erstellen und sie anschließend auf das CoreOS-System zu kopieren.
 
Führen Sie auf dem CoreOS-System den folgenden Befehl aus, um die Moduldatei herunterzuladen und in einem Fedora-Container abzulegen: 
```
docker run -t -i -v /tmp:/host_tmp fedora /bin/bash
```
{:pre}
 
Führen Sie folgende Befehle aus, sobald Sie sich in dem Container befinden, um das CIFS-Dienstprogramm zu erstellen:
```
dnf groupinstall -y "Development Tools" "Development Libraries"
dnf install -y tar
dnf install -y bzip2
curl https://ftp.samba.org/pub/linux-cifs/cifs-utils/cifs-utils-6.4.tar.bz2 | bunzip2 -c - | tar -xvf -
cd cifs-utils-6.4/
./configure && make
cp mount.cifs /host_tmp/
```
{:codeblock}
 
Nach dem Kopieren der Datei 'mount.cifs' auf den Host können Sie den Docker-Container verlassen, indem Sie den Befehl `exit` eingeben oder die Tastenkombination **STRG+d** drücken. Wenn Sie wieder im CoreOS-System sind, können Sie die CIFS-Freigabe mit dem folgenden Befehl anhängen:  
```
/tmp/mount.cifs //nasXXX.service.softlayer.com/USERNAME -o username=USERNAME,password=PASSWORD /path/to/mount
```
{:pre}
 
## ISCSI anhängen

Dies wird in CoreOS gegenwärtig nicht unterstützt, wird jedoch für ein zukünftiges Release vorbereitet: https://github.com/coreos/bugs/issues/634
