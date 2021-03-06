---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-24"

---
{:new_window: target="_blank"}
{:pre: .pre}
 
# Configuración de {{site.data.keyword.filestorage_short}} para la copia de seguridad con cPanel

El objetivo de este artículo es ofrecer instrucciones para configurar sus copias de seguridad para almacenarlas en {{site.data.keyword.filestorage_full}} a través de cPanel. Suponemos que está disponible el acceso de SSH sudo o root y de WebHost Manager (WHM) completo. Este ejemplo se basa en un host **CentOS 7**.

**Nota**: encontrará la documentación de cPanel sobre cómo configurar el directorio de copias de seguridad [aquí](https://docs.cpanel.net/display/68Docs/Backup+Configuration#BackupConfiguration-ConfigureBackupDirectory){:new_window}.

1. Conéctese al host a través de SSH.

2. Asegúrese de que un exista un destino de punto de montaje. <br />
   **Nota**: de forma predeterminada, el sistema cPanel guarda los archivos de copia de seguridad en local, en el directorio `/backup`. En este documento se supone que la carpeta `/backup` ya existe y contiene copias de seguridad, de modo que utilizaremos `/backup2` como el nuevo punto de montaje.
   
3. Configure {{site.data.keyword.filestorage_short}} como se describe en [Acceso a {{site.data.keyword.filestorage_short}} en Red Hat Enterprise Linux](accessing-file-storage-linux.html) y [Montaje de NFS/{{site.data.keyword.filestorage_short}} en CentOS](mounting-nsf-file-storage.html). Monte el volumen en `/backup2` y configúrelo en la tabla del sistema de archivos `/etc/fstab` para habilitar el montaje al arrancar. <br />
   **Nota**: de forma predeterminada, NFS degradará los archivos creados con los permisos de root al usuario nobody. Para permitir que los clientes root retengan los permisos de root en la unidad compartida NFS, se debe añadir `no_root_squash` a `/etc/exports`. <br />
   **Nota**: hay instrucciones disponibles para [Montar NFS/{{site.data.keyword.filestorage_short}} en CoreOS](mounting-storage-coreos.html) también. <br />

4. **Opcional**: Copie las copias de seguridad existentes en el nuevo almacenamiento. Utilice `rsync` por ejemplo:
   ```
   rsync -azv /backup/* /backup2/
   ```
   {: pre}
    
    **Nota**: este mandato transfiere sus datos comprimidos conservando todo lo posible, excepto los enlaces fijos. También proporciona información sobre los archivos que se están transfiriendo, además de un breve resumen final.
    
5. Inicie una sesión en WebHost Manager y vaya a la configuración de la copia de seguridad a través de **Inicio** > **Copia de seguridad** > **Configuración de copia de seguridad**.

6. Edite la configuración para guardar las copias seguridad en el nuevo punto de montaje. 
    - Cambie el directorio de copia de seguridad predeterminado especificando la vía de acceso absoluta a la nueva ubicación en lugar del directorio `/backup/`. 
    - Seleccione **Habilitar el montaje de una unidad de copia de seguridad**. Este valor hace que el proceso de configuración compruebe el archivo `/etc/fstab` para el montaje de la copia de seguridad (`/backup2`). <br /> **Nota**: si existe un montaje con el mismo nombre que el directorio intermedio, el proceso de configuración de copia de seguridad monta la unidad y realiza aquí la copia de seguridad de la información. Cuando el proceso de copia de seguridad finaliza, desmonta la unidad. 

7. Aplique los cambios pulsando **Guardar configuración** en la parte inferior de la interfaz **Configuración de copia de seguridad**.

8. **Opcional**: en función de sus necesidades específicas, elimine el almacenamiento antiguo del servidor y cancele desde la cuenta.
