---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-11"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Erweiterbare Dateifreigabekapazität

Mit diesem neuen Feature können aktuelle Benutzer von {{site.data.keyword.filestorage_full}} die Größe ihres {{site.data.keyword.filestorage_short}}-Speichers in GB-Inkrementen sofort auf bis zu 12 TB erweitern, ohne ein Duplikat erstellen oder Daten manuell auf größere Datenträger migrieren zu müssen. Während die Größe geändert wird, tritt kein Ausfall auf und der Zugriff ist weiterhin möglich. 

Die Abrechnung für den Datenträger wird automatisch aktualisiert, um die anteilmäßige Differenz des neuen Preises in den laufenden Rechnungsstellungszyklus einzuarbeiten. Anschließend wird der neue Betrag vollständig im nächsten Rechnungsstellungszyklus in Rechnung gestellt.

Diese Funktion ist nur in [ausgewählten Rechenzentren](new-ibm-block-and-file-storage-location-and-features.html) verfügbar. 

## Welchen Nutzen haben erweiterbare Dateifreigaben?

- **Kostenmanagement** – möglicherweise wissen Sie, dass der Umfang Ihrer Daten potenziell anwächst, zu Anfang benötigen Sie jedoch nur eine kleine Speichermenge. Durch die Möglichkeit zur Erweiterung können Kunden Speicherkosten zu Beginn sparen und anschließend größere Speichermengen nutzen, um ihre Anforderungen zu erfüllen.  

- **Wachsender Speicherbedarf** - Kunden, die ein rasches Wachstum des Datenvolumens zu verzeichnen haben, benötigen eine Möglichkeit, die Größe ihres Speichers schnell und problemlos erhöhen zu können, um diesem Wachstum Rechnung zu tragen.

## Wie wirkt sich die Größenänderung des Speichers auf die Replikation aus?

Die Erweiterungsaktion für den primären Speicher hat automatisch eine Größenänderung des Replikats zur Folge.

## Sind irgendwelche Einschränkungen zu beachten?

Dieses Feature ist nur für Speicher verfügbar, der in [Rechenzentren](new-ibm-block-and-file-storage-location-and-features.html) mit erweiterter Funktionalität bereitgestellt wird. Verschlüsselter Speicher, der in diesen Rechenzentren bereitgestellt wird, kann auf bis zu 12 TB vergrößert werden. 

Die bestehenden Größenbegrenzungen für {{site.data.keyword.filestorage_short}}-Speicher, der mit Endurance bereitgestellt wird, gelten weiterhin (d. h. bis zu 4 TB für die 10-IOPS-Stufe und bis zu 12 TB für alle anderen Stufen).

## Wie lässt sich feststellen, ob der bereitgestellte Speicher erweiterbar ist?

Für Speicher, der mit erweiterter Funktionalität bereitgestellt wird, werden ruhende Daten immer verschlüsselt. Sie können leicht feststellen, dass Ihr Speicher dazu gehört, wenn neben ihm das Sperrsymbol in der Portalbenutzerschnittstelle angezeigt wird. 

## Wie lässt sich die Größe des Speichers ändern?

1. Klicken Sie im {{site.data.keyword.slportal}} auf **Speicher** > **{{site.data.keyword.filestorage_short}}** oder im Katalog von {{site.data.keyword.BluSoftlayer_full}} auf **Infrastruktur** > **Speicher** > **{{site.data.keyword.filestorage_short}}**.
2. Wählen Sie den Datenträger in der Liste aus und klicken Sie auf **Aktionen** > **Datenträger ändern**.
3. Geben Sie die neue Speichergröße in GB ein.
4. Prüfen Sie Ihre Auswahl und die neue Preisgestaltung.
5. Klicken Sie auf das Kontrollkästchen **Ich habe die Rahmenvereinbarung gelesen...** und klicken Sie auf **Bestellung abschicken**.
6. Ihre neue Speicherzuordnung sollte nach wenigen Minuten zur Verfügung stehen.

