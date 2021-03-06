---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-29"

---
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}

# 在 CoreOS 上安装 {{site.data.keyword.filestorage_short}}

CoreOS 是一种功能强大的 Linux 分发版，构建用于简化对不同基础架构上大型可扩展部署的管理。CoreOS 基于 Chrome OS 的构建版，可维护轻量级主机系统，并对所有应用程序使用 Docker 容器。

## 安装可移植存储器

所有辅助安装文件都会放入 `/etc/systemd/system` 目录中，因为系统级别安装位于 CoreOS 中的只读目录中。首先，必须创建 `MOUNTPOINT.mount` 文件。`.mount` 文件中的 **Where** 部分必须与文件名相匹配。如果安装点不是直接位于 `/` 下，那么您必须使用语法 `path-to-mount.mount` 对该文件命名。例如，如果要将可移植存储驱动器安装到 `/mnt/www`，请将文件命名为 `mnt-www.mount`。

可以使用 `fdisk` 或 `parted` 来创建分区，并确保创建的文件系统与 `.mount` 文件中列出的文件系统相匹配，否则服务将无法启动。


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


CoreOS 使用 `systemd`，因此为了使安装点在重新启动后继续有效，必须启用 `*.mount` 文件。如果使用 `--now` 标志，那么将立即安装分区，并将其设置为在引导时启动。

```
$ systemctl enable --now mnt-www.mount
```
{:pre}

## 安装 NFS/{{site.data.keyword.filestorage_short}}

安装 {{site.data.keyword.filestorage_short}} 的过程相同。因为安装的是 NFS，所以可以在安装文件中使用 `Options=` 行来指定更多选项。 

在示例中，NFS 设置为安装在 `/data/www` 上。可以在 {{site.data.keyword.filestorage_short}} 列表页面中或通过以下 API 调用来获取 {{site.data.keyword.filestorage_short}} 实例的 NFS 安装点：`SoftLayer_Network_Storage::getNetworkMountAddress()`。

```
$ cat data-www.mount
[Unit]
Description = Mount for Container Storage

[Mount]
What=<nfs_mount_point>
Where=/data/www
Type=nfs
Options=vers=4,sec=sys,noauto

[Install]
WantedBy = multi-user.target
```
{:codeblock}

现在，请启用安装，并检查它是否正确安装。

```
systemctl enable --now /etc/systemd/system/data-www.mount

cluster1 ~ # mount |grep data
<nfs_mount_point> on /data/www type nfs4 (rw,relatime,vers=4.0,rsize=65536,wsize=65536,namlen=255,hard,proto=tcp,port=0,timeo=600,retrans=2,sec=sys,clientaddr=10.81.x.x,local_lock=none,addr=10.1.x.x)
```
{:codeblock}
 
## 安装 NAS/CIFS

在 CoreOS 中不支持以本机方式安装 CIFS 共享，但有一个简单的变通方法可允许主机系统安装 NAS 共享。您可以使用容器来构建 `mount.cfis` 模块，然后将其复制到 CoreOS 系统。
 
在 CoreOS 系统上，运行以下命令来下载并进入 Fedora 容器。

```
docker run -t -i -v /tmp:/host_tmp fedora /bin/bash
```
{:pre}
 
位于容器中后，请运行以下命令来构建 CIFS 实用程序。

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
 
现在，已将 `mount.cifs` 文件复制到主机，您可以通过输入 `exit` 命令或按 **ctrl+d** 来退出 Docker 容器。返回到 CoreOS 系统后，可以使用以下命令来安装 CIFS 共享： 
```
/tmp/mount.cifs //nasXXX.service.softlayer.com/USERNAME -o username=USERNAME,password=PASSWORD /path/to/mount
```
{:pre}
 
## 安装 ISCSI

目前 CoreOS 中不支持此功能，但未来发行版中会纳入此功能 - https://github.com/coreos/bugs/issues/634
