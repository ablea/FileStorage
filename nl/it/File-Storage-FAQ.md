---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-29"

---
{:new_window: target="_blank"}

# {{site.data.keyword.filestorage_short}} - Domande frequenti (FAQ - Frequently Asked Questions)

## Come faccio a distinguere quali dei miei volumi {{site.data.keyword.filestorage_short}} sono crittografati?
Ricerca nel tuo elenco di {{site.data.keyword.filestorage_short}} nel portale clienti. Puoi vedere un'icona di blocco a destra del nome LUN/volume per i volumi che sono crittografati.

## Se ho acquistato {{site.data.keyword.filestorage_short}} non crittografato in un data center di cui non è stato eseguito l'upgrade per la crittografia, posso crittografare il mio {{site.data.keyword.filestorage_short}}?
{{site.data.keyword.filestorage_short}} di cui era stato eseguito il provisioning prima dell'upgrade a un data center non può essere crittografato. Il nuovo {{site.data.keyword.filestorage_short}} di cui è stato eseguito il provisioning in data center di cui è stato eseguito l'upgrade viene crittografato automaticamente. Non c'è alcuna impostazione di crittografia da cui scegliere, l'operazione è automatica. I dati su un'archiviazione non crittografata possono essere crittografati creando un nuovo volume e copiando quindi i dati nel nuovo volume crittografato con la migrazione basata sull'host. Per ulteriori informazioni, vedi [Migrazione dell'archiviazione file](/docs/infrastructure/FileStorage/migrate-file-storage-encrypted-file-storage.html).

## Come faccio a sapere se sto eseguendo il provisioning di {{site.data.keyword.filestorage_short}} in un data center di cui è stato eseguito l'upgrade?
Nel modulo di ordine {{site.data.keyword.filestorage_short}}, tutti i data center di cui è stato eseguito l'upgrade sono segnalati da un asterisco (`*`). Durante il processo di ordine, stai dando un'indicazione che stai eseguendo il provisioning con la crittografia. Una volta eseguito il provisioning dell'archiviazione, puoi vedere un'icona nell'elenco archiviazioni che mostra il volume come crittografato.  

Il provisioning di tutte le condivisioni file e di tutti i volumi crittografati viene eseguito solo nei data center di cui è stato eseguito l'upgrade. Puoi trovare un elenco completo dei data center di cui è stato eseguito l'upgrade e delle funzioni disponibili [qui](/docs//infrastructure/BlockStorage/new-ibm-block-and-file-storage-location-and-features.html).

## Perché è possibile eseguire il provisioning di {{site.data.keyword.filestorage_short}} con un livello Endurance 10 IOPS in alcuni data center e non in altri?
Il livello 10 IOPS/GB del tipo Endurance di {{site.data.keyword.filestorage_short}} è disponibile solo in data center selezionati e a tale selezione verranno a breve aggiunti dei nuovi data center.  Puoi trovare un elenco completo dei data center di cui è stato eseguito l'upgrade e delle funzioni disponibili [qui](/docs//infrastructure/BlockStorage/new-ibm-block-and-file-storage-location-and-features.html).

## Come posso trovare il punto di montaggio corretto per il mio {{site.data.keyword.filestorage_short}}?
Tutti i volumi {{site.data.keyword.filestorage_short}} crittografati di cui viene eseguito il provisioning nei data center avanzati hanno un punto di montaggio diverso rispetto ai volumi non crittografati. Per assicurarti che stai usando il punto di montaggio corretto, visualizza le informazioni sul punto di montaggio nella pagina **Volume Details** nell'IU. Puoi inoltre accedere al punto di montaggio corrente tramite una chiamata API: `SoftLayer_Network_Storage::getNetworkMountAddress()`.

## Di quanti volumi posso eseguire il provisioning?
Per impostazione predefinita, puoi eseguire il provisioning di un totale combinato di 250 volumi di archiviazione blocchi e file. Per incrementare il tuo limite, contatta il tuo rappresentante delle vendite.

## Quante istanze possono condividere l'uso di un volume {{site.data.keyword.filestorage_short}} di cui è stato eseguito il provisioning?
Il limite predefinito per il numero di autorizzazioni per volume di file è 64. Per incrementare questo limite, contatta il tuo rappresentante delle vendite.

## Quante condivisione file sono consentite in base alla dimensione del volume di file? Quali sono le dimensioni file massime consentite in base alla dimensione del volume?

<table>
  <caption>La tabella 1 mostra che il numero massimo di inode consentiti si basa sulla dimensione del volume. Le dimensioni del volume sono a sinistra. Il numero di inode/condivisioni file è a destra.</caption>
  <thead>
    <tr>
      <th>Dimensione del volume</th>
      <th>Inode/Condivisioni file</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>20 GB </td>
      <td>622.484</td>
    </tr>
    <tr>
      <td>40 GB </td>
      <td>1.245.084</td>
    </tr>          
    <tr>
      <td>80 GB</td>
      <td>2.490.263</td>
    </tr>          
    <tr>
      <td>100 GB</td>
      <td>3.112.863</td>
    </tr>          
    <tr>
      <td>250 GB</td>
      <td>7.782.300</td>
    </tr>          
    <tr>
      <td>500 GB</td>
      <td>15.564.695</td>
    </tr>
    <tr>
      <td>1 TB+</td>
      <td>31.876.593</td>
    </tr>
   </tbody>
</table>

## Misurazione degli IOPS
Gli IOPS vengono misurati in base a un profilo di caricamento di blocchi da 16 KB con 50 percento di letture e 50 percento di scritture casuali. I carichi di lavoro che differiscono da questo profilo potrebbero riscontrare delle prestazioni insoddisfacenti.

## Cosa succede quando uso una dimensione blocco più piccola per la misurazione delle prestazioni?
Il numero massimo di IOPS può essere ottenuto anche se utilizzi dimensioni blocco più piccole. Tuttavia, la velocità effettiva è inferiore, in questo caso. Ad esempio, un volume con 6000 IOPS ha la seguente velocità effettiva alle varie dimensioni blocco:

- 16 KB * 6000 IOPS == ~93,75 MB/sec
- 8 KB * 6000 IOPS == ~46,88 MB/sec
- 4 KB * 6000 IOPS == ~23,44 MB/sec


## L'IOPS allocato viene implementato in base all'istanza o in base al volume? 
L'IOPS viene implementato a livello dei volumi. In altre parole, due host connessi a un volume con 6000 IOPS condividono questi 6000 IOPS.

## Occorre preriscaldare il volume per ottenere la velocità effettiva prevista?
Non è necessario eseguire un preriscaldamento. Puoi osservare la velocità effettiva specificata non appena verrà eseguito il provisioning del volume. 

## È possibile ottenere una velocità effettiva maggiore se viene utilizzata una connessione Ethernet più veloce?
I limiti di velocità effettiva sono impostati su un livello per volume/LUN; pertanto, l'utilizzo di una connessione Ethernet più veloce non aumenta tale limite impostato. Tuttavia, con una connessione Ethernet più lenta, la tua larghezza di banda può essere un potenziale collo di bottiglia.

## I firewall/gruppi di sicurezza hanno ripercussioni sulle prestazioni?
È meglio eseguire il traffico di archiviazione su una VLAN che ignora il firewall. L'esecuzione del traffico di archiviazione tramite i firewall software aumenta la latenza e ha un impatto negativo sulle prestazioni dell'archiviazione.

## Che latenza delle prestazioni ci si può aspettare da {{site.data.keyword.filestorage_short}}?   
La latenza di destinazione nell'archiviazione è di <1ms. L'archiviazione è connessa alle istanze di elaborazione su una rete condivisa e, pertanto, la latenza delle prestazioni esatta dipende dal traffico di rete durante l'operazione.

## Cosa succede ai dati quando i volumi {{site.data.keyword.filestorage_short}} vengono eliminati?
Quando l'archiviazione viene eliminata, gli eventuali puntatori ai dati su tale volume vengono rimossi e, pertanto, i dati diventano inaccessibili. Se viene eseguito nuovamente il provisioning dell'archiviazione fisica a un altro account, viene assegnato un nuovo set di puntatori. Non vi è alcuna possibilità che il nuovo account acceda ad eventuali dati che erano presenti nell'archiviazione fisica. La nuova serie di puntatori mostra tutti 0. I nuovi dati sovrascrivono gli eventuali dati inaccessibili che erano presenti nell'archiviazione fisica.

## Cosa succede alle unità che vengono disattivate dal data center cloud?
Quando le unità vengono disattivate, IBM le distrugge prima del loro smaltimento. Le unità diventano inutilizzabili. Tutti i dati scritti in queste unità diventano inaccessibili.
