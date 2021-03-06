---

copyright:
  years: 2014, 2018
lastupdated: "2018-08-01"

---
{:new_window: target="_blank"}

# 订购 {{site.data.keyword.filestorage_short}}

您可以供应 {{site.data.keyword.filestorage_short}} 存储器并进行微调，以满足您的容量和 IOPS 需求。通过两个指定性能的选项，最充分地利用存储器。

- 可以从具有预定义性能级别的耐久性 IOPS 层中进行选择，以适合没有明确定义性能需求的工作负载。 
- 可以通过指定性能类型的 IOPS 总数来微调存储器，以满足非常具体的性能需求。

## 订购使用预定义的 IOPS 层（耐久性）的 {{site.data.keyword.filestorage_short}}

1. 在 [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} 中，单击**存储** > **{{site.data.keyword.filestorage_short}}**，或者在 {{site.data.keyword.BluSoftlayer_full}}“目录”中，单击**基础架构** > **存储** > **{{site.data.keyword.filestorage_short}}**。
2. 单击右上角的**订购 {{site.data.keyword.filestorage_short}}**。
3. 选择部署**位置**（数据中心）。
   - 确保将新存储器添加到您拥有的计算主机所在位置。
4. 计费。如果选择了具有改进功能的数据中心（标记有星号），那么可以选择“按月计费”或“按小时计费”。 
     1. 对于**按小时**计费，在删除 LUN 时或在计费周期结束时（以先发生者为准），将计算块 LUN 在帐户上存在的小时数。对于使用了数天或不足一个月的存储器，按小时计费是不错的选择。按小时计费仅可用于在这些[精选数据中心](new-ibm-block-and-file-storage-location-and-features.html)内供应的存储器。 
     2. 对于**按月**计费，将从创建日期一直到记帐周期结束按比例计算价格并立即记帐。如果在计费周期结束之前删除了块 LUN，那么不会有任何退款。对于所用数据需要长期（一个月或更长时间）存储和访问的生产工作负载，存储器选择按月计费是不错的选择。
        >**注** - 缺省情况下，对于在**未**更新为使用改进功能的数据中心内供应的存储器，将使用按月计费类型。
5. 在**新存储器大小**字段中，输入存储器大小。
6. 在**存储器 IOPS 选项**部分中，选择**耐久性（分层 IOPS）**。
7. 选择应用所需的 IOPS 层。
    - **0.25 IOPS/GB** 适用于具有低 I/O 强度的工作负载。这些工作负载的典型特点是同时有很大比例的不活动数据。示例应用包括存储邮箱或部门级别文件共享。
    - **2 IOPS/GB** 适用于最通用的用途。示例应用包括托管支持 Web 应用程序的小型数据库或用于系统管理程序的虚拟机磁盘映像。
    - **4 IOPS/GB** 适用于高强度工作负载。这些工作负载的典型特点是同时有较高比例的活动数据。示例应用包括事务型数据库和其他性能敏感型数据库。
    - **10 IOPS/GB** 适用于要求最苛刻的工作负载，例如由 NoSQL 数据库创建的工作负载以及为 Analytics 进行的数据处理。此层在[精选数据中心](new-ibm-block-and-file-storage-location-and-features.html)内提供，用于供应的最高达 4 TB 的存储器。
8. 单击**指定快照空间大小**，然后从列表中选择快照大小。这是除了可用空间以外的空间。有关快照空间注意事项和建议，请阅读[订购快照](ordering-snapshots.html)。
9. 选中**条款和条件**的复选框，然后单击**下订单**。
10. 新的存储器分配会在几分钟后可用。

>**注** - 缺省情况下，总共可以供应 250 个 {{site.data.keyword.blockstorageshort}} 卷。要增加卷的数量，请联系销售代表。请阅读[此处](managing-storage-limits.html)以了解有关增大限制的信息。<br/><br/>有关同时授权的限制，请参阅[常见问题](File-Storage-FAQ.html)。

## 订购使用定制 IOPS（性能）的 {{site.data.keyword.filestorage_short}}

1. 在 [{{site.data.keyword.slportal}}](https://control.softlayer.com/){:new_window} 中，单击**存储** > **{{site.data.keyword.filestorage_short}}**，或者在 {{site.data.keyword.BluSoftlayer_full}}“目录”中，单击**基础架构** > **存储** > **{{site.data.keyword.filestorage_short}}**。
2. 单击右上角的**订购 {{site.data.keyword.filestorage_short}}**。
3. 单击**位置**，然后选择数据中心。
   - 确保将新存储器添加到您拥有的计算主机所在位置。
4. 计费。如果选择了具有改进功能的数据中心（标记有星号），那么可以选择“按月计费”或“按小时计费”。 
     1. 对于**按小时**计费，在删除 LUN 时或在计费周期结束时（以先发生者为准），将计算块 LUN 在帐户上存在的小时数。对于使用了数天或不足一个月的存储器，按小时计费是不错的选择。按小时计费仅可用于在这些[精选数据中心](new-ibm-block-and-file-storage-location-and-features.html)内供应的存储器。 
     2. 对于**按月**计费，将从创建日期一直到记帐周期结束按比例计算价格并立即记帐。如果在计费周期结束之前删除了块 LUN，那么不会有任何退款。对于所用数据需要长期（一个月或更长时间）存储和访问的生产工作负载，存储器选择按月计费是不错的选择 。
        >**注** - 缺省情况下，对于在**未**更新为使用改进功能的数据中心内供应的存储器，将使用按月计费类型。
5. 在**新存储器大小**字段中，输入存储器大小。
6. 在**存储器 IOPS 选项**部分中，选择**性能（分配的 IOPS）**。
7. 在**性能（分配的 IOPS）**字段中，输入 IOPS。
8. 单击**指定快照空间大小**，然后从列表中选择快照大小。这是除了可用空间以外的空间。有关快照空间注意事项和建议，请阅读[订购快照](ordering-snapshots.html)。
9. 选中**条款和条件**的复选框，然后单击**下订单**。
10. 新的存储器分配会在几分钟后可用。

>**注** - 缺省情况下，总共可以供应 250 个 {{site.data.keyword.blockstorageshort}} 卷。要增加卷的数量，请联系销售代表。请阅读[此处](managing-storage-limits.html)以了解有关增大限制的信息。<br/><br/>有关同时授权的限制，请参阅[常见问题](File-Storage-FAQ.html)。


## 连接新存储器

完成供应请求后，授权主机来访问新存储器并配置连接。根据主机的操作系统，访问相应的链接。
- [在 Linux 上访问 {{site.data.keyword.filestorage_short}}](accessing-file-storage-linux.html)
- [在 CentOS 中安装 NFS/{{site.data.keyword.filestorage_short}}](mounting-nsf-file-storage.html)
- [在 CoreOS 上安装 {{site.data.keyword.filestorage_short}}](mounting-storage-coreos.html)
- [使用 cPanel 配置 {{site.data.keyword.filestorage_short}} 进行备份](configure-backup-cpanel.html)
- [使用 Plesk 配置 {{site.data.keyword.filestorage_short}} 进行备份](configure-backup-plesk.html)
- [在 ESXi 主机上安装 {{site.data.keyword.filestorage_short}} 卷](architecture-guide-file-storage-vmware.html)


## 识别发票上的 {{site.data.keyword.filestorage_short}} 卷

所有 LUN 都将在发票上显示为行项。“耐久性”将显示为“耐久性存储服务”，“性能”将显示为“性能存储服务”。此费率根据您的存储级别而有所不同。可以展开“耐久性”或“性能”，以查看它是否为 {{site.data.keyword.filestorage_short}}。
