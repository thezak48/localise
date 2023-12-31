---
title: Radarrのトラブルシューティング
description: Radarrのトラブルシューティングに関する情報です。ログファイルの取得方法、検索のトラブルシューティングと一般的な問題、ダウンロード/インポートのトラブルシューティングと一般的な問題について説明します。
published: true
date: 2023-08-12T09:40:45.369Z
tags: radarr, トラブルシューティング
editor: markdown
dateCreated: 2021-08-03T21:05:52.988Z
---

# 目次

- [目次](#目次)
- [ヘルプを求める](#ヘルプを求める)
- [ログとログファイル](#ログとログファイル)
  - [標準ログの場所](#標準ログの場所)
  - [アップデートログの場所](#アップデートログの場所)
  - [ログの共有](#ログの共有)
  - [トレース/デバッグログ](#トレースデバッグログ)
  - [ログのクリア](#ログのクリア)
- [複数のログファイル](#複数のログファイル)
- [アップデートの失敗からの復旧](#アップデートの失敗からの復旧)
  - [問題の特定](#問題の特定)
    - [データベースディスクイメージが破損しています](#データベースディスクイメージが破損しています)
    - [マイグレーションの問題](#マイグレーションの問題)
    - [UIマイグレーションの問題](#UIマイグレーションの問題)
    - [パーミッションの問題](#パーミッションの問題)
  - [問題の解決](#問題の解決)
    - [マイグレーションの問題](#マイグレーションの問題)
    - [パーミッションの問題](#パーミッションの問題)
    - [手動でのアップグレード](#手動でのアップグレード)
- [ダウンロードとインポート](#ダウンロードとインポート)
  - [ダウンロードクライアントのテスト](#ダウンロードクライアントのテスト)
  - [ダウンロードのテスト](#ダウンロードのテスト)
  - [インポートのテスト](#インポートのテスト)
  - [一般的な問題](#一般的な問題)
    - [ダウンロードクライアントのWebUIが有効になっていない](#ダウンロードクライアントのwebuiが有効になっていない)
    - [誤った設定でSSLを使用している](#誤った設定でSSLを使用している)
    - [Windowsで共有が表示されない](#windowsで共有が表示されない)
    - [マップされたネットワークドライブは信頼性がありません](#マップされたネットワークドライブは信頼性がありません)
    - [Dockerとユーザー、グループ、所有権、パーミッション、パス](#dockerとユーザーグループ所有権パーミッションパス)
    - [リモートパスマッピング](#リモートパスマッピング)
      - [リモートマウントまたはリモート同期（Syncthing）](#リモートマウントまたはリモート同期syncthing)
    - [ライブラリフォルダのパーミッション](#ライブラリフォルダのパーミッション)
    - [ダウンロードフォルダのパーミッション](#ダウンロードフォルダのパーミッション)
    - [ダウンロードフォルダとライブラリフォルダが異なるフォルダではありません](#ダウンロードフォルダとライブラリフォルダが異なるフォルダではありません)
    - [誤ったカテゴリ](#誤ったカテゴリ)
    - [パックされたトレント](#パックされたトレント)
    - [繰り返しダウンロード](#繰り返しダウンロード)
    - [Usenetのダウンロードがインポートされない](#usenetのダウンロードがインポートされない)
    - [ダウンロードクライアントがアイテムをクリアしてしまう](#ダウンロードクライアントがアイテムをクリアしてしまう)
    - [ダウンロードがライブラリアイテムにマッチングされない](#ダウンロードがライブラリアイテムにマッチングされない)
    - [接続がタイムアウトしました](#接続がタイムアウトしました)
  - [問題がリストにない場合](#問題がリストにない場合)
- [検索、インデクサ、トラッカー](#検索インデクサトラッカー)
  - [トレースログを有効にする](#トレースログを有効にする)
  - [インデクサまたはトラッカーのテスト](#インデクサまたはトラッカーのテスト)
  - [検索のテスト](#検索のテスト)
  - [一般的な問題](#一般的な問題-1)
    - [トラッカーにRawSearch Capsが必要です](#トラッカーにrawsearch-capsが必要です)
    - [メディアが監視されていません](#メディアが監視されていません)
    - [誤ったカテゴリ](#誤ったカテゴリ-1)
    - [クエリが成功しましたが、結果が返されませんでした](#クエリが成功しましたが結果が返されませんでした)
    - [誤った結果](#誤った結果)
    - [結果が見つかりません](#結果が見つかりません)
    - [証明書の検証](#証明書の検証)
    - [レート制限に達しました](#レート制限に達しました)
    - [IP Ban](#ip-ban)
    - [年が一致しません](#年が一致しません)
    - [年がありません](#年がありません)
    - [Jackettの/allエンドポイントを使用する](#jackettのallエンドポイントを使用する)
    - [NZBHydra2を単一のエントリとして使用する](#nzbhydra2を単一のエントリとして使用する)
    - [問題がリストにない場合](#問題がリストにない場合-1)
  - [エラー](#エラー)
    - [The underlying connection was closed: An unexpected error occurred on a send](#the-underlying-connection-was-closed-an-unexpected-error-occurred-on-a-send)
    - [The request timed out](#the-request-timed-out)
    - [問題がリストにない場合](#問題がリストにない場合-2)

# ヘルプを求める

ヘルプが必要ですか？大丈夫です、誰でも時にはヘルプが必要です。以下の方法でリアルタイムのヘルプを受けることができます。

- [<i class="fab fa-discord"></i>&emsp;Discord *公式Radarr Discord*](https://radarr.video/discord)
- [<i class="fab fa-reddit"></i>&emsp;Reddit *公式Radarr Subreddit*](https://reddit.com/r/radarr)
{.links-list}

ただし、投稿する前に、ヘルプを求めるためのリクエストが最善のものであることを確認してください。問題を明確に説明し、OS/ディストリビューション、.NETのバージョン、Radarrのバージョン、ダウンロードクライアントとそのバージョンなど、セットアップに関する情報を簡単に説明してください。**[Docker](https://www.docker.com/)を使用している場合は、まず[Dockerガイド](/docker-guide)を実行して、一般的で頻繁なパス/パーミッションの問題を解決してください。それ以外の場合は、[docker compose](/docker-guide#docker-compose)を手元に用意してください。[Docker Composeの生成方法](https://trash-guides.info/compose)** すでに試したこと、調査したことについて教えてください。問題を再現し、[ログとログファイルのセクション](#ログとログファイル)を使用してログをトレースレベルに設定し、問題を再現し、関連するコンテキストをパスビンに貼り付け、そのリンクを投稿に含めてください。問題をハイライトするためにスクリーンショットを含めることもできます。

私たちが知っていることが多ければ多いほど、あなたを助けることが容易になります。

# ログとログファイル

以下の一般的なトラブルシューティングの問題も確認することをお勧めします：
- [ダウンロードとインポートの一般的な問題](#一般的な問題)
- [インデクサとトラッカーの検索の一般的な問題](#一般的な問題-1)
{.links-list}

デバッグログが必要な場合、ログには `debug` が含まれ、トレースログが必要な場合は `trace` が含まれます。提供するログがこれらのいずれも含まれていない場合は、要求されたログではありません。

- 要求されていない限り、ログファイル全体を共有しないでください。
- 要求されていない限り、ログを直接Discordにアップロードしたり、テキストの壁として貼り付けたりしないでください。
- ログを添付ファイルやzipアーカイブなどの形式で共有しないでください。以下で説明するサービスを介して共有するのはテキストのみです。

有用なログを提供するための手順：

> RSSの更新など、スパムの多いタスクが実行されていないことを確認してください。
{.is-warning}

1. [ログレベルをトレースに設定する（設定 => 一般 => ログレベルまたは設定ファイルの編集）](#トレースデバッグログ)
2. [ログをクリアする（システム => ログ => ログをクリアまたはログフォルダ内のすべてのログを削除）](#ログのクリア)
3. 問題を再現する（問題が発生していることを再現する）
4. UIまたはファイルシステム上のログファイル（radarr.trace.txt）を開き、関連するコンテキストを見つける
5. 問題の前、問題そのもの、問題の後ろの大きなチャンクをコピーする
6. [Gist](https://gist.github.com/)、[0bin（**カラーリングを無効にすることを忘れないでください**）](https://0bin.net/)、[PrivateBin](https://privatebin.net/)、[Notifiarr PrivateBin](http://logs.notifiarr.com/)、[Hastebin](https://hastebin.com/)、[UbuntuのPastebin](https://pastebin.ubuntu.com/)などのサイトを使用して、上記でコピーしたログを共有する

**注意事項:**
- **[pastebin.com](https://pastebin.com)はログをブロックする傾向があるため使用しないでください。
- [pastebin.pl](https://pastebin.pl)はサイトに頻繁にアクセスできないため使用しないでください。
- [JustPasteIt](https://justpaste.it/)はログの確認を容易にすることができないため使用しないでください。
- ログをファイルとしてアップロードしないでください。
- ログをGoogle Drive、Dropbox、その他のサイトで共有しないでください。
- ログをアーカイブ（zip、tar（tarボール）、7zipなど）しないでください。
- コンソール出力、Dockerコンテナの出力、アプリケーションログ以外のものを共有しないでください。

**重要な注意事項:**
- [0bin](https://0bin.net/)を使用する場合は、カラーリングを無効にし、読み終わった後に破棄しないようにしてください。

- また、特定のエントリを古いログファイルから探す場合、どのログファイルにあるかわからない場合は、N++を使用することができます。Notepad++の「ファイル内検索」機能を使用して必要な古いログファイルを検索できます。
- **Unixの場合のみ:** 特定のエントリを古いログファイルから探す場合、どのログファイルにあるかわからない場合は、grepを使用することができます。たとえば、映画/番組/書籍/曲/インデクサ「Shooter」に関する情報を検索したい場合は、次のコマンドを実行します。`grep -inr -C 100 -e 'Shooter' /path/to/logs/*.trace*.txt` もし[Appdataディレクトリ](/radarr/appdata-directory)がホームフォルダにある場合は、次のように実行します。`grep -inr -C 100 -e 'Shooter' /home/$User/.config/logs/*.trace*.txt`

```none

    * 各フラグの機能は以下の通りです
    * -i: 大文字と小文字を区別しない
    * -n: 行番号を表示する
    * -r: パス内のすべてのファイルを再帰的にチェックする
    * -C: 検索された行の前後の行数を指定する
    * -e: 検索するパターン

```

## 標準ログの場所

ログファイルは、Radarrの[Appdataディレクトリ](/radarr/appdata-directory)内のlogs/フォルダにあります。また、UIからもログファイルにアクセスできます。システム => ログ => ファイル。

> 注意: UIのログ（"イベント"）テーブルはログファイルとは異なり、あまり役に立ちません。ログが要求された場合は、ログファイルからコピー/貼り付けしてください。
{.is-info}

## アップデートログの場所

アップデートログファイルは、Radarrの[Appdataディレクトリ](/radarr/appdata-directory)内のUpdateLogs/フォルダにあります。

## ログの共有

ログは長くて読みにくいため、フォーラムやRedditの投稿の一部として共有することは避け、Discordではスパムになります。そのため、[Pastebin](https://pastebin.ubuntu.com/)、[Hastebin](https://hastebin.com/)、[Gist](https://gist.github.com)、[0bin](https://0bin.net)、または類似のパステビンサイトを使用してください。通常、ファイル全体は必要ありません。問題/エラーの前後のコンテキストを十分に含めて共有してください。スパムの多いタスク（RSSの同期やライブラリの更新など）が終了するのを忘れないでください。

## トレース/デバッグログ

ログレベルは、設定 => 一般 => ロギングで変更できます。Radarrを再起動する必要はありません。この変更はログファイルのみに影響を与えます。ログデータベースには影響しません。最新のデバッグ/トレースログファイルは、それぞれ `radarr.debug.txt` と `radarr.trace.txt` という名前です。

ログレベルを設定するためにUIにアクセスできない場合は、AppDataディレクトリのconfig.xmlを編集して、LogLevelの値をInfoではなくDebugまたはTraceに設定することで設定できます。

```xml
 <Config>
  [...]
  <LogLevel>debug</LogLevel>
  [...]
 </Config>
```

## ログのクリア

ログファイルとログデータベースは、UIのシステム => ログ => ファイルおよびシステム => ログ => 削除（ゴミ箱アイコン）から直接クリアできます。

# 複数のログファイル

Radarrは、1MBまでのローリングログファイルを使用します。現在のログファイルは常に `radarr.txt` であり、他のファイル `radarr.0.txt` は次に新しいものです（数値が大きいほど古いものです）。このログファイルには `fatal`、`error`、`warn`、`info` のエントリが含まれます。

デバッグログレベルが有効になっている場合、追加の `radarr.debug.txt` ローリングログファイルが存在します。このログファイルには `fatal`、`error`、`warn`、`info`、`debug` のエントリが含まれます。通常、40時間分のログをカバーしています。

トレースログレベルが有効になっている場合、追加の `radarr.trace.txt` ローリングログファイルが存在します。このログファイルには `fatal`、`error`、`warn`、`info`、`debug`、`trace` のエントリが含まれます。トレースの詳細さにより、最大でも数時間分のログしかカバーしません。

# アップデートの失敗からの復旧

- アップグレード時の問題を防ぐために、最善の努力をしていますが、問題が発生した場合は、この手順に従ってインストールを復旧します。
- このセクションでは、アップデート後の一般的な問題についても説明します。

## 問題の特定

- アップデート後にアプリケーションが起動しない場合は、まず[アップデートログ](#アップデートログの場所)を確認し、アップデートが正常に完了したかどうかを確認してください。それでも問題が解決しない場合は、起動する前に通常のアプリケーションログファイルを確認し、[ログ](/radarr/settings#logging)と[ログファイル](/radarr/system#log-files)を使用してログファイルを見つけ、ログレベルを上げてください。
- 最も頻繁に発生する問題は、アプリケーションがインストールされているシステムが `/tmp` ディレクトリをいじり、アップグレード中に重要な \*Arr ファイルを削除したため、アップグレードとロールバックの両方が失敗することです。この場合は、単に既存の破損したインストールの上に再インストールしてください。

### データベースディスクイメージが破損しています

- [FAQエントリ](/radarr/faq#i-am-getting-an-error-database-disk-image-is-malformed)を参照してください。

### マイグレーションの問題

- マイグレーションエラーは同一ではありませんが、以下は例です。

```none
14-2-4 18:56:49.5|Info|MigrationLogger|\*\*\* 36: update\_with\_quality\_converters migrating \*\*\*

14-2-4 18:56:49.6|Error|MigrationLogger|SQL logic error or missing database duplicate column name: Items

While Processing: "ALTER TABLE "QualityProfiles" ADD COLUMN "Items" TEXT"

```

### UIマイグレーションの問題

- [サポートされていないバージョン/ブランチ](/radarr/faq#can-i-switch-between-branches)の切り替えを行うと、以下のようなマイグレーションの問題が発生する場合があります。解決策は、[以前のバージョンのブランチまたはより高いバージョンに戻る](/radarr/faq#how-do-i-update-radarr)か、現在のバージョンの[バックアップを復元](/radarr/faq#how-do-i-backuprestore-radarr)することです。

![radarr-migration-error-ui.png](/assets/radarr/radarr-migration-error-ui.png)

### パーミッションの問題

- パーミッションの問題は、アプリケーションが関連する一時フォルダやアプリのバイナリフォルダにアクセスできないために発生します。アプリケーションが実行されるユーザー/グループが適切なアクセス権を持つように、パーミッションを修正してください。

- Synologyユーザーは、このSynologyのバグ「パス '/proc/{some number}/maps' へのアクセスが拒否されました」と遭遇することがあります。

- Synologyユーザーは、特定のNASで`/tmp`の容量不足にも遭遇することがあります。アプリのために異なる`/tmp`パスを指定する必要があります。この問題の解決には、SynoCommunityまたは他のSynologyサポートチャンネルのヘルプが必要です。

## 問題の解決

### 移行の問題

移行の問題が発生した場合、すぐに対処することはできません。もし問題が特定のユーザーに固有のものである場合（またはまだ投稿がない場合）、[私たちのサブレディット](https://reddit.com/r/radarr)で投稿を作成するか、[discord](https://radarr.video/discord)に参加してください。同じ問題を抱えている他のユーザーがいる場合は、私たちが対応していることを保証します。

> 安定版で`nightly`のデータベースを使用しようとしていないことを確認してください。ブランチの切り替えはお勧めしません。{.is-info}

### 権限の問題

- `/tmp`とアプリケーションのインストールディレクトリの両方に対して、アプリケーションが実行されるユーザー/グループがアクセス（読み取りおよび書き込み）できるように、権限を修正してください。

- `/proc/###/maps`の問題でSonarrや他の\*Arrアプリケーションが停止しているSynologyユーザーは、アプリケーションの更新を行うことで解決することができます。これはSynoCommunityパッケージの問題です。

### 手動でのアップグレード

ウェブサイトから最新のリリースを入手してください。

アップデート（.exe）をインストールするか、既存のインストールに内容を展開（.zip）し、通常どおりRadarrを実行してください。

# ダウンロードとインポート

ダウンロードとインポートは、*ほとんどの*ユーザーが問題を抱える場所です。大まかな視点から見ると、Radarrはダウンロードクライアントと通信し、ダウンロードしたファイルにアクセスする必要があります。サポートされているダウンロードクライアントの種類はさまざまで、さらに多様なセットアップがあります。つまり、一部の*一般的な*セットアップがありますが、*正しい*セットアップはなく、すべてのセットアップは少し異なる可能性があります。

> **最初のステップは、ログをトレースレベルに設定することです。ログの調整と検索の詳細については、[ログとログファイル](#logging-and-log-files)を参照してください。その後、問題を再現し、その時間枠のトレースレベルのログを使用して問題を調査します。**誰かがあなたを助けている場合は、前後の文脈を[pastebin](https://0bin.net)、[Gist](https://gist.com)、または類似のサイトに表示してください。全体のファイルである必要はありませんし、エラーだけではありません。また、ログファイルにスパムを送信するタスクが実行されていない状態で問題を再現する必要があります。
{.is-danger}

ヘルプを求める際には、必要な詳細を提供できるように、[ヘルプの要求](#asking-for-help)を必ず読んでください。

## ダウンロードクライアントのテスト

ダウンロードクライアントが実行されていることを確認してください。まず、ダウンロードクライアントをテストしてください。うまくいかない場合、トレースレベルのログに詳細が表示されます。ブラウザに入力できるURLを見つけて、それが機能するかどうか確認してください。接続の問題かもしれません。間違ったIP、ホスト名、ポート、またはファイアウォールによるアクセスのブロックの可能性があります。ユーザー名、パスワード、またはAPIキーが間違っている場合など、明らかな認証の問題かもしれません。一部のシードボックスでは、ダウンロードクライアントの実際のポートではなく、https、ポート443、およびURLベース（詳細オプション）の使用が必要な場合があります。

## ダウンロードのテスト

次に、ダウンロードを試してみましょう。映画を選んで手動で検索を実行します。そのファイルのうちの1つをダウンロードしようとしてください。ダウンロードクライアントに送信されますか？正しいカテゴリに表示されますか？アクティビティに表示されますか？トレースレベルのログには表示されますか（監視中のダウンロードの更新と監視中のダウンロードの処理タスクが約1分ごとに実行されます）？そのタスク中に正しく解析されますか？キューに入ったダウンロードには適切な名前が付いていますか？一部のインデクサ/トラッカーではIDで検索されるため、認識できない名前でキューに入ることがあります。

## インポートのテスト

インポートの問題は、ほとんどの場合、アクティビティにエラーが表示されるアイテムとして現れます。アクティビティに表示されない場合は、まずこの問題に焦点を当てる必要がありますので、戻って解決してください。ほとんどのインポートエラーは*権限*の問題です。ダウンロードフォルダー内で読み取りおよび書き込みができるようにする必要があります。場合によっては、ライブラリフォルダーの権限も原因となる場合があるため、両方を確認してください。

パスの問題も発生する可能性がありますが、通常は一般的なセットアップではあまり一般的ではありません。パスの問題を理解するためのキーは、がダウンロードクライアントからダウンロードのパスを取得することです。これは、ダウンロードクライアントが別のシステム（おそらく別のOS）で実行されている場合など、よりユニークな使用例で問題となることがあります。Dockerのセットアップでは、ボリュームがうまく設定されていない場合にも問題が発生することがあります。リモートパスマップは、シードボックスのセットアップなど、制御できない場合に有効な解決策です。Dockerのセットアップでは、パスを修正することがより良いオプションです。

## 一般的な問題

以下は一般的な問題のいくつかです。

### ダウンロードクライアントのWebUIが有効になっていない

Radarrは、ダウンロードクライアントとの通信にAPIを使用し、クライアントのWebUIを介してアクセスします。クライアントのWebUIが有効になっていることを確認し、使用しているポートが他のクライアントポートやシステムで使用されているポートと競合していないことを確認してください。

### SSLが使用され、正しく構成されていない

インスタンスとダウンロードクライアントの両方をローカルネットワークで使用している場合、SSL暗号化がオンになっていないことを確認してください。詳細については、[SSL FAQエントリ](/radarr/faq#invalid-certificate-and-other-HTTPS-or-SSL-issues)を参照してください。

### Windowsで共有が表示されない

Windowsサービスのデフォルトユーザーは`LocalService`であり、通常は共有にアクセスできません。サービスを編集し、自分自身のユーザーとして実行するように設定してください。詳細については、FAQエントリの[リモートサーバー上のファイルが表示されない理由](/radarr/faq#why-cant-i-see-my-files-on-a-remote-server)を参照してください。

### マップされたネットワークドライブは信頼性がない

`X:\`のようなマップされたネットワークドライブは便利ですが、UNCパス（`\\server\share`のような）ほど信頼性がありません。また、ログイン前には利用できません。必要に応じて、セットアップとダウンロードクライアントをUNCパスを使用するように構成してください。ライブラリが共有にある場合は、ルートフォルダーがUNCパスを使用していることを確認してください。ダウンロードクライアントが共有に送信する場合は、ダウンロードパスをダウンロードクライアントから取得する必要があるため、UNCパスを構成する必要があります。マップされたネットワークドライブを自分自身で使用することは問題ありませんが、自動化には使用しないでください。

### Dockerとユーザー、グループ、所有権、権限、パス

Dockerは、間違いやすい複雑なレイヤーを追加しますが、それでも機能するセットアップを作成することができますが、さまざまな問題が発生する可能性があります。ここではそれらについて説明する代わりに、環境に実装できるように、ユーザー、グループ、所有権、権限、パスについて説明したこのウィキ記事を読んでください。これは特定のDockerシステムに固有ではなく、高レベルでの説明です。

### リモートパスマッピング

RadarrをDockerで使用し、ダウンロードクライアントを非Dockerで使用している場合（またはその逆）、またはプログラムを異なるサーバーに配置している場合は、リモートパスマップが必要になる場合があります。

ログには次のような内容が表示されます。

```none
2022-02-03 14:03:54.3|Error|DownloadedMovieImportService|Import failed, path does not exist or is not accessible by Radarr: /volume3/data/torrents/movies/The.Orville.2022.1080p.WEB.H264-GGEZ[rarbg]. Ensure the path exists and the user running Radarr has the correct permissions to access this file/folder
```

したがって、`/volume3/data`はRadarrのコンテナ内に存在しないか、アクセスできないことを意味します。

- [設定 => ダウンロードクライアント => リモートパスマッピング](/radarr/settings#remote-path-mappings)
- リモートパスマッピングは、ダウンロードクライアントが別のサーバー上の完了したデータのパスを報告している場合、または\*Arrがそのフォルダーに対応していない方法で報告している場合に使用されます。
- 一般的に、ダウンロードクライアントがLinux上にあり、\*ArrがWindows上にある場合、またはその逆の場合にのみリモートパスマップが必要です。リモートパスマップは、DUMBな検索/置換（リモートの値を見つけて、指定されたホストのローカルの値に置き換える）です。
- パスのマッピングに関するエラーメッセージにREPLACEDの値が含まれていない場合、パスマッピングが期待どおりに機能していない可能性があります。通常の解決策は、マッピングを追加および削除することです。
- [リモートパスマッピングに関する詳細な情報については、TRaSHのチュートリアルを参照してください](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)

> \*Arrとダウンロードクライアントの両方がDockerコンテナである場合、リモートパスマップはほとんど必要ありません。[Dockerガイド](/docker-guide)を確認するか、[TRaSHのチュートリアル](https://trash-guides.info/hardlinks)に従うことをお勧めします。
{.is-info}

#### リモートマウントまたはリモート同期（Syncthing）

- ダウンロード中に常に同期される必要があります。また、ローカルの同期先は、\*Arrのインポート時にハードリンク可能である必要があります。つまり、同じファイルシステムであり、同じように見える必要があります。
  - 不完全なものと完全なものの両方を含む一般的なフォルダーで同期します。
  - ライブラリと同じファイルシステムであり、同じように見える場所に同期します（Dockerとネットワーク共有を使用すると、これを誤って設定することがよくあります）。
  - ダウンロードクライアントが移動を行うと、同期がローカルに反映されます。これにより、ダウンロードが「完了」したと宣言される前に、ほとんどのファイルがすでに「そこ」にある状態になります（まだダウンロード中であっても）。その後、ハードリンクを使用する必要があります。インポートが完了する前でも、ダウンロードが完了するまでハードリンクが可能であるため、問題ありません。
  - これにより、ダウンロード中は常に同期され、トレントクライアントがtvサブフォルダーに移動すると、同期がそれを反映します。これにより、ダウンロードはほとんど完了している状態になります。完全に完了していない場合でも、ハードリンクが可能であるため、問題ありません。
  - （オプション - 該当する場合および/または必要な場合（例：リモートUsenetクライアント））インポート/ダウンロード/アップグレード時にカスタムスクリプトを設定して、リモートファイルを削除します。
- リモート同期の代わりに、リモートマウントの設定は非常に複雑ではありませんが、通常は遅くなります。
  - sshfsや他のネットワークファイルシステムプロトコルを使用して、リモートストレージをマウントします。
  - \*Arrが実行されるユーザーとグループが読み取りまたは書き込みアクセス権を持っていることを確認してください。
  - リモートパスマップを構成して、REMOTEパスを見つけて、それをLOCALの値に置き換えるようにします。

### ライブラリフォルダーの権限

ログは次のようになります。

```none
2022-02-28 18:51:01.1|Error|DownloadedMovieImportService|Import failed, path does not exist or is not accessible by Radarr: /data/media/Movie Name (2010). Ensure the path exists and the user running Radarr has the correct permissions to access this file/folder
```

*宛先*の権限と所有権を確認するのを忘れないでください。ダウンロードの所有権と権限にこだわりすぎることが簡単であり、通常は権限に関連する問題の原因ですが、*宛先*も原因となる可能性があります。宛先フォルダーが存在することを確認してください。宛先の*ファイル*がすでに存在していないか、削除またはごみ箱に移動できないかを確認してください。所有権と権限が、ダウンロードしたファイルのコピー、ハードリンク、または移動を許可するようになっていることを確認してください。実行するユーザーまたはグループは、ルートフォルダーを読み取りおよび書き込みできる必要があります。

- Windowsユーザーの場合、これはサービスとして実行されているためです：
  - Windowsサービスはデフォルトで「Local Service」アカウントで実行されます。このアカウントは、通常、手動でアクセス許可が割り当てられていない限り、ユーザーのホームディレクトリにアクセスできません。これは、ホームディレクトリにダウンロードを設定しているダウンロードクライアントを使用している場合に特に関係があります。
  - 「Local Service」は一般に非常に制限された権限を持っています。したがって、ユーザーがログインしたままであれば、システムトレイアプリケーションとしてアプリをインストールすることをお勧めします。インストーラーでこのオプションが提供されます。サービスからトレイアプリに変換する方法については、FAQを参照してください。

- Synologyユーザーは、[SynoCommunityのパッケージの権限管理に関する記事](https://github.com/SynoCommunity/spksrc/wiki/Permission-Management)を参照してください。

- Windows以外の場合：NFSマウントを使用している場合は、`nolock`が有効になっていることを確認してください。
- SMBマウントを使用している場合は、`nobrl`が有効になっていることを確認してください。

### ダウンロードフォルダーの権限

ログは次のようになります。

```none
2022-02-28 18:51:01.1|Error|DownloadedMovieImportService|Import failed, path does not exist or is not accessible by Radarr: /data/downloads/The.Movie. Ensure the path exists and the user running Radarr has the correct permissions to access this file/folder
```

*ソース*の権限と所有権を確認するのを忘れないでください。宛先の所有権と権限にこだわりすぎることが簡単であり、通常はソースの所有権と権限が問題の原因です。ソースフォルダーが存在することを確認してください。所有権と権限が、ダウンロードされたファイルのコピー/ハードリンクまたはコピー+削除/移動を許可するようになっていることを確認してください。実行するユーザーまたはグループは、ダウンロードフォルダーを読み取りおよび書き込みできる必要があります。

- Windowsユーザーの場合、これはサービスとして実行されているためです：
  - Windowsサービスはデフォルトで「Local Service」アカウントで実行されます。このアカウントは、通常、手動でアクセス許可が割り当てられていない限り、ユーザーのホームディレクトリにアクセスできません。これは、ホームディレクトリにダウンロードを設定しているダウンロードクライアントを使用している場合に特に関係があります。
  - 「Local Service」は一般に非常に制限された権限を持っています。したがって、ユーザーがログインしたままであれば、システムトレイアプリケーションとしてアプリをインストールすることをお勧めします。インストーラーでこのオプションが提供されます。サービスからトレイアプリに変換する方法については、FAQを参照してください。

- Synologyユーザーは、[SynoCommunityのパッケージの権限管理に関する記事](https://github.com/SynoCommunity/spksrc/wiki/Permission-Management)を参照してください。

- Windows以外の場合：NFSマウントを使用している場合は、`nolock`が有効になっていることを確認してください。
- SMBマウントを使用している場合は、`nobrl`が有効になっていることを確認してください。

### ダウンロードフォルダーとライブラリフォルダーが同じフォルダーではない

ダウンロードクライアントは、\*Arrがアクセスできるフォルダーにダウンロードする必要があります。また、それはルート/ライブラリフォルダーではない必要があります。別々のダウンロードフォルダーからライブラリフォルダーにインポートする必要があります。

直接ルートフォルダーにダウンロードしないでください。また、ダウンロードクライアントの完了フォルダーまたは不完全なフォルダーとしてルートフォルダーを使用しないでください。

> ダウンロードフォルダーとルート/ライブラリフォルダーは別々にする必要があります
{.is-warning}

### カテゴリが間違っている

Radarrは、自分自身のダウンロードのみを処理しようとするため、カテゴリを使用するように設定する必要があります。正しいカテゴリを持たないまま追加されることはまれですが、それは起こり得ます。手動でトレントを追加して処理したい場合は、正しいカテゴリを設定する必要があります。いつでも設定できます。はダウンロードを1分ごとに処理しようとします。

### 圧縮されたトレント

ログには次のようなエラーが表示されます。

```none
No files found are eligible for import
```

トレントが`.rar`ファイルで圧縮されている場合、展開を設定する必要があります。私たちは[Unpackerr](https://github.com/unpackerr/unpackerr)をお勧めします。これは、正しく展開するためのものです：破損した部分的なインポートを防ぎ、インポート後に展開されたファイルをきれいにします。

また、エラーが表示される場合は、フォルダーに有効なメディアファイルがない場合もあります。

### 繰り返しのダウンロード

繰り返しダウンロードの原因はいくつかありますが、そのうちの1つはカスタムフォーマットに関連しています。リリース名がカスタムフォーマットと一致する可能性がありますが、ダウンロードファイルは一致しません。これにより、アップグレードのように見えて何度もアイテムをダウンロードし続けることになります。カスタムフォーマットをリネームスキーマに含めることで、この問題を回避できる場合があります（リネームにカスタムフォーマットを含めるようにカスタムフォーマットを有効にし、リネームスキーマにカスタムフォーマットを追加します）。

また、ダウンロードが実際にはインポートされず、キューから消えてしまうため、新しいダウンロードが永遠に取得されずにいます。この場合は、他の一般的な問題やトラブルシューティング手順を参照してください。

### Usenetのダウンロードがインポートされない

RadarrはSABnzbdとNZBGetの最新の60件のダウンロードのみを参照するため、履歴を保持している場合、大量のキューでインポートの問題が発生すると、ダウンロードが静かに見落とされてインポートされません。これを回避するためには、完了および失敗したダウンロードハンドラの下で「削除」を有効にすることが最善の方法です。NZBGetでは、これによりアイテムが「非表示」の履歴に移動されます。残念ながら、SABnzbdには類似の機能はありません。そこで、nzbバックアップフォルダを使用することができます。

### ダウンロードクライアントがアイテムをクリアしてしまう

ダウンロードクライアントは、ダウンロードの削除には責任を持つべきではありません。Usenetクライアントは、履歴からダウンロードを削除しないように設定する必要があります。Torrentクライアントは、シーディングが終了したらトレントを削除するのではなく、一時停止または停止するように設定する必要があります。これは、Radarrがインポートするアイテムを知るためにダウンロードクライアントと通信するためです。したがって、ダウンロードが削除されると、インポートするものがなくなります... ファイルがいっぱいのフォルダがあってもです。

SABnzbdでは、これは「History Retention」設定で処理されます。

### ダウンロードがライブラリアイテムにマッチングできない

さまざまな理由で、ダウンロードが取得された後に解析できなくなることがあります。Activity => Options => Show Unknown（最近のビルドではデフォルトで有効になっています）を使用すると、\*Arrのダウンロードクライアントカテゴリ内でそれ以外の無視された/すでにインポートされたアイテムが表示されます。これらは通常、手動でマッピングしてインポートする必要があります。

理由には以下が含まれます：
- 映画名に`:`が含まれており、TMDbには`-`または`:`を` `に置き換えた代替タイトルがない場合
- ファイル名に必要な年が欠落している場合
- AKAまたは奇妙な複数の名前；Radarrはこれらに対して限定的なサポートしか提供していません
- ファイル名が複数の映画に一致する場合
- インデクサからのリリース名またはリリースIDがファイル名と一致しない場合

これは、ダウンロードクライアントにリリースがあるが、そのメディアアイテム（映画/エピソード/本/曲）がアプリケーションに存在しない場合にも発生する可能性があります。

### The underlying connection was closed: An unexpected error occurred on a send

これは、インデクサが現在の.NETバージョンでサポートされていないSSLプロトコルを使用しているためです。[Radarr => System => Status](/radarr/system#status)で現在の.NETバージョンを確認できます。

### The request timed out

Radarrはクライアントからの応答を受け取っていません。

```none
    System.NET.WebException: The request timed out: ’https://example.org/api?t=caps&apikey=(removed) —> System.NET.WebException: The request timed out
```

```none
2022-11-01 10:16:54.3|Warn|Newznab|Unable to connect to indexer

[v4.3.0.6671] System.Threading.Tasks.TaskCanceledException: A task was canceled.
```

これは次の原因によっても引き起こされる可能性があります：

- VPNの設定が正しくないか、使用されている
- プロキシの設定が正しくないか、使用されている
- ローカルのDNSの問題 - 異なるDNSプロバイダに変更してみてください
- ローカルのIPv6の問題 - 通常、IPv6は有効になっていますが、機能していません
- Privoxyの使用と、それが正しく設定されていないこと

## リストされていない問題

一般的なアクセス許可とネットワーキングのトラブルシューティングコマンドについては、[ガイド](/permissions-and-networking)を参照してください。それ以外の場合は、ディスコードのサポートチームと相談してください。これが一般的な問題である可能性がある場合は、ウィキに追加することを提案してください。

# 検索インデクサとトラッカー

- [Prowlarr](/prowlarr)を使用している場合、Prowlarrが受信したすべてのクエリの[履歴](/prowlarr/history)とそれらがどのようにサイトに送信されたかを表示できます。Prowlarr History => Optionsで`Parameters`が有効になっていることを確認してください。詳細については(i)アイコンをクリックして追加の詳細を表示できます。

## ログをトレースレベルに設定する

> **最初のステップは、ログをトレースレベルに設定することです。ログの調整と検索に関する詳細については、[ログとログファイル](#logging-and-log-files)を参照してください。問題を再現し、その時間枠のトレースレベルのログを使用して問題を調査します。** サポートを受けている場合は、前後のコンテキストを[pastebin](https://0bin.net)、[Gist](https://gist.com)、または類似のサイトに表示してください。ファイル全体である必要はありませんし、エラーだけであってはいけません。また、ログファイルにスパムをするタスクが実行されていない状態で問題を再現する必要があります。
{.is-danger}

## インデクサまたはトラッカーのテスト

インデクサまたはトラッカーをテストする場合、デバッグまたはトレースログで使用されたURLを見つけることができます。以下は成功したテストの例です。特定のURLとパラメータを使用してインデクサにクエリを送信し、その応答を確認できます。このURLをブラウザでテストして、`apikey=(removed)`を正しいapikey（例：`apikey=123`）に置き換えてみてください。動作しますか？期待される結果が表示されますか？このURLでは、特定のカテゴリ（2000）が設定されていることがわかります。期待される結果が表示されない場合、これが原因の1つです。インデクサ上で映画が適切にカテゴリ分類されていない場合、修正する必要があります。動作するクエリの出力の例については、Manual Search XML Outputを参照してください。

- Manual Search XML Output

```xml
<rss xmlns:atom="http://www.w3.org/2005/Atom" xmlns:newznab="http://www.newznab.com/DTD/2010/feeds/attributes/" version="2.0">
<channel>
<atom:link href="https://api.nzbgeek.info/api?t=movie&cat=2000&apikey=(removed)&q=O+Brother+Where+Art+Thou" rel="self" type="application/rss+xml"/>
<title>api.nzbgeek.info</title>
<description>NZBgeek API</description>
<link>http://api.nzbgeek.info/</link>
<language>en-gb</language>
<webMaster>info@nzbgeek.info (NZBgeek)</webMaster>
<category/>
<image>
<url>https://api.nzbgeek.info/covers/nzbgeek.png</url>
<title>api.nzbgeek.info</title>
<link>http://api.nzbgeek.info/</link>
<description>NZBgeek</description>
</image>
<newznab:response offset="0" total="17"/>
<item>
<title>O.Brother.Where.Art.Thou.2000.1080p.BluRay.H264.AC3.DD5.1</title>
<guid isPermaLink="true">https://api.nzbgeek.info/api?t=details&id=e83b7ae75bca71e92367fab29b036731&apikey=(removed)</guid>
<link>https://api.nzbgeek.info/api?t=get&id=e83b7ae75bca71e92367fab29b036731&apikey=(removed)</link>
<comments>https://nzbgeek.info/geekseek.php?guid=e83b7ae75bca71e92367fab29b036731</comments>
<pubDate>Sat, 10 Jul 2021 08:33:22 +0000</pubDate>
<category>Movies > BluRay</category>
<description>O.Brother.Where.Art.Thou.2000.1080p.BluRay.H264.AC3.DD5.1</description>
<enclosure url="https://api.nzbgeek.info/api?t=get&id=e83b7ae75bca71e92367fab29b036731&apikey=(removed)" length="4041237000" type="application/x-nzb"/>
<newznab:attr name="category" value="2000"/>
<newznab:attr name="category" value="2050"/>
<newznab:attr name="size" value="4041237000"/>
<newznab:attr name="guid" value="e83b7ae75bca71e92367fab29b036731"/>
</item>
<item>
<title>O.Brother.Where.Art.Thou.2000.1080p.BluRay.H264.AC3.DD5.1</title>
<guid isPermaLink="true">https://api.nzbgeek.info/api?t=details&id=c00a92567863801ab1a4901458ae31ba&apikey=(removed)</guid>
<link>https://api.nzbgeek.info/api?t=get&id=c00a92567863801ab1a4901458ae31ba&apikey=(removed)</link>
<comments>https://nzbgeek.info/geekseek.php?guid=c00a92567863801ab1a4901458ae31ba</comments>
<pubDate>Sun, 28 Mar 2021 10:50:38 +0000</pubDate>
<category>Movies > BluRay</category>
<description>O.Brother.Where.Art.Thou.2000.1080p.BluRay.H264.AC3.DD5.1</description>
<enclosure url="https://api.nzbgeek.info/api?t=get&id=c00a92567863801ab1a4901458ae31ba&apikey=(removed)" length="4041237000" type="application/x-nzb"/>
<newznab:attr name="category" value="2000"/>
<newznab:attr name="category" value="2050"/>
<newznab:attr name="size" value="4041237000"/>
<newznab:attr name="guid" value="c00a92567863801ab1a4901458ae31ba"/>
</item>
<item>
<title>O.Brother.Where.Art.Thou.2000.720p.BrRip.x264-YIFY</title>
<guid isPermaLink="true">https://api.nzbgeek.info/api?t=details&id=75f5be8b4cd573c2359b638350689f73&apikey=(removed)</guid>
<link>https://api.nzbgeek.info/api?t=get&id=75f5be8b4cd573c2359b638350689f73&apikey=(removed)</link>
<comments>https://nzbgeek.info/geekseek.php?guid=75f5be8b4cd573c2359b638350689f73</comments>
<pubDate>Sun, 28 Jul 2019 00:46:00 +0000</pubDate>
<category>Movies > HD</category>
<description>O.Brother.Where.Art.Thou.2000.720p.BrRip.x264-YIFY</description>
<enclosure url="https://api.nzbgeek.info/api?t=get&id=75f5be8b4cd573c2359b638350689f73&apikey=(removed)" length="936738000" type="application/x-nzb"/>
<newznab:attr name="category" value="2000"/>
<newznab:attr name="category" value="2040"/>
<newznab:attr name="size" value="936738000"/>
<newznab:attr name="guid" value="75f5be8b4cd573c2359b638350689f73"/>
</item>
<item>
<title>O.Brother.Where.Art.Thou.[bdrip-1080p-multilang-multisub-CHAPTERS]</title>
<guid isPermaLink="true">https://api.nzbgeek.info/api?t=details&id=a0fe801d9ba0a703db7d2164e996aa1f&apikey=(removed)</guid>
<link>https://api.nzbgeek.info/api?t=get&id=a0fe801d9ba0a703db7d2164e996aa1f&apikey=(removed)</link>
<comments>https://nzbgeek.info/geekseek.php?guid=a0fe801d9ba0a703db7d2164e996aa1f</comments>
<pubDate>Mon, 14 Aug 2017 15:34:36 +0000</pubDate>
<category>Movies > HD</category>
<description>O.Brother.Where.Art.Thou.[bdrip-1080p-multilang-multisub-CHAPTERS]</description>
<enclosure url="https://api.nzbgeek.info/api?t=get&id=a0fe801d9ba0a703db7d2164e996aa1f&apikey=(removed)" length="9746182000" type="application/x-nzb"/>
<newznab:attr name="category" value="2000"/>
<newznab:attr name="category" value="2040"/>
<newznab:attr name="size" value="9746182000"/>
<newznab:attr name="guid" value="a0fe801d9ba0a703db7d2164e996aa1f"/>
</item>
</channel>
</rss>
```

***画像が必要***

![searches-indexers-and-trackers1.png](/assets/radarr/searches-indexers-and-trackers1.png)
![searches-indexers-and-trackers2.png](/assets/radarr/searches-indexers-and-trackers2.png)

- トレースログのスニペット

```none
必要な手動検索のトレースログのスニペット
```

- 検索の完全なトレースログ

```none
必要な手動検索のトレースログの完全なセクション
```

## 一般的な問題

以下は一般的な問題です。

### トラッカーがRawSearch Capsを必要とする

- Radarrが「Kikis Delivery Service」を検索していますが、トラッカーには「Kiki's Delivery Service」の結果しかありません
- これは、トラッカーが通常の標準化された検索をサポートしていないためです
- 解決策は、トラッカーの定義の検索機能を更新して、`RawSearch`を必要とし、サポートすることを示す必要があります（[Radarrの問題#4502](https://github.com/Radarr/Radarr/issues/4502#issuecomment-981143905)を参照）
- Jackettはこのフラグをサポートしていますが、機能を追加するためにJackettのインデクサごとに機能を更新する必要があります。Jackettに対してインデクサの機能追加のリクエストをオープンしてください。
- Prowlarrはこのフラグをサポートしていますが、Prowlarrのインデクサごとに機能を更新する必要があります。Prowlarrに対してインデクサの機能追加のリクエストをオープンしてください。

### メディアが監視されていない

映画が監視されていません。

### カテゴリが間違っています

誤ったカテゴリは、インデクサ/トラッカーの手動検索結果に表示される最も一般的な原因ですが、結果がに表示されない場合があります。インデクサ/トラッカーは、検索結果にカテゴリを表示するはずですので、何が欠けているかを特定するのに役立ちます。JackettやProwlarrを使用している場合、各トラッカーには特にサポートされているカテゴリのリストがあります。カテゴリのエントリを編集する際に、リストを別のブラウザウィンドウで表示すると便利です。

### クエリは成功しましたが、結果が返されませんでした

`クエリは成功しましたが、インデクサから結果が返されませんでした。これはインデクサまたはインデクサのカテゴリ設定の問題かもしれません。`というメッセージが表示される場合、インデクサが構成されたカテゴリ内の結果を返さないためです。

### 誤った結果

インデクサがまったく関係のない結果を返すことがあります。Radarrは検索を制限するためのパラメータを提供しますが、返される結果はまったく関係のないものです。または、ほとんど関連しているが、いくつかの誤った結果があることもあります。前者は通常、インデクサの問題であり、トレースログから原因を特定できます。そのインデクサを無効にして問題を報告できます。後者は通常、カテゴリが誤って分類されたリリースであり、インデクサ/トラッカーで報告できます。

### 結果が見つからない

Radarrに表示されないが、サイトで見つけることができる結果がある場合、問題はおそらく次のいずれかの可能性です。

- [カテゴリが間違っています - 上記を参照](#wrong-categories)
- ID（IMDbId、TMDbIdなど）に基づいた検索が行われ、インデクサがリリースを正しくそのIDにマッピングしていない場合。これはインデクサだけが解決できる問題です。インデクサは、リリースが正しい適用可能なIDにマッピングされるようにする必要があります。
- Radarrが検索している方法とは異なる方法で検索している可能性があります。Radarrがどのようにクエリを行っているかは、トレースログから確認できます。テキストベースのクエリは一般的に`q=words%20and%20things%20here`の形式であり、この文字列はHTTPエンコードされており、オンラインのHTMLデコード/エンコードツールを使用して簡単にデコードできます。
- [外国映画のタイトルの扱いと、Radarrがそれらを検索するタイミングについては、FAQを参照してください](/radarr/faq#how-does-radarr-handle-foreign-movies-or-foreign-titles)

### 証明書の検証

ほとんどのインデクサ/トラッカーにはhttps経由で接続する必要があるため、システム上で正常に機能する必要があります。つまり、タイムゾーンと時刻の両方が*正しく*設定されている必要があります。また、システムの証明書も最新である必要があります。

### レート制限に達する

VPNやプロキシを使用して実行している場合、他の数十人または数百人、または数千人のユーザーと競合する可能性があります。これらのユーザーは、やtheXEM、またはインデクサ/トラッカーなどのサービスを利用しようとしています。レート制限とDDoS保護は、IPアドレスごとに行われることがよくあります。VPN/プロキシのエグジットポイントは*1つの*IPアドレスです。中国、オーストラリア、南アフリカなどの抑圧的な国でない限り、VPN/プロキシは必要ありません。

Rarbgは、API内である種のレート制限を持つ傾向があり、結果がないと表示されます。

### IPブロック

レート制限と同様に、特定のインデクサ（Nyaaなど）はIPアドレスを完全にブロックする場合があります。これは通常、半永久的なものであり、解決策はISPまたはVPNプロバイダから新しいIPを取得することです。

### 年が一致しない

- [このFAQエントリを参照してください](/radarr/faq#how-does-radarr-determine-the-year-of-a-movie)
  - RadarrはTMDbからメタデータを取得します
  - Radarrは最も古い**劇場公開**日と最も古い**プレミア**日の年を使用して一致を見つけます
- 一部の場合、映画が変更されたり移動されたりして、リリースグループが使用している年が最も古いプレミア日の年または最も古い劇場公開日の年と一致しない場合があります。このような場合は、手動で取得してインポートする必要があります。

### 年が欠落している

リリース名に年が含まれていない場合、Radarrはリリースを取得しません。これは不良なリリースであり、手動で取得する必要があります。これは、映画が予想どおりに取得されなかった理由を特定しようとする際に見落とされることがよくあります。

### Jackettの/allエンドポイントの使用

Jackettの`/all`エンドポイントは便利ですが、それが唯一の利点です。それ以外は潜在的な問題がありますので、各トラッカーを個別に追加する必要があります。または、Jackett & NZBHydra2の代替である[Prowlarr](/prowlarr)をご覧いただくこともできます。

[Jackett自体も/allは避けるべきであり、使用しないでくださいと言っています。](https://github.com/Jackett/Jackett#aggregate-indexers)

/allエンドポイントの使用には利点がありません（管理のオーバーヘッドが減る以外）、デメリットしかありません。

- インデクサ固有の設定（カテゴリ、検索モードなど）を制御できなくなります。
- 検索モード（IMDB、クエリなど）を混在させると、品質の低い結果が生じる可能性があります。
- インデクサ固有のカテゴリ（100000以上）は使用できません。
- 遅いインデクサは全体の結果を遅くします。
- 合計結果は1000に制限されます。

各インデクサを個別に追加することで、カテゴリをインデクサごとに細かく調整できます。`/all`エンドポイントでは、間違ったカテゴリを使用すると一部のトラッカーでエラーが発生する可能性があるため、問題が発生することがあります。また、ページネーションがサポートされている場合は、各インデクサは1000件の結果に制限されます。ページネーションがサポートされていない場合は100件に制限されます。つまり、Jackettにトラッカーを追加するにつれて、結果が切り取られる可能性が高くなります。最後に、`/all`の中の*1つ*のトラッカーがエラーを返すと、はそれを無効にし、結果が得られなくなります。

### 単一のエントリとしてNZBHydra2を使用する

NZBHydra2を単一のインデクサエントリ（つまり、NZBHydra2内の多くのインデクサに対するRadarr内の1つのNZBHydra2エントリ）として使用する場合、Jackettの`/all`エンドポイントと同様の問題が発生します。

### リストされていない問題

一般的な権限とネットワーキングのトラブルシューティングコマンドについては、[ガイド](/permissions-and-networking)を参照してください。それ以外の場合は、ディスコードのサポートチームと相談してください。これが一般的な問題である可能性がある場合は、ウィキに追加することを提案してください。

## エラー

インデクサを追加する際に表示される一部の一般的なエラーは次のとおりです。

### The underlying connection was closed: An unexpected error occurred on a send

これは、インデクサが現在の.NETバージョンでサポートされていないSSLプロトコルを使用しているためです。[Radarr => システム => ステータス](/radarr/system#status)で見つかる.NETバージョンを確認してください。

### The request timed out

Radarrはインデクサからの応答を受け取っていません。

```none
    System.NET.WebException: The request timed out: ’https://example.org/api?t=caps&apikey=(removed) —> System.NET.WebException: The request timed out
```

```none
2022-11-01 10:16:54.3|Warn|Newznab|Unable to connect to indexer

[v4.3.0.6671] System.Threading.Tasks.TaskCanceledException: A task was canceled.
```

これは次の原因によっても引き起こされる可能性があります。

- VPNの設定が正しくないか、使用方法が誤っている
- プロキシの設定が正しくないか、使用方法が誤っている
- ローカルのDNSの問題 - 異なるDNSプロバイダに変更してみてください
- ローカルのIPv6の問題 - 通常、IPv6は有効になっていますが、機能していません
- Privoxyの使用と、それが正しく設定されていないこと

### リストされていない問題

一般的な権限とネットワーキングのトラブルシューティングコマンドについては、[ガイド](/permissions-and-networking)を参照してください。それ以外の場合は、ディスコードのサポートチームと相談してください。これが一般的な問題である可能性がある場合は、ウィキに追加することを提案してください。