---
title: Lidarr快速入门
description: 
published: true
date: 2022-07-14T14:10:13.343Z
tags: 
editor: markdown
dateCreated: 2021-06-13T06:14:53.615Z
---

# 目录

- [目录](#目录)
- [快速入门设置指南](#快速入门设置指南)
- [注意事项](#注意事项)
- [概念](#概念)
  - [发布（元数据）](#发布元数据)
  - [艺术家（元数据）](#艺术家元数据)
- [首次启动](#首次启动)
- [设置](#设置)
  - [媒体管理](#媒体管理)
  - [配置文件](#配置文件)
  - [质量](#质量)
  - [索引器](#索引器)
  - [下载客户端](#下载客户端)
    - [{.tabset}](#tabset)
      - [Usenet](#usenet)
      - [BitTorrent](#bittorrent)
- [首个艺术家](#首个艺术家)
- [首次下载/导入](#首次下载导入)
- [快速入门 - 高级](#快速入门-高级)
  - [Lidarr使用案例](#lidarr使用案例)
    - [松散文件](#松散文件)
    - [特殊库](#特殊库)
  - [导入现有库或文件](#导入现有库或文件)
    - [准备现有文件](#准备现有文件)
      - [文件夹结构](#文件夹结构)
      - [标记](#标记)
    - [导入前的注意事项](#导入前的注意事项)
    - [开始导入](#开始导入)

# 快速入门设置指南

> 此页面仍在编写中，尚未完成。欢迎贡献。

> 要详细了解所有设置，请查看[Lidarr =>设置](/lidarr/settings)。
{.is-info}

在本指南中，我们将尝试解释使用Lidarr开始的基本设置。我们将跳过您在屏幕上可能看到的一些选项。如果您想深入了解这些选项，请参阅FAQ和文档中的相应页面以获取完整的解释。

> 请注意，在`橙色`的屏幕截图和GUI设置中是高级选项，因此您需要在页面顶部单击“显示高级”以使它们可见。
{.is-warning}

# 注意事项

在本指南中，我们将解释开始使用Lidarr的基本步骤。本指南假设您已经安装了该应用程序。安装说明可以在以下页面找到：[安装](/lidarr/installation)。我们将重点介绍最低限度的设置和选项，以获得可工作的配置。如果适用以下任何情况，则还有其他设置和注意事项：

- 现有库或文件
- 不正确的用例
- 不正确的文件夹结构
- 不正确或极其复杂的标记
- 松散的文件集合
- 基于特殊音乐库的专业库：古典音乐、单曲、电子音乐

如果适用上述任何情况，请参阅“快速入门 - 高级”部分。

本指南分为几个部分。建议阅读整个指南以获得全面的了解，但您也可以跳转到特定部分以解决即时问题。使用左侧的大纲可以快速跳转。

# 概念

要正确使用Lidarr，必须了解底层概念。从高层次上讲，它遵循其他Arr应用程序的原则。Lidarr充当音乐库管理系统、数据聚合器和自动化平台，用于查找和下载媒体。

然后，偏离的程度相当大。音乐库管理是一个非常复杂的过程，因为有许多竞争变量妨碍了这个过程。与电影或电视节目管理不同，音乐标记、命名或存储没有一套一致的标准。这种情况进一步复杂化了从实体媒体到电子媒体的音乐分发方法的变化。最后，处理此管理的意见各不相同。

Lidarr利用来自数据聚合服务的信息来正确标记和管理音乐库。这些第三方数据代表了定义的类别和类型的媒体。

> 如果第三方服务中不存在数据，则无法由Lidarr管理。
有关参与和贡献的详细信息，请参见下面的详细信息。
{.is-warning}

主要使用的服务是[MusicBrainz](https://musicbrainz.org/)。这是一个免费的服务，由社区驱动，最终存在并生存于您的贡献和参与。创建和贡献发布超出了本指南的范围。您可以在这里找到说明：[如何贡献](https://musicbrainz.org/doc/How_to_Contribute)

最终，数据由第三方数据标准定义。如果这些标准与您的用例不符，则**Lidarr可能不是正确的解决方案**。用于管理媒体的其他应用程序可能包括：

[Beets媒体管理](https://beets.io/)
[MusicBrainz Picard](https://picard.musicbrainz.org/)
[Music Bee](https://getmusicbee.com/)

这些实现可以与Lidarr一起使用，但这超出了本指南的范围。

## 发布（元数据）

Lidarr选择了音乐媒体管理的`发布`标准。这意味着为了系统正常工作，系统处理的所有媒体都必须是`发布`。

发布的示例：

- 专辑
- EP
- 单曲
- 广播

要管理的每个项目都必须在第三方数据服务中有一个相应的`发布`。

> `发布`必须存在于第三方服务中，才能在Lidarr中进行管理。

## 艺术家（元数据）

艺术家就是所期望的`发布艺术家`。不幸的是，艺术家的命名、风格、随时间的变化、用户偏好和其他原因使得构成这个`发布艺术家`的内容变得复杂。

正确和不正确的“艺术家”示例：

- Bob Dylan
- BOB DYLAN
- The Bob Dylan
- Bob Dylan, The
- Bob Dylan & the Band
- Bob Dylan feat. The Band
- The Band featuring Bob Dylan
- ...

这个列表可以继续下去。再次强调，所有的`发布`都与一个`艺术家`相关联。您必须找到（稍后在本指南中介绍）并使用正确的`艺术家`来下载`发布`。

> `发布艺术家`必须存在于第三方服务中，才能在Lidarr中进行管理。

# 首次启动

安装并启动Lidarr后，通过打开浏览器并转到`http://{your_ip_here}:8686`来访问。

![lidarr_qs_startup.png](/assets/lidarr/quick-start-guide/lidarr_qs_startup.png)

启动屏幕上显示了两个选项，但我们最初不会使用它们。

# 设置

我们将使用默认配置的设置来配置Lidarr。这将使用现有的配置文件、质量、标签等。

> 要详细了解所有设置，请查看[Lidarr > 设置](/lidarr/settings)。
{.is-info}

## 媒体管理

首先，我们将查看`媒体管理`，在其中我们将设置`根文件夹`。这将是存储媒体文件的位置。

> 不要将Lidarr媒体存储在云存储提供商上！由于Lidarr使用标签的方式，这将耗尽任何API限制并引起问题。将您的库保留在您的网络上。
{.is-warning}

单击左侧菜单上的`设置` > `媒体管理`。

![lidarr_qs_mediamanagement.png](/assets/lidarr/quick-start-guide/lidarr_qs_mediamanagement.png)

单击`根文件夹`的`添加（+）`。

您将看到以下窗口：

![lidarr_qs_rootfolder.png](/assets/lidarr/quick-start-guide/lidarr_qs_rootfolder.png)

- **名称** - 这是存储位置的`友好名称`。
- **路径** - 这是实际的数据存储位置的`路径`。系统/用户必须具有对此存储路径的适当权限。此文件夹不能是您的下载位置！

将其他选项保留为默认值。

> 如果使用具有现有文件的`根文件夹`。请查看“快速入门 - 高级”部分以了解注意事项。
{.is-warning}

> \* 非Windows：如果您使用的是NFS挂载，请确保启用了`nolock`。
> \* 如果您使用的是SMB挂载，请确保启用了`nobrl`。
{.is-warning}

> 配置Lidarr运行的用户和组必须对此位置具有读写访问权限。{.is-info}

> 您的下载客户端将下载到下载文件夹，然后Lidarr将其导入到您的媒体文件夹（最终目标），您的媒体服务器将使用该文件夹。
{.is-info}

> **您的下载文件夹和媒体文件夹不能是同一个位置**。
{.is-danger}

## 配置文件

`设置` > `配置文件`

配置文件设置将保持默认值。

## 质量

`设置` > `质量`

质量设置将保持默认值。

## 索引器

`设置` > `索引器`

此部分设置您将用于查找可下载媒体文件的索引器/跟踪器。

单击`索引器`的`添加（+）`。您将看到一个包含许多不同选项的新窗口。Lidarr将Usenet索引器和BitTorrent跟踪器都视为`索引器`。

至少添加一个`索引器`，以便Lidarr能够正确查找可用的文件。

理解`索引器`背后的配置/概念超出了本指南的范围。互联网上有大量关于此主题的信息。

## 下载客户端

`设置` => `下载客户端`

![Lidarr-settings-download-clients.png](/assets/lidarr/Lidarr-settings-download-clients.png)

下载和导入是大多数人遇到问题的地方。从高层次的角度来看，软件需要能够与您的下载客户端进行通信，并访问其下载的文件。支持的下载客户端种类繁多，设置更是千差万别。这意味着虽然有一些常见的设置，但没有一个正确的设置，每个人的设置可能都有所不同。但是，错误的设置有很多。

> 有关更多信息，请参见[设置页面](/lidarr/settings#download-clients)，[更多信息（支持的）](/lidarr/supported#download-clients)页面以及[TRaSH的下载客户端指南](https://trash-guides.info/Downloaders/)。
{.is-info}

### {.tabset}

#### Usenet

{#usenet}

- Lidarr将向您的客户端发送下载请求，并将其与您在下载客户端设置中配置的标签或类别名称相关联。
  - 示例：电影、电视、系列、音乐等。
- Lidarr将通过您的下载客户端的API监视使用该类别名称的活动下载。
- 下载完成后，Lidarr将根据您的下载客户端报告的最终文件位置来了解该文件的位置。此文件位置几乎可以是任何地方，只要它与您的媒体文件夹分开并且Lidarr可以访问。
- Lidarr将扫描该完成的文件位置以查找Lidarr可以使用的文件。它将解析文件名以将其与请求的媒体进行匹配。如果可以做到这一点，它将根据您的规格对文件进行重命名，并将其移动到指定的媒体位置。
- 默认情况下启用原子移动（即时移动）。您的已完成下载目录和媒体库的文件系统和挂载点必须相同。如果原子移动失败或您的设置不支持硬链接和原子移动，则Lidarr将退回并复制文件，然后从源中删除文件，这会导致IO密集型操作。
- 如果在Lidarr的设置中启用了“完成的下载处理 - 删除”选项，则会将下载的剩余文件通过请求发送给您的客户端以删除/移除发布。

#### BitTorrent

{#bittorrent}

- Lidarr将向您的客户端发送下载请求，并将其与您在下载客户端设置中配置的标签或类别名称相关联。
  - 示例：电影、电视、系列、音乐等。
- Lidarr将通过您的下载客户端的API监视使用该类别名称的活动下载。
- 完成的文件保留在其原始位置，以便您可以种子文件（可以在下载客户端或在Lidarr中的特定下载客户端中调整比率或时间）。当文件导入到您的媒体文件夹时，如果您的设置支持硬链接，则Lidarr将创建硬链接，否则将复制文件。
- 默认情况下启用硬链接。[硬链接将不使用任何额外的磁盘空间。](https://trash-guides.info/Hardlinks/Hardlinks-and-Instant-Moves/)您的已完成下载目录和媒体库的文件系统和挂载点必须相同。如果硬链接创建失败或您的设置不支持硬链接，则Lidarr将退回并复制文件。
- 如果在Lidarr的设置中启用了“完成的下载处理 - 删除”选项，并且客户端报告种子完成并停止（完成后暂停），Lidarr将从您的客户端中删除种子并要求客户端删除种子数据。

# 首个艺术家

如果按照本指南操作，您的`根文件夹`没有任何媒体文件，则需要添加一个`艺术家`。

`库` > `添加新的`

![lidarr_qs_addnew.png](/assets/lidarr/quick-start-guide/lidarr_qs_addnew.png)

这将链接到搜索屏幕，以查找要添加的艺术家。搜索并选择您要添加的`艺术家`。这将打开“添加新艺术家”窗口。

![lidarr_qs_addnewdylan.png](/assets/lidarr/quick-start-guide/lidarr_qs_addnewdylan.png)

我们将使用默认选择。这应该包括：

- 根文件夹 - 您创建的文件夹
- 监视 - 无
- 质量配置文件 - 任何
- 标签 - （空）
- 开始搜索缺失的专辑 - 未选中

这将启动`艺术家`元数据下载。这将根据要收集的数据量需要一些时间。请记住，此信息来自第三方来源，其完整性仅取决于社区的贡献。

单击新添加的`艺术家`（此示例中为Bob Dylan）。

> 默认的`元数据配置文件`正在使用，只显示`发布类型`为`录音室专辑`的`发布`。
![lidarr_qs_dylan.png](/assets/lidarr/quick-start-guide/lidarr_qs_dylan.png)

> 不喜欢下载的元数据？- 贡献以使其更好！
{.is-info}

# 首次下载/导入

终于可以下载/导入您的第一个`发布`了！

找到您要添加到库中的`发布`。选择该发布旁边的手动搜索（人类）图标。

![lidarr_qs_dylanrelease.png](/assets/lidarr/quick-start-guide/lidarr_qs_dylanrelease.png)

这将打开“发布”选择窗口。此窗口将显示`索引器`查询的结果，或者简单地说，可用下载的搜索结果。

> 默认的`质量配置文件`允许任何文件类型。默认的`发布配置文件`允许所有下载。有关这些高级设置的详细说明，请查看[Lidarr > 设置](/lidarr/settings)。

![lidarr_qs_dylandownload.png](/assets/lidarr/quick-start-guide/lidarr_qs_dylandownload.png)

查看下载窗口以获取各种提供的信息：

1. 标题 - 这是`索引器`返回的下载名称。
1. 质量 - 这是Lidarr根据标题确定的质量。
1. 警告指示器将提供下载未通过Lidarr检查的原因的描述。在示例中，搜索返回了“错误的专辑”。

在查看后，选择下载图标（编号4）以下载可用的`发布`。

如果配置正确，下载将被发送到您的`下载客户端`。

下载将添加到`队列`中，并将按照您的类型的`下载客户端`的各种状态进行处理。

最后，下载将导入到您的`根文件夹`。如果一切顺利，它应该显示如下。

![lidarr_qs_dylansucess.png](/assets/lidarr/quick-start-guide/lidarr_qs_dylansuccess.png)

您可以在`根文件夹`中找到已下载的文件，并可以使用您选择的媒体播放器进行播放。

![lidarr_qs_dylanfolder.png](/assets/lidarr/quick-start-guide/lidarr_qs_dylanfolder.png)

# 快速入门 - 高级

这个高级部分适用于具有特殊考虑因素的设置。请查看是否适用于您的配置，并可能节省一些麻烦。

> 下面的部分将帮助您解决常见的问题和困惑。
{.is-warning}

## Lidarr 的使用案例

如前所述，在概念部分中。如果您的使用场景与 Lidarr 的“发布”管理系统不匹配，则不应使用 Lidarr。Lidarr 将无法处理以下使用案例：

- 散乱的文件 - 来自多个艺术家（非合辑）或多个“发布”的文件
- 专业音乐库：古典音乐、单曲、电子音乐

### 散乱的文件

Lidarr 无法处理散乱的文件。最好不要尝试将这些文件与 Lidarr 一起使用。

### 专业音乐库

专业音乐库对于任何管理系统都会带来独特的问题。这些情况下，Lidarr 可能可以工作，但可能需要您付出大量的努力，基本上放弃内置的自动化功能。例如：

- **古典音乐** - 通常需要进行详细的标记。`发布`的元数据可能不存在或不正确。
- **单曲** - 单曲可能不是真正的“发布”。第三方数据服务将返回没有元数据的结果。它们将无法自动化，Lidarr 将无法应用管理。
- **电子音乐** - 这不适用于电子音乐流派中的“发布”。这是指混音、节拍、采样等库（Beatport）。第三方数据源无法识别这些作为“发布”。它们将无法自动化，Lidarr 将无法应用管理。

## 导入现有库或文件

> 请注意，Lidarr 不会定期搜索“发布”。请查看以下两个常见问题解答条目，了解 Lidarr 的工作原理的详细信息。
[如何让 Lidarr 找到发布？](/lidarr/faq#how-does-lidarr-find-releases) 和 [Lidarr 如何工作？](/lidarr/faq#how-does-lidarr-work)
{.is-info}

> 自动导入是一个定期进行的过程，一旦开始就无法停止
在完整地查看本节之前，请勿添加具有现有文件的“根文件夹”
{.is-warning}

Lidarr 使用自动化系统来添加位于您的“根文件夹”中的“发布艺术家”和“发布”。

如果 Lidarr 的使用案例匹配，并且您没有独特或专业的音乐库，您可以继续导入您的现有库。

确保您现有的库文件结构良好，并遵循 Lidarr 的“发布”管理系统非常重要。这意味着以下内容将无法工作：

- 不正确的文件夹结构 - 文件位于一个文件夹中 - 参考准备>文件夹结构部分
- 不正确或非常复杂的标记 - 参考准备>标记部分

### 准备现有文件

为了使自动化过程正常工作，您的文件必须经过准备，以确保其能够高效地流动或根本能够工作。

#### 文件夹结构

建议遵循标准的文件夹结构：

\根文件夹\发布艺术家\发布\XX - 曲目

结合正确的标记，这将使媒体播放器能够识别近95%或更多的文件。

#### 标记

标记可能是一个复杂的过程。文件的数量以及它们当前的标记方式将决定所需的工作量。

标记文件的推荐方法包括：

- MusicBrainz Picard
- Beets
- MusicBee、MediaMonkey、JRiver

使用这些应用程序超出了本指南的范围，但最好在标记过程中将 MusicBrainz 发布 ID 与之关联。

> 大多数标记软件都能够在正确标记文件的同时进行文件夹结构和重命名。
{.is-info}

### 导入前的注意事项

一旦文件正确标记和命名，应验证以下项目，以确保导入过程能够成功完成：

- **系统架构** - 推荐使用 x64 / 64 位 - 导入大型库需要系统访问大量的 RAM 并更高效地计算。虽然支持 x86 / 32 位，但效率不高，需要更长的时间。
- **系统内存需求（RAM）** - 最低 4GB，推荐 8GB - 导入过程对内存要求很高，Lidarr 导入并同时打开浏览器将导致大量的 RAM 使用。
- **`发布`的碟片/曲目限制** - 应从导入过程中删除具有大量曲目或碟片的“发布”。可以使用内置的程序手动导入它们。没有确切的限制，但为了安全起见，应删除超过 25 张碟片或 250 个曲目的“发布”。
- **具有许多`发布`的`发布艺术家`** - Lidarr 的自动化过程会将发布与您的文件进行比较。虽然不太可能失败，但这些文件经过自动化过程将导致导入时间大大增加。有些艺术家有数千个发布。
- **时间** - 自动导入过程需要时间。对于 500 个正确标记的“发布”，合理的估计是 1 小时。这在很大程度上取决于您的存储、互联网速度和系统性能。

### 开始导入

//

即将推出

- 监视 * - 这将为“根文件夹”设置默认的监视选项（`发布`）。
- 质量配置文件 * - 这将为“根文件夹”设置默认的质量选项。
- 元数据配置文件 * - 这将为“根文件夹”设置默认的元数据选项。