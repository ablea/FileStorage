---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-29"

---

# Protegendo seus dados - criptografia gerenciada por provedor em repouso 

O {{site.data.keyword.BluSoftlayer_full}} leva a necessidade de segurança a sério e entende a importância de ser capaz de criptografar dados para mantê-los seguros. Com a criptografia gerenciada por provedor, o {{site.data.keyword.filestorage_full}} provisionado com as opções Endurance ou Performance é criptografado por padrão sem nenhum custo adicional e nenhum impacto no desempenho.

O recurso de criptografia em repouso gerenciada por provedor usa os protocolos padrão de mercado a seguir:

* Criptografia AES-256 de padrão de mercado
* As chaves são gerenciadas internamente com o Key Management Interoperability Protocol (KMIP) padrão
de mercado
* O armazenamento é validado com relação aos padrões a seguir: 
    - Publicação do Federal Information Processing Standard (FIPS) 140-2, 
    - Federal Information Security Management Act (FISMA), 
    - Health Insurance Portability and Accountability Act (HIPAA), 
    - Payment Card Industry (PCI), 
    - Basileia II, 
    - Security Breach Information Act da Califórnia (SB 1386) e 
    - Conformidade da Medida de Proteção de Dados da UE 95/46/EC.

## Protegendo suas capturas instantâneas ou armazenamento replicado  

Todas as capturas instantâneas e réplicas de armazenamento de arquivo criptografado também são criptografadas por padrão. Esse recurso não pode ser desligado em uma base de volume.

## Provisionando armazenamento com criptografia

O recurso de criptografia em repouso gerenciado pelo provedor está disponível em data centers selecionados. Todo o armazenamento pedido nesses data centers é provisionado automaticamente com criptografia para dados em repouso. Clique [aqui](new-ibm-block-and-file-storage-location-and-features.html) para ver a lista atual de data centers nos quais a criptografia do {{site.data.keyword.filestorage_short}} está disponível.

Ao pedir o {{site.data.keyword.filestorage_short}}, selecione um data center que esteja marcado com um asterisco (`*`). É possível ver um ícone de bloqueio à direita do campo Nome do LUN/Volume que indica que o volume está criptografado. Veja a Figura 1.

![O ícone de bloqueio indica que o LUN está criptografado](/images/encryptedstorage.png)
<caption>Figura 1. Exemplo do ícone de bloqueio que indica que o volume está criptografado.</caption>



>**Nota** - Qualquer armazenamento não criptografado que tenha sido provisionado antes do upgrade de um data center **não** é criptografado automaticamente. Se você possuir um armazenamento não criptografado em um data center submetido a upgrade e desejar tê-lo criptografado, será necessário criar um novo volume e mover seus dados. Para obter mais informações, consulte [Migração do File Storage em data centers submetidos a upgrade](migrate-file-storage-encrypted-file-storage.html)
