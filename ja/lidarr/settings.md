---
title: Lidarrの設定
description: 
published: true
date: 2022-07-24T14:21:19.994Z
tags: lidarr, needs-love, settings
editor: markdown
dateCreated: 2021-06-14T21:36:07.513Z
---

# 目次

- [目次](#目次)
- [設定](#設定)
- [ダウンロードクライアント](#ダウンロードクライアント)
  - [概要](#概要)
  - [ダウンロードクライアントの処理](#ダウンロードクライアントの処理)
  - [Usenet](#usenet)
  - [BitTorrent](#bittorrent)
  - [ダウンロードクライアント](#ダウンロードクライアント-1)
    - [サポートされているダウンロードクライアント](#サポートされているダウンロードクライアント)
    - [Usenetクライアントの設定](#usenetクライアントの設定)
    - [Torrentクライアントの設定](#torrentクライアントの設定)
    - [Torrentクライアントのダウンロードの互換性を削除する](#torrentクライアントのダウンロードの互換性を削除する)
  - [完了したダウンロードの処理](#完了したダウンロードの処理)
    - [完了したダウンロードの削除](#完了したダウンロードの削除)
    - [ダウンロードの処理に失敗した場合](#ダウンロードの処理に失敗した場合)
  - [リモートパスのマッピング](#リモートパスのマッピング)
- [インポートリスト](#インポートリスト)
  - [インポートリスト](#インポートリスト-1)
  - [インポートリストの除外](#インポートリストの除外)
  - [インポートリストの追加](#インポートリストの追加)
- [接続](#接続)
- [タグ](#タグ)
- [一般](#一般)
  - [アップデート](#アップデート)

# 設定

このページは作業中であり、他の \*Arr ページに基づいた貢献は歓迎されています。

# ダウンロードクライアント

> サポートされているダウンロードクライアントの情報は、このセクションの[詳細情報（サポート）](/lidarr/supported#download-clients)ページで確認できます。
{.is-info}

## 概要

- ダウンロードとインポートは、多くの人が問題を抱える箇所です。ソフトウェアは、ダウンロードクライアントと通信し、ダウンロードしたファイルにアクセスできる必要があります。サポートされているダウンロードクライアントはさまざまで、さまざまなセットアップがあります。つまり、一部の共通のセットアップがある一方で、正しいセットアップは1つではなく、すべてのセットアップが少し異なる場合があります。しかし、間違ったセットアップも多くあります。

## ダウンロードクライアントの処理

## Usenet

- Lidarrは、ダウンロードクライアントにダウンロードリクエストを送信し、設定したラベルまたはカテゴリ名と関連付けます。
  - 例: movies、tv、series、music など
- Lidarrは、そのカテゴリ名を使用するダウンロードクライアントのアクティブなダウンロードを監視します。これは、ダウンロードクライアントのAPIを介して監視されます。
- ダウンロードが完了すると、Lidarrはダウンロードクライアントによって報告された最終ファイルの場所を把握します。このファイルの場所は、メディアフォルダとは別の場所であればどこでも構いませんが、Lidarrからアクセスできる必要があります。
- Lidarrは、その完了したファイルの場所をスキャンし、Lidarrが使用できるファイルを検出します。ファイル名を解析して要求されたメディアと一致させることができれば、指定された仕様に従ってファイル名を変更し、指定されたメディアの場所に移動します。
- アトミックムーブ（インスタントムーブ）はデフォルトで有効になっています。完了したダウンロードディレクトリとメディアライブラリのファイルシステムとマウントは同じである必要があります。アトミックムーブが失敗するか、セットアップがハードリンクとアトミックムーブをサポートしていない場合、Lidarrはファイルをコピーしてからソースから削除します。これはI/Oが集中するためです。
- Lidarrの設定で「完了したダウンロードの処理 - 削除」オプションが有効になっている場合、ダウンロードから残ったファイルは、クライアントに削除/削除リクエストを送信してごみ箱またはリサイクルに送信されます。

## BitTorrent

- Lidarrは、ダウンロードクライアントにダウンロードリクエストを送信し、設定したラベルまたはカテゴリ名と関連付けます。
  - 例: movies、tv、series、music など
- Lidarrは、そのカテゴリ名を使用するダウンロードクライアントのアクティブなダウンロードを監視します。この監視は、ダウンロードクライアントのAPIを介して行われます。
- 完了したファイルは、ファイルをシードするために元の場所に残されます（シードの比率や時間はダウンロードクライアントまたはLidarr内の特定のダウンロードクライアントの設定で調整できます）。ファイルがメディアフォルダにインポートされると、Lidarrはファイルをハードリンク（サポートされている場合）またはコピー（ハードリンクがサポートされていない場合）します。
- ハードリンクはデフォルトで有効になっています。[ハードリンクを使用すると、追加のディスクスペースを使用しません。](https://trash-guides.info/Hardlinks/Hardlinks-and-Instant-Moves/)完了したダウンロードディレクトリとメディアライブラリのファイルシステムとマウントは同じである必要があります。ハードリンクの作成が失敗するか、セットアップがハードリンクをサポートしていない場合、Lidarrはファイルをコピーします。
- Lidarrの設定で「完了したダウンロードの処理 - 削除」オプションが有効になっている場合、Lidarrはトレントをクライアントから削除し、クライアントにトレントデータの削除を要求しますが、これはクライアントがシーディングが完了し、トレントが停止している（完了時に一時停止）場合にのみ行われます。

## ダウンロードクライアント

`設定 => ダウンロードクライアント`をクリックし、新しいダウンロードクライアントを追加するための<kb>+</kb>をクリックします。ダウンロードクライアントはすでに設定され、実行されている必要があります。

### サポートされているダウンロードクライアント

- サポートされているダウンロードクライアントのリストは、このセクションの[詳細情報（サポート）](/lidarr/supported#downloadclient)ページにあります。

追加するダウンロードクライアントを選択すると、接続の詳細を入力するためのポップアップボックスが表示されます。これらの詳細は、ほとんどのクライアントに対して同様です。ユーザー名やパスワードを求められる場合もありますし、新しいダウンロードを一時停止/開始状態で追加するかどうかを求められる場合もあります。

### Usenetクライアントの設定

- 名前 - Lidarr内のダウンロードクライアントの名前
- 有効化 - このダウンロードクライアントを有効にする
- ホスト - ダウンロードクライアントのURL
- ポート - ダウンロードクライアントのポート
- SSLを使用する - ダウンロードクライアントとの安全な接続を使用する。この一般的な間違いに注意してください。
- (高度なオプション) URLベース - URLに接頭辞を追加します。これはリバースプロキシで一般的に必要です。
- APIキー - クライアントに認証するためのAPIキー
- ユーザー名 - クライアントに認証するためのユーザー名（通常は必要ありません）
- パスワード - クライアントに認証するためのパスワード（通常は必要ありません）
- カテゴリ - \*Arrが使用するダウンロードクライアント内のカテゴリ。関連しないダウンロードがアクティビティに表示されないようにするために、カテゴリを設定することを強くお勧めします。
- 最近の優先度 - 最近リリースされたメディアのダウンロードクライアントの優先度
- 古い優先度 - 最近リリースされていないメディアのダウンロードクライアントの優先度
- (高度なオプション) クライアントの優先度 - ダウンロードクライアントの優先度。同じタイプ（torrent/usenet）のクライアントで同じ優先度を持つ場合、ラウンドロビンが使用されます。1が最も高い優先度で、50が最も低い優先度です。

### Torrentクライアントの設定

- 名前 - Lidarr内のダウンロードクライアントの名前
- 有効化 - このダウンロードクライアントを有効にする
- ホスト - ダウンロードクライアントのURL
- ポート - ダウンロードクライアントのポート。通常はWebGUIポートです。
- SSLを使用する - ダウンロードクライアントとの安全な接続を使用する。この一般的な間違いに注意してください。
- (高度なオプション) URLベース - URLに接頭辞を追加します。これはリバースプロキシで一般的に必要です。
- ユーザー名 - クライアントに認証するためのユーザー名
- パスワード - クライアントに認証するためのパスワード
- カテゴリ - \*Arrが使用するダウンロードクライアント内のカテゴリ。関連しないダウンロードがアクティビティに表示されないようにするために、カテゴリを設定することを強くお勧めします。
- インポート後のカテゴリ - リリースがダウンロードされてインポートされた後に設定するカテゴリ。完了したダウンロードの処理の削除が破損しますので、注意してください。
- 最近の優先度 - 最近リリースされたメディアのダウンロードクライアントの優先度
- 古い優先度 - 最近リリースされていないメディアのダウンロードクライアントの優先度
- 初期状態 - トレントの初期状態（Qbittorrentのみ: 強制的にすべてのシードのしきい値をバイパスします）
- (高度なオプション) - ダウンロードクライアントの優先度。同じタイプ（torrent/usenet）のクライアントで同じ優先度を持つ場合、ラウンドロビンが使用されます。1が最も高い優先度で、50が最も低い優先度です。

### Torrentクライアントのダウンロードの互換性を削除する

- Lidarrは、トレントが追加される際にその値をAPI経由で設定できるクライアントでのみ、シードの比率/時間を設定できます。シードの目標は、クライアント自体でグローバルに設定するか、各インデクサの\*Arrの設定でトラッカーごとに設定できます。以下の表は、クライアントの互換性に関する情報です。

|      クライアント       |                                比率                                 |                                   時間                                   |
| :---------------: | :------------------------------------------------------------------: | :----------------------------------------------------------------------: |
|       Aria2       |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |   ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical)   |
|      Deluge       |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |   ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical)   |
| Download Station  | ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical) |   ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical)   |
|       Flood       |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |     ![サポート](https://img.shields.io/badge/サポート-はい-success)     |
|     Hadouken      | ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical) |   ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical)   |
|    qBittorrent    |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |     ![サポート](https://img.shields.io/badge/サポート-はい-success)     |
|     rTorrent      |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |     ![サポート](https://img.shields.io/badge/サポート-はい-success)     |
| Torrent Blackhole | ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical) |   ![サポートされていません](https://img.shields.io/badge/サポート-いいえ-critical)   |
|   Transmission    |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   | ![アイドル制限](https://img.shields.io/badge/サポート-アイドル制限*-blue) |
|     uTorrent      |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |     ![サポート](https://img.shields.io/badge/サポート-はい-success)     |
|       Vuze        |   ![サポート](https://img.shields.io/badge/サポート-はい-success)   |     ![サポート](https://img.shields.io/badge/サポート-はい-success)     |

> ![アイドル制限](https://img.shields.io/badge/サポート-アイドル制限*-blue) - Transmissionは内部的にアイドル時間のチェックを行いますが、アイドル制限がトレントごとに設定されている場合、Lidarrはシーディング時間と比較します。これは、TransmissionのAPIの制限回避策として行われます。{.is-info}

## 完了したダウンロードの処理

- 完了したダウンロードの処理は、Lidarrがダウンロードクライアントからメディアをシリーズフォルダにインポートする方法です。

- 有効化（高度なグローバル設定） - ダウンロードクライアントから完了したダウンロードを自動的にインポートする
- 削除（クライアントごとの設定） - 完了したダウンロードを削除する（usenetの場合）または停止/完了（torrentの場合）
  - トレントの場合、ダウンロードクライアントはシードの目標に達した時点で一時停止する必要があります。また、シードの目標は上記の表に従ってLidarrでサポートされている必要があります。トレントは同じカテゴリに留まる必要もあります。

### 完了したダウンロードの削除

- Lidarrは、ダウンロードクライアントにダウンロードリクエストを送信し、設定したラベルまたはカテゴリ名と関連付けます。
- Lidarrは、そのカテゴリ名を使用するダウンロードクライアントのアクティブなダウンロードを監視します。これは、ダウンロードクライアントのAPIを介して監視されます。
- ダウンロードが完了すると、Lidarrはダウンロードクライアントによって報告された最終ファイルの場所を把握します。このファイルの場所は、メディアフォルダとは別の場所であればどこでも構いません。
- Lidarrは、その完了したファイルの場所をスキャンし、ビデオファイルを検出します。ビデオファイル名を解析してエピソードに一致させることができれば、指定された仕様に従ってファイル名を変更し、割り当てられたライブラリフォルダに移動します。
- ダウンロードから残ったファイルは、ごみ箱またはリサイクルに送信されます。

BitTorrentクライアントを使用してダウンロードする場合、プロセスは少し異なります。

- 完了したファイルは、シードするために元の場所に残されます。ファイルが割り当てられたライブラリフォルダにインポートされると、Lidarrはファイルをハードリンクしようとします。ハードリンクがサポートされていない場合はコピーします（ディスクスペースが2倍になります）。
- Lidarrの設定で「完了したダウンロードの処理 - 削除」オプションが有効になっている場合、Lidarrはトレントクライアントに元のファイルとトレントを削除するように要求しますが、これはクライアントがシーディングが完了し、トレントが同じカテゴリ（つまり、ポストインポートカテゴリを使用していない）である場合、およびトレントが一時停止（停止）している場合にのみ行われます。

### ダウンロードの処理に失敗した場合

- ダウンロードの処理に失敗した場合、SABnzbdとNZBGetのみと互換性があります。
- ダウンロードの処理に失敗した場合、Torrentには適用されず、そのような機能を追加する予定もありません。

- ダウンロードの処理に失敗した場合、いくつかのコンポーネントがあります。

- ダウンローダのチェック:
  - キュー - ダウンローダのキューで、パスワードで保護された（暗号化された）リリースが失敗したとマークされたものをチェックします
  - 履歴 - ダウンローダの履歴で失敗したものをチェックします（例: ブロックが不足して修復できない、または抽出に失敗した）
- Lidarrは、失敗したダウンロードを見つけると、次のことを行います。
  - Lidarrの履歴に失敗したイベントを追加します
  - 失敗したダウンロードをダウンロードクライアントから削除して、スペースを解放し、ダウンロードされたファイルをクリアします（オプション）
  - 代替ファイルを検索し始めます（オプション）
  - ブロックリスト（以前は 'ブラックリスト'）は、失敗した場合に自動的にnzbsをスキップすることを可能にします。これにより、そのnzbはLidarrによって自動的にダウンロードされなくなります（手動検索でダウンロードすることはできます）。
  - Lidarrのダウンロードクライアントの設定ページには、ダウンロードの失敗動作を制御する2つの高度なオプションがあります。現時点では、これらのオプションはデフォルトですべてオンになっています。

- 再ダウンロード - 失敗後に同じファイルを検索するかどうかを制御します
- (高度なオプション) 削除 - 失敗が検出されたときにダウンロードを自動的にダウンロードクライアントから削除するかどうか

## リモートパスのマッピング

- リモートパスマッピングは、単純なリモートパスを検索してローカルパスに置き換えるものです。これは、マージドローカル/リモートセットアップ（mergerfsなど）を使用している場合や、アプリケーションとダウンロードクライアントが同じサーバー上にない場合に主に使用されます。
- リモートパスマッピングは、ダウンロードクライアントが別のサーバー上の完了データのパスを報告している場合や、\*Arrがそのフォルダに対応していない方法で報告されている場合に使用されます。
- 一般的に、リモートパスマップは、ダウンロードクライアントがLinux上にあり、\*ArrがWindows上にある場合、またはその逆の場合にのみ必要です。リモートパスマップは、Dockerとネイティブクライアントを混在させる場合や、リモートサーバーを使用する場合にも必要になる可能性があります。
- リモートパスマップは、DUMBな検索/置換（リモートの値を見つけてホストごとにローカルの値に置き換える）です。
- パスのマッピングが期待どおりに機能していない場合、エラーメッセージに置換された値が含まれていない場合、典型的な解決策はマッピングを追加して削除することです。
- [TRaSHのチュートリアルを参照して、リモートパスマッピングに関する追加情報を確認してください](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)

# インポートリスト

## インポートリスト

## インポートリストの除外

## インポートリストの追加

# 接続

# タグ

# 一般

## アップデート

> もし \*Arr とダウンロードクライアントの両方がDockerコンテナである場合、リモートパスマップはほとんど必要ありません。[Dockerガイド](/docker-guide)を参照するか、[TRaSHのチュートリアル](https://trash-guides.info/hardlinks)に従ってください。
{.is-info}

# インポートリスト

> サポートされているリストの種類に関する情報は、このセクションの[詳細情報（サポート）](/lidarr/supported#lists)ページで確認できます。
{.is-info}

インポートリストを使用すると、SpotifyやLast.fmからLidarrにアイテムを追加することができます。これにより、予期しないアイテムがLidarrデータベースに大量に追加される可能性があるため、注意して使用してください。

<!-- ![importlists.png](/assets/readarr/importlists.png) -->

## インポートリスト

現在のリストを表示し、新しいリストを追加することができます。リストの追加方法については、以下で詳しく説明します。

## インポートリストの除外

ここに表示されるアイテムは、リストから追加されることが除外されており、どのリストからも追加されません。アイテムを削除するには、それをクリックします。

## インポートリストの追加

<kb>+</kb>をクリックした後、追加するリストの種類を選択します：

<!-- ![addlist.png](/assets/readarr/addlist.png) -->

この例では、Spotifyの保存されたアルバムリストを追加します。

<!-- ![bookshelflist.png](/assets/readarr/bookshelflist.png) -->

- 名前 - このリストの名前を入力します。
- 自動追加を有効にする - リストに含まれるアイテムを自動的にLidarrに追加します。

> これにより、そのアーティストのすべてのアルバムがLidarrに追加されます！

- モニター - 追加されたアイテムの監視レベルを選択します。有効なオプションは `なし`、`特定のアルバム`、`すべてのアーティストのアルバム` です。すべてのアルバムはLidarrに追加されますが、この選択に基づいて監視されるか監視されないかが決まります。
- ルートフォルダー - このリストから追加されるアーティストのルートフォルダーを選択します。
- 新しいアルバムの監視 - 追加されたアーティストの将来のアルバムに対してLidarrが行う操作を選択します。有効なオプションは `すべてのアルバム`、`なし`、`新しいアルバム` です。
- クオリティプロファイル - このリストから追加されるアーティストのクオリティプロファイルを選択します。
- メタデータプロファイル - このリストから追加されるアーティストのメタデータプロファイルを選択します。
- Lidarr タグ - このリストから追加されるアーティストに適用されるタグを選択します。

> ここに説明的なタグを追加することを強くお勧めします。そうしないと、これらのアイテムがLidarrに追加されたリストがわからず、一度追加されるとこの情報を再び取得することはできません！この情報はログに記録されません！

リストはデフォルトで24時間ごとに同期されますが、`System` => `Tasks` ページから手動でトリガーすることもできます。このプロセスをこれより早く自動化することはできません。

# 接続

> サポートされている接続タイプに関する情報は、このセクションの[詳細情報（サポート）](/lidarr/supported#notifications)ページで確認できます。
{.is-info}

# タグ

- Lidarrのタグセクションは、Lidarrのさまざまな側面をリンクするために使用されます。
- タグは、以下のような場合に特に便利です：

  - 遅延プロファイル
  - リリースプロファイル
  - インデクサー

- タグは、遅延プロファイル、リリースプロファイル、インデクサー、アーティスト/アルバムをリンクするために使用できます。
- 例えば：
  - 特定のアーティスト/アルバムが特定のインデクサーのみを使用するようにしたい場合、タグを作成し、アーティスト/アルバムとインデクサーにそのタグを割り当てます。
  - 特定のリリースプロファイルが特定の遅延プロファイルのみを使用するようにしたい場合、タグを作成し、リリースプロファイルと遅延プロファイルにそのタグを割り当てます。

> 注意：タグは「クオリティプロファイル」、「メタデータプロファイル」など、上記で言及されていない他の側面には影響しません。
{.is-info}

# 一般

## 更新

- (高度なオプション) ブランチ - 実行しているLidarrのブランチです。
  - [詳細については、このFAQエントリーを参照してください](/lidarr/faq#how-do-i-update-lidarr)
- 自動 - 更新を自動的にダウンロードしてインストールします。System: Updates からインストールすることもできます。注意：Windowsユーザーは常に自動的に更新されます。
- メカニズム - Lidarrの組み込みの更新プログラムまたはスクリプトを使用します。
  - 組み込み - Lidarr独自の更新プログラムを使用します。
  - スクリプト - Lidarrに更新スクリプトを実行させます。
  - Docker - Docker内部からLidarrを更新せず、新しい更新を持つブランドイメージをプルします。
- スクリプト - メカニズムがスクリプトに設定されている場合にのみ表示されます - 更新スクリプトへのパス
- 更新プロセス - Lidarrは更新ファイルをダウンロードし、その整合性を確認し、一時的な場所に展開し、選択した方法を呼び出します。更新プロセスは、Lidarrが実行されているユーザーと同じユーザーで実行されます。Lidarrファイルを更新する権限だけでなく、Lidarrの停止/開始も必要です。
- 組み込み - 組み込みの方法では、Lidarrのファイルと設定をバックアップし、Lidarrを停止し、インストールを更新し、Lidarrを開始します。システムがLidarrの停止を処理できず、自動的に再起動しようとする場合は、代わりにスクリプトを使用することが最善です。失敗した場合、以前のバージョンのLidarrが再起動されます。
- スクリプト - スクリプトは組み込みの更新プログラムと同じように処理するはずです。サービスの停止と開始を処理する必要がある場合（upstart/launchdなど）、ここで行う必要があります。