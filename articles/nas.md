# 整了个 NAS

最近整了个 [DS423+](https://x.com/yinan_ch/status/1840031881254797353) 来代替之前的老旧 MacBook Pro + 一块外接硬盘的 NAS/homeserver 方案。

我买了四块盘。 1、2 8TB 希捷盘做了 RAID1 冗余，其余两块略大的盘 Basic（希捷12TB 和 16 TB），另有两块 NVMe SSD 作为存储池跑 Docker，放告诉存储。几天用下来，发现 NAS 有几个好处，

> 1. 数据从冷数据变成了 24 小时在线的热数据，可以随时访问编辑，而不用插硬盘挂个线。而且，终于把散落在各个硬盘的数据整合在了一起，之前一份数据为了访问方便可能存到了好几块外接硬盘上，而 NAS 提供了个中心化的存储方案。另外据我所知，Btrfs 格式支持 deduplication， 重复数据只存一份，不会浪费空间。
> 2. Raid1 冗余允许一块硬盘坏了重建，和 DSM 的较为完备的预警系统以及文件完整性检查。之前在移动硬盘上数据坏了都不知道，只能从备份恢复（如果有备份的话）。
> 3. Btrfs 文件系统支持快照，可以随时回滚到之前的状态（群晖有官方套件 Snaptshots Replication，非常推荐，就像 macOS 的时间机器一样）。
> 4. 无线的时间机器备份真的很爽。第一次有点慢可以考虑接网线备份，之后增量备份的时候就不用管了。
> 5. 折腾的乐趣

不得不说， DSM 虽然最近[走了倒车](https://www.reddit.com/r/synology/comments/1feqy62/synology_722_proves_that_this_company_doesnt_care/)，但仍是一个很新手友好和功能和生态完善的 NAS 系统（其他 unraid truenas 没有用过不做评价）。用下来我的感觉是，DSM 的很多功能是在教用户应该怎么维护数据健康/维持高可用性，怎么做备份和快照。另外还有什么影音库，照片库，跑下载，甚至 DNS，软路由等都是 NAS 很好用的功能，不过目前对我来说收益不是特别大。

当然缺点也有:

一是读写速度显然没有插个固态快（受制于网络和机械硬盘），不过花几十块钱买个交换机用 smb 双通道 (multichannel) 也算上了 250 MB/s, 比外接一块机械硬盘快了。 

二是 8TB 以上7200转的硬盘读写时炒豆子声音还是很大，解决方法是换5400转的硬盘或者上 SATA SSD 解决。如果跑 Docker 和虚拟机，也可以考虑装个 NVME SSD 把套件数据和 Docker 转移到 SSD 存储池上。加内存条减少 swap 或许也有帮助。

三是 DS423+ 的 DSM 系统虽然好用，但是奈何硬件太弱了，Intel Celeron J3455, PCIe 2.0 x 1 (NVME 只能跑 500 MB/s)，1Gbps 网口，这些要升级就得加钱，然而一台白裙的价格对于其硬件来说已经很贵了。

关于 SSD 的配置和其他资料，推荐一个链接和两个 Github 项目。
> 1. [专门开一贴，群晖硬软件的的各种坑及解决方案](https://www.chiphell.com/thread-2187138-1-1.html)
> 2. [https://github.com/007revad/Synology_M2_volume](https://github.com/007revad/Synology_M2_volume)
> 3. [https://github.com/007revad/Synology_HDD_db](https://github.com/007revad/Synology_HDD_db)

另外再提一嘴数据安全，虽然 Raid 有冗余，但是冗余不是备份！遵循 [3-2-1 原则](https://en.wikipedia.org/wiki/Backup)定期备份数据到云端是很有必要的，防止硬盘损坏，天灾人祸等意外情况。后面会写一篇文章分享一下我的备份方案。

最后给我的 NAS 上个照片。

![DS423+](../output/pics/nas.jpeg)