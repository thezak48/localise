# トラブルシューティング

## ヘルプを求める

ヘルプが必要ですか？大丈夫です、誰でも時にはヘルプが必要です。以下の方法でリアルタイムのヘルプを受けることができます。

- [<i class="fab fa-discord"></i>&emsp;Discord *公式Lidarr Discord*](https://lidarr.audio/discord)
- [<i class="fab fa-reddit"></i>&emsp;Reddit *公式Lidarr Subreddit*](https://reddit.com/r/lidarr)
{.links-list}

ただし、投稿する前に、ヘルプを求めるためのリクエストが最善のものであることを確認してください。問題を明確に説明し、OS/ディストリビューション、.NETのバージョン、Lidarrのバージョン、ダウンロードクライアントとそのバージョンなど、セットアップに関する情報を簡単に説明してください。**[Docker](https://www.docker.com/)を使用している場合は、まず[Dockerガイド](/docker-guide)を実行して、一般的で頻繁なパス/アクセス許可の問題を解決してください。それ以外の場合は、[docker compose](/docker-guide#docker-compose)を手元に用意してください。[Docker Composeの生成方法](https://trash-guides.info/compose)** すでに試したこと、調べたことについて教えてください。問題を再現し、関連するコンテキストをパスビンに貼り付け、そのリンクを投稿に含めてください。問題を強調するためにスクリーンショットを含めることもできます。

私たちが知っていることが多ければ多いほど、あなたを助けることが容易になります。

## ロギングとログファイル

以下の一般的なトラブルシューティングの問題も確認することをお勧めします。
- [ダウンロードとインポートの一般的な問題](#downloads-and-importing)
- [検索インデクサとトラッカーの一般的な問題](#searches-indexers-and-trackers)
{.links-list}

デバッグログが必要な場合、ログには `debug` が含まれ、トレースログが必要な場合は `trace` が含まれます。提供するログにこれらのいずれかが含まれていない場合は、要求されたログではありません。

- 要求されていない限り、ログファイル全体を共有しないでください。
- 要求されていない限り、ログを直接Discordにアップロードしたり、テキストの壁として貼り付けたりしないでください。
- ログを添付ファイル、ZIPアーカイブ、またはそれ以外のテキスト以外の形式で共有しないでください。

有用なログを提供するための手順:

> RSSの更新など、スパムの多いタスクが実行されていないことを確認してください。
{.is-warning}

1. [ログレベルをトレースに設定する（設定 => 一般 => ログレベルまたは設定ファイルの編集）](#tracedebug-logs)
2. [ログをクリアする（システム => ログ => ログをクリアまたはログフォルダ内のすべてのログを削除）](#clearing-logs)
3. 問題を再現する（問題を引き起こしていることを再現する）
4. UIまたはログファイル上の[標準ログの場所](#standard-logs-location)から関連するコンテキストを見つける
5. 問題の前、問題そのもの、問題の後ろの大きなチャンクをコピーする
6. [Gist](https://gist.github.com/)、[0bin（**カラーリングを無効にすることを忘れないでください**）](https://0bin.net/)、[PrivateBin](https://privatebin.net/)、[Notifiarr PrivateBin](http://logs.notifiarr.com/)、[Hastebin](https://hastebin.com/)、[UbuntuのPastebin](https://pastebin.ubuntu.com/)などのサイトを使用して、上記でコピーしたログを共有する

**注意事項:**
- **[pastebin.com](https://pastebin.com)は、フィルターがログをブロックする傾向があるため使用しないでください。
- [pastebin.pl](https://pastebin.pl)は、サイトに頻繁にアクセスできないため使用しないでください。
- [JustPasteIt](https://justpaste.it/)は、ログの確認を容易にすることができないため使用しないでください。
- ログをファイルとしてアップロードしないでください。
- ログをGoogleドライブ、Dropbox、または上記以外のサイトでアップロードして共有しないでください。
- ログをアーカイブ（zip、tar（tarボール）、7zipなど）しないでください。
- コンソール出力、Dockerコンテナ出力、アプリケーションログ以外のものを共有しないでください。

**重要な注意事項:**
- [0bin](https://0bin.net/)を使用する場合は、カラーリングを無効にし、読み終わった後も削除しないようにしてください。

- また、古いログファイルで特定のエントリを検索する場合、Notepad++を使用することができます。Notepad++の「ファイル内検索」機能を使用して必要な古いログファイルを検索できます。
- **Unixの場合:** 古いログファイルで特定のエントリを検索する場合、grepを使用することができます。たとえば、映画/番組/書籍/曲/インデクサ「Shooter」に関する情報を検索したい場合は、次のコマンドを実行します。`grep -inr -C 100 -e 'Shooter' /path/to/logs/*.trace*.txt` もし[Appdataディレクトリ](/lidarr/appdata-directory)がホームフォルダにある場合は、次のように実行します。`grep -inr -C 100 -e 'Shooter' /home/$User/.config/logs/*.trace*.txt`

```none

    * 各フラグの機能は次のとおりです
    * -i: 大文字と小文字を区別しない
    * -n: 行番号を表示する
    * -r: パス内のすべてのファイルを再帰的にチェックする
    * -C: 検索された行の前後の行数を指定する
    * -e: 検索するパターン

```

## 標準ログの場所

ログファイルは、Lidarrの[Appdataディレクトリ](/lidarr/appdata-directory)内のlogs/フォルダにあります。また、UIからもログファイルにアクセスできます。System => Logs => Files.

> 注意: UIのログ（"イベント"）テーブルはログファイルとは異なり、あまり役に立ちません。ログが要求された場合は、ログファイルからコピー/貼り付けしてください。
{.is-info}

## 更新ログの場所

更新ログファイルは、Lidarrの[Appdataディレクトリ](/lidarr/appdata-directory)内のUpdateLogs/フォルダにあります。

## ログの共有

ログは長くて読みにくい場合があり、フォーラムやRedditの投稿ではスパムになりますので、[Pastebin](https://pastebin.ubuntu.com/)、[Hastebin](https://hastebin.com/)、[Gist](https://gist.github.com)、[0bin](https://0bin.net)、または類似のパステビンサイトを使用してください。通常、ファイル全体ではなく、問題/エラーの前後の十分なコンテキストを共有すれば十分です。RSSの同期やライブラリの更新など、スパムの多いタスクが終了するまで待つのを忘れないでください。

## トレース/デバッグログ

ログレベルは、設定 => 一般 => ロギングで変更できます。Lidarrを再起動する必要はありません。この変更はログファイルのみに影響を与えます。最新のデバッグ/トレースログファイルは、それぞれ `lidarr.debug.txt` と `lidarr.trace.txt` という名前です。

ログレベルを設定するためにUIにアクセスできない場合は、AppDataディレクトリのconfig.xmlを編集して、LogLevelの値をInfoではなくDebugまたはTraceに設定することで設定できます。

```xml
 <Config>
  [...]
  <LogLevel>debug</LogLevel>
  [...]
 </Config>
```

## ログのクリア

ログファイルとログデータベースは、UIから直接クリアできます。System => Logs => FilesとSystem => Logs => Delete（ゴミ箱アイコン）を使用してください。

## 複数のログファイル

Lidarrは、1MBまでのローリングログファイルを使用します。現在のログファイルは常に `lidarr.txt` です。他のファイルは `.0.txt` が次に新しいものです（数値が大きいほど古いものです）。このログファイルには `fatal`、`error`、`warn`、`info` のエントリが含まれています。

デバッグログレベルが有効になっている場合、追加の `lidarr.debug.txt` ローリングログファイルが存在します。このログファイルには `fatal`、`error`、`warn`、`info`、`debug` のエントリが含まれています。通常、40時間の期間をカバーしています。

トレースログレベルが有効になっている場合、追加の `lidarr.trace.txt` ローリングログファイルが存在します。このログファイルには `fatal`、`error`、`warn`、`info`、`debug`、`trace` のエントリが含まれています。トレースの冗長性のため、最大で数時間しかカバーしていません。

# 失敗したアップデートからの復旧

アップグレード時の問題を防ぐために最善の努力をしていますが、問題が発生した場合は、この手順に従ってインストールを復旧します。

## 問題の特定

- アップデート後にアプリケーションが起動しない場合は、まず[アップデートログ](#update-logs-location)を確認し、アップデートが正常に完了したかどうかを確認してください。それでも問題が解決しない場合は、起動する前に通常のアプリケーションログファイルを確認し、[ログ](/lidarr/settings#logging)と[ログファイル](/lidarr/system#log-files)を使用してログファイルを見つけ、ログレベルを上げてください。
- 最も頻繁に発生する問題は、アプリケーションがインストールされているシステムが `/tmp` ディレクトリをいじり、アップグレード中に重要な \*Arr ファイルを削除したため、アップグレードとロールバックの両方が失敗することです。この場合は、単に既存の破損したインストールの上に再インストールしてください。

### 移行の問題

- 移行エラーは同一ではありませんが、以下は例です。

```none
14-2-4 18:56:49.5|Info|MigrationLogger|\*\*\* 36: update\_with\_quality\_converters migrating \*\*\*

14-2-4 18:56:49.6|Error|MigrationLogger|SQL logic error or missing database duplicate column name: Items

While Processing: "ALTER TABLE "QualityProfiles" ADD COLUMN "Items" TEXT"

```

### アクセス許可の問題

- アクセス許可の問題は、アプリケーションが関連する一時フォルダやアプリケーションのバイナリフォルダにアクセスできないために発生します。アプリケーションが実行されるユーザー/グループが適切なアクセス権を持つようにアクセス許可を修正してください。

- Synologyユーザーは、Synologyのバグ「アクセスが拒否されました '/proc/{some number}/maps」に遭遇する場合があります。

- Synologyユーザーは、特定のNASの/tmpディレクトリの容量が不足している場合があります。この場合は、アプリの別の/tmpパスを指定する必要があります。SynoCommunityやその他のSynologyのサポートチャンネルでヘルプを求めてください。

## 問題の解決

移行の問題の場合、すぐにできることはあまりありません。問題が特定のユーザーに固有の場合（またはまだ投稿がない場合）、[reddit](https://reddit.com/r/lidarr)で投稿を作成するか、[discord](https://lidarr.audio/discord)に参加してください。同じ問題を抱えている他のユーザーがいる場合は、私たちはそれに取り組んでいます。

> 安定版で「nightly」のデータベースを使用しようとしないでください。ブランチを行き来することはお勧めしません。{.is-info}

### アクセス許可の問題

- アクセス許可を修正して、アプリケーションが `/tmp` とインストールディレクトリにアクセス（読み取りと書き込み）できるようにしてください。

- Synologyユーザーが `/proc/###/maps` の問題でSonarrまたは他の\*Arrアプリケーションが停止する場合は、Sonarrを停止して更新すると、問題が解決する場合があります。これはSynoCommunityパッケージの問題です。

### 手動でのアップグレード

ウェブサイトから最新のリリースを取得してください。

アップデート（.exe）をインストールするか、（.zip）の内容を既存のインストールに解凍し、通常通りLidarrを再実行します。

# ダウンロードとインポート

ダウンロードとインポートは、*ほとんどの*人が問題を抱える場所です。大まかな視点から見ると、Lidarrはダウンロードクライアントと通信し、ダウンロードしたファイルにアクセスする必要があります。サポートされているダウンロードクライアントの種類はさまざまで、さらに多様なセットアップがあります。つまり、一部の*一般的な*セットアップがありますが、*正しい*セットアップはなく、誰のセットアップも少し異なる可能性があります。

> **まずはログをトレースレベルに設定し、詳細については[ログとログファイル](#logging-and-log-files)を参照してログの調整と検索方法を確認してください。その後、問題を再現し、その時間枠のトレースレベルのログを使用して問題を調査します。**誰かが助けてくれる場合は、過去/後のコンテキストを[pastebin](https://0bin.net)、[Gist](https://gist.com)、または類似のサイトに表示して共有してください。全体のファイルである必要はなく、エラーだけではありません。また、ログファイルにスパムを送るタスクが実行されていない状態で問題を再現してください。
{.is-danger}

ヘルプを求める際には、[ヘルプを求める](#asking-for-help)を必ず読んで、必要な詳細を提供できるようにしてください。

## ダウンロードクライアントのテスト

ダウンロードクライアントが実行されていることを確認してください。まず、ダウンロードクライアントをテストしてください。うまくいかない場合は、トレースレベルのログで詳細を確認できます。ブラウザに入力できるURLを見つけて、それが機能するかどうか確認してください。接続の問題かもしれません。間違ったIP、ホスト名、ポート、またはファイアウォールによるアクセスのブロックなどが原因となる可能性があります。ユーザー名、パスワード、またはAPIキーが間違っている場合など、明らかな問題かもしれません。

## ダウンロードのテスト

次に、ダウンロードを試してみましょう。曲を選んで手動で検索してみてください。それらのファイルのうちの1つを選んでダウンロードを試みます。ダウンロードクライアントに送信されますか？正しいカテゴリに表示されますか？アクティビティに表示されますか？トレースレベルのログに表示されますか（「完了したダウンロードのチェック」タスク（監視されているダウンロードの更新と監視されているダウンロードの処理タスク）の間隔で実行されます）？そのタスク中に正しく解析されますか？キューに入れられたダウンロードの名前は適切ですか？一部のインデクサ/トラッカーではIDで検索されるため、認識できない名前でキューに入れることがあります。

## インポートのテスト

インポートの問題はほとんど常にアクティビティに表示され、エラーをホバーするとオレンジのアイコンが表示されます。アクティビティに表示されない場合は、まずこの問題に焦点を当てて解決する必要がありますので、戻って確認してください。ほとんどのインポートエラーは*パーミッション*の問題です。ダウンロードフォルダーに読み取りと書き込みができるようにする必要があります。ライブラリフォルダーのパーミッションも問題の原因となる場合があるため、両方を確認してください。

パスの問題も発生する可能性がありますが、通常のセットアップではあまり一般的ではありません。パスの問題を理解するためのキーは、ダウンロードクライアントからのダウンロードのパスをAPI経由で取得することです。これは、ダウンロードクライアントが異なるシステム（おそらく異なるOS）で実行されているなど、よりユニークな使用例で問題となることがあります。また、Dockerのセットアップでは、ボリュームがうまく設定されていない場合にも発生する可能性があります。リモートパスマップは、シードボックスのセットアップなど、制御できない場所で使用するのに適しています。Dockerのセットアップでは、パスを修正することがより良いオプションです。

## よくある問題

以下は一部の一般的な問題です。

### ダウンロードクライアントのWebUIが有効になっていない

Lidarrは、ダウンロードクライアントとの通信にAPIを使用し、クライアントのWebUIにアクセスします。クライアントのWebUIが有効になっていることを確認し、使用しているポートが他のクライアントポートやシステムで使用されているポートと競合していないことを確認してください。

### SSLが使用され、正しく構成されていない

インスタンスとダウンロードクライアントの両方をローカルネットワークで使用している場合は、SSL暗号化がオンになっていないことを確認してください。詳細については、[SSL FAQエントリ](/lidarr/faq#invalid-certificate-and-other-HTTPS-or-SSL-issues)を参照してください。

### Windowsで共有が表示されない

Windowsサービスのデフォルトユーザーは「LocalService」であり、通常は共有にアクセスできません。サービスを編集し、自分自身のユーザーとして実行するように設定してください。詳細については、FAQエントリの[リモートサーバー上のファイルが表示されない理由](/lidarr/faq#why-cant-see-my-files-on-a-remote-server)を参照してください。

### マップされたネットワークドライブは信頼性がない

「X：\」のようなマップされたネットワークドライブは便利ですが、UNCパス（「\\server\share」のような）ほど信頼性がありません。また、ログイン前には利用できません。必要に応じて、セットアップとダウンロードクライアントをUNCパスを使用するように構成してください。ライブラリが共有にある場合は、ルートフォルダーがUNCパスを使用していることを確認してください。ダウンロードクライアントが共有に送信する場合は、ダウンロードパスをダウンロードクライアントから取得する必要があるため、UNCパスを構成する必要があります。マップされたネットワークドライブを自分自身で使用することは問題ありませんが、自動化には使用しないでください。

### Dockerとユーザー、グループ、所有権、パーミッション、パス

Dockerは、間違いやすい複雑さを追加しますが、それでも機能するセットアップになることがあります。ここではそれらについて説明しませんが、[これらの自動化ソフトウェアとDockerに関するこのウィキ記事](/docker-guide)を読んで、ユーザー、グループ、所有権、パーミッション、パスについての情報を確認してください。これは特定のDockerシステムに特化しているのではなく、高レベルでの説明を行っているため、独自の環境で実装できます。

### リモートパスマッピング

LidarrをDockerで使用し、ダウンロードクライアントを非Dockerで使用している場合（またはその逆）、またはプログラムを異なるサーバーで使用している場合は、リモートパスマップが必要になる場合があります。

ログは次のようになります。

```none
2022-02-03 14:03:54.3|Error|DownloadedTracksImportService|Import failed, path does not exist or is not accessible by Lidarr: /volume3/data/torrents/music/Five Finger Death Punch - F8 (2020) FLAC. Ensure the path exists and the user running Lidarr has the correct permissions to access this file/folder
```

したがって、`/volume3/data`はLidarrのコンテナ内に存在しないか、アクセスできない可能性があります。

- [設定 => ダウンロードクライアント => リモートパスマッピング](/lidarr/settings#remote-path-mappings)
- リモートパスマッピングは、ダウンロードクライアントが別のサーバー上の完了したデータのパスを報告している場合、または\*Arrがそのフォルダーに対応していない方法で報告している場合に使用されます。
- 一般的には、ダウンロードクライアントがLinux上にある場合にのみリモートパスマップが必要です。また、Dockerとネイティブクライアントを混在させる場合や、リモートサーバーを使用する場合にもリモートパスマップが必要になる可能性があります。
- リモートパスマップは、指定したホストのために、検索/置換（リモートの値を見つけて、ローカルの値に置き換える）を行います。
- パスのマッピングが正常に機能していない場合、エラーメッセージに置換された値が含まれていない場合は、通常どおりの動作ではありません。典型的な解決策は、マッピングを追加および削除することです。
- [リモートパスマッピングに関する詳細な情報については、TRaSHのチュートリアルを参照してください](https://trash-guides.info/Radarr/Radarr-remote-path-mapping/)

> \*Arrとダウンロードクライアントの両方がDockerコンテナである場合、リモートパスマップはほとんど必要ありません。[Dockerガイド](/docker-guide)を参照するか、[TRaSHのチュートリアル](https://trash-guides.info/hardlinks)に従うことをお勧めします。
{.is-info}

#### リモートマウントまたはリモート同期（Syncthing）

- ダウンロード中に常に同期される必要があります。また、ローカルの同期先は、\*Arrのインポート時にハードリンクになる必要があります。つまり、同じファイルシステムであり、同じように見える必要があります。
  - 不完全なものと完全なものの両方を含む共通のフォルダーで同期します。
  - ライブラリと同じファイルシステム上の場所に同期します（Dockerとネットワーク共有を使用すると、これを誤って設定することがよくあります）。
  - 不完全なものと完全なものを同期することで、トレントクライアントが移動を行ったときにローカルで反映され、すべてのファイルがすでに「そこ」にある状態になります（まだダウンロード中でも）。その後、ハードリンクを使用する必要があります。インポートが完了する前にインポートされても、それらはまだ完了します。
  - これにより、ダウンロード中は常に同期され、トレントクライアントがtvサブフォルダーに移動すると、同期が反映されます。これにより、ダウンロードはほぼ完了してから宣言されます。そして、完全に完了していなくても、ハードリンクが可能であることはまだ問題ありません。
  - （オプション - 該当する場合および/または必要な場合（例：リモートユーズネットクライアント））インポート/ダウンロード/アップグレード時にカスタムスクリプトを設定して、リモートファイルを削除します。
- リモート同期の代わりに、リモートマウントの設定ははるかに複雑ではありませんが、通常は遅くなります。
  - sshfsや他のネットワークファイルシステムプロトコルを使用してリモートストレージをマウントします。
  - \*Arrが実行されるユーザーとグループが読み取りまたは書き込みアクセス権を持っていることを確認します。
  - リモートパスマップを構成して、REMOTEパスを見つけて、それをLOCALの相当するパスに置き換えます。

### ライブラリフォルダーのパーミッション

ログは次のようになります。

```none
2022-02-28 18:51:01.1|Error|DownloadedTracksImportService|Import failed, path does not exist or is not accessible by Lidarr: /data/media/music/Jasmine Guillory/Party of Two - Jasmine Guillory.mp3. Ensure the path exists and the user running Lidarr has the correct permissions to access this file/folder
```

*宛先*のパーミッションと所有権も確認してください。ダウンロードの所有権とパーミッションにこだわりすぎることが簡単であり、通常はパーミッション関連の問題の原因ですが、*宛先*も原因となる可能性があります。宛先フォルダーが存在することを確認してください。宛先の*ファイル*がすでに存在しないか、削除またはごみ箱に移動できないか確認してください。所有権とパーミッションが、ダウンロードしたファイルのコピー、ハードリンク、または移動を許可していることを確認してください。実行するユーザーまたはグループは、ルートフォルダーを読み取りおよび書き込みできる必要があります。

- Windowsユーザーの場合、これはサービスとして実行されていることによるものかもしれません：
  - Windowsサービスはデフォルトで「Local Service」アカウントで実行されますが、このアカウントは通常、手動で権限が割り当てられていない限り、ユーザーのホームディレクトリにアクセスできません。これは、ユーザーのホームディレクトリにダウンロードを設定しているダウンロードクライアントを使用する場合に特に関係します。
  - 「Local Service」は一般的に非常に制限された権限を持っています。したがって、ユーザーがログインしたままであれば、システムトレイアプリケーションとしてアプリをインストールすることをお勧めします。インストーラーで提供されるオプションです。サービスからトレイアプリに変換する方法については、FAQを参照してください。

- Synologyユーザーは、[SynoCommunityのパッケージの権限管理に関する記事](https://github.com/SynoCommunity/spksrc/wiki/Permission-Management)を参照してください。

- Windows以外の場合：NFSマウントを使用している場合は、`nolock`が有効になっていることを確認してください。
- SMBマウントを使用している場合は、`nobrl`が有効になっていることを確認してください。

### ダウンロードフォルダーのパーミッション

ログは次のようになります。

```none
2022-02-28 18:51:01.1|Error|DownloadedTracksImportService|Import failed, path does not exist or is not accessible by Lidarr: /data/downloads/music/Party of Two - Jasmine Guillory.mp3. Ensure the path exists and the user running Lidarr has the correct permissions to access this file/folder
```

*ソース*のパーミッションと所有権も確認してください。宛先の所有権とパーミッションにこだわりすぎることが簡単であり、パーミッション関連の問題の原因となる可能性がありますが、通常はソースです。ソースフォルダーが存在することを確認してください。所有権とパーミッションが、ダウンロードしたファイルをコピー/ハードリンクまたはコピー+削除/移動できるようにしていることを確認してください。実行するユーザーまたはグループは、ダウンロードフォルダーを読み取りおよび書き込みできる必要があります。

- Windowsユーザーの場合、これはサービスとして実行されていることによるものかもしれません：
  - Windowsサービスはデフォルトで「Local Service」アカウントで実行されますが、このアカウントは通常、手動で権限が割り当てられていない限り、ユーザーのホームディレクトリにアクセスできません。これは、ユーザーのホームディレクトリにダウンロードを設定しているダウンロードクライアントを使用する場合に特に関係します。
  - 「Local Service」は一般的に非常に制限された権限を持っています。したがって、ユーザーがログインしたままであれば、システムトレイアプリケーションとしてアプリをインストールすることをお勧めします。インストーラーで提供されるオプションです。サービスからトレイアプリに変換する方法については、FAQを参照してください。

- Synologyユーザーは、[SynoCommunityのパッケージの権限管理に関する記事](https://github.com/SynoCommunity/spksrc/wiki/Permission-Management)を参照してください。

- Windows以外の場合：NFSマウントを使用している場合は、`nolock`が有効になっていることを確認してください。
- SMBマウントを使用している場合は、`nobrl`が有効になっていることを確認してください。

### ダウンロードフォルダーとライブラリフォルダーが同じフォルダーではない

ダウンロードクライアントは、\*Arrがアクセスできるフォルダーにダウンロードし、ルート/ライブラリフォルダーではないフォルダーにインポートするように設定する必要があります。

直接ルートフォルダーにダウンロードしないでください。また、ルートフォルダーをダウンロードクライアントの完了フォルダーまたは不完全なフォルダーとして使用しないでください。

[**これはシステムのヘルスチェックでも発生します**](/lidarr/system#downloading-into-root-folder)

アプリケーション内では、ルートフォルダーは設定されたメディアライブラリフォルダーと定義されます。これはマウントのルートフォルダーではありません。ダウンロードクライアントは、ルート（ライブラリ）フォルダーに完了したダウンロードまたは移動している場合、またはNZBGet/SABnzbdがソートを有効にしてルートフォルダーにソートしている場合、エラーが発生します。ダウンロードクライアントがダウンロードをルートフォルダーに配置するか、NZBGet/SABnzbdがソートを有効にしてルートフォルダーにソートする場合、ダウンロードクライアントのカテゴリがルートフォルダーに設定されている場合など、これは頻繁に問題を引き起こし、推奨されません。これを修正するには、ダウンロードクライアントをルートフォルダーにダウンロードしないように変更してください。なお、このチェックは、現在使用されているルートフォルダーだけでなく、定義/設定されたすべてのルートフォルダーを確認します。つまり、ダウンロードクライアントがダウンロードまたは完了したダウンロードを配置するフォルダーは、\*Arrアプリケーションで設定したルート/ライブラリ/最終メディアの宛先フォルダーと同じであってはなりません。
- 設定されたルートフォルダー（ライブラリフォルダー）は、[設定 => メディア管理 => ルートフォルダー](/lidarr/settings/#root-folders)で見つけることができます。
- 例えば、ダウンロードが`\data\downloads`に行く場合、ルートフォルダーは`\data\downloads`と設定されている可能性があります。
- ルートフォルダー/ライブラリに直接ダウンロードしないようにしてください。
{.is-warning}

### カテゴリが間違っている

Lidarrは、自分自身のダウンロードのみを処理するためにカテゴリを使用するように設定する必要があります。トレントが正しいカテゴリで追加されることはまれですが、それが起こることがあります。手動でトレントを追加して処理したい場合は、正しいカテゴリを設定する必要があります。いつでも設定できます。なぜなら、はダウンロードを毎分処理しようとするからです。

### パックされたトレント

ログには次のようなエラーが表示されます。

```none
No files found are eligible for import
```

トレントが`.rar`ファイルでパックされている場合、展開を設定する必要があります。[Unpackerr](https://github.com/unpackerr/unpackerr)をお勧めします。これにより、破損した部分的なインポートが防止され、インポート後に展開されたファイルがきれいになります。

また、フォルダーに有効なメディアファイルがない場合、エラーが表示される場合もあります。

### 繰り返しのダウンロード

繰り返しのダウンロードの原因はいくつかありますが、1つはリリースプロファイルのインデクサ制限に関連しています。インデクサはデータと一緒に保存されないため、メディアライブラリ内のアイテムに対しては優先ワードスコアが*ゼロ*になりますが、「RSS」および検索時には適用されます。これにより、アップグレードのように見えてダウンロードを繰り返し、その後アップグレードではなくなり、再び表示されてアップグレードのように見え、その後アップグレードではないようになるループに入ることがあります。リリースプロファイルをインデクサに制限しないでください。

これは、ダウンロードが実際にインポートされず、キューから欠落しているため、新しいダウンロードが永遠に取得されず、インポートされない場合もあります。これに関しては、他のさまざまな一般的な問題とトラブルシューティング手順を参照してください。

### Usenetダウンロードがインポートされない

Lidarrは、SABnzbdとNZBGetの60件の最新のダウンロードのみを参照するため、履歴を*保持*する場合、大量のキューでインポートの問題が発生すると、ダウンロードが黙って見落とされ、インポートされないことがあります。これを回避するための最良の方法は、履歴をクリアし続けることです。表示されるアイテムについては、調査が必要です。これを実現するには、完了および失敗したダウンロードハンドラーの下の「削除」を有効にします。NZBGetでは、これによりアイテムが*非表示*の履歴に移動します。残念ながら、SABnzbdには類似の機能はありません。そこで、nzbバックアップフォルダーを使用することができます。

### ダウンロードクライアントがアイテムをクリアしてしまう



ダウンロードクライアントは、ダウンロードの削除には責任を持たないでください。Usenetクライアントは、履歴からダウンロードを削除しないように設定する必要があります。Torrentクライアントは、シーディングが終了したらトレントを削除するのではなく、一時停止または停止するように設定する必要があります。これは、ダウンロードクライアントと通信して何をインポートするかを知るためであり、削除されている場合はインポートするものがないため、ファイルがいっぱいのフォルダがあってもインポートされません。

SABnzbdでは、これは履歴保持設定で処理されます。

### ライブラリアイテムにダウンロードがマッチしない

さまざまな理由で、リリースは取得された後に解析できず、ダウンロードクライアントに送信されます。Activity => Options => Show Unknown（最近のビルドではデフォルトで有効になっています）を使用すると、\*Arrのダウンロードクライアントカテゴリ内で無視されない/すでにインポートされていないすべてのアイテムが表示されます。これらは通常、手動でマッピングしてインポートする必要があります。

これは、ダウンロードクライアントにリリースがあるが、そのメディアアイテム（映画/エピソード/本/曲）がアプリケーションに存在しない場合にも発生する可能性があります。

### The underlying connection was closed: An unexpected error occurred on a send

これは、インデクサが現在の.NETバージョンでサポートされていないSSLプロトコルを使用しているため、[Radarr => System => Status](/radarr/system#status)で発見されたエラーです。

### The request timed out

Lidarrはクライアントからの応答を受け取っていません。

```none
    System.NET.WebException: The request timed out: ’https://example.org/api?t=caps&apikey=(removed) —> System.NET.WebException: The request timed out
```

```none
2022-11-01 10:16:54.3|Warn|Newznab|Unable to connect to indexer

[v4.3.0.6671] System.Threading.Tasks.TaskCanceledException: A task was canceled.
```

これは次の原因でも発生する可能性があります。

- VPNの設定が正しくないか使用されている
- プロキシの設定が正しくないか使用されている
- ローカルのDNSの問題 - 異なるDNSプロバイダに変更してみてください
- ローカルのIPv6の問題 - 通常、IPv6は有効になっていますが、機能していません
- Privoxyの使用とその設定が正しくない

## リストされていない問題

また、一般的なアクセス許可とネットワーキングのトラブルシューティングコマンドについては、[ガイド](/permissions-and-networking)を参照することもできます。それ以外の場合は、discordのサポートチームと相談してください。これが一般的な問題である可能性がある場合は、ウィキに追加することを提案してください。

# インデクサとトラッカーの検索

- [Prowlarr](/prowlarr)を使用している場合、Prowlarrが受信したすべてのクエリの[履歴](/prowlarr/history)と、それらがどのようにサイトに送信されたかを表示できます。Prowlarr History => Optionsで`Parameters`が有効になっていることを確認してください。詳細については(i)アイコンを参照してください。

## ロギングをトレースレベルに設定する

> **最初のステップは、ログをトレースレベルに設定することです。ログの調整と検索の詳細については、[ログとログファイル](#logging-and-log-files)を参照してください。問題を再現し、その時間枠のトレースレベルのログを使用して問題を調査します。**誰かが助けてくれる場合は、前後のコンテキストを[pastebin](https://0bin.net)、[Gist](https://gist.com)、または類似のサイトに入れて表示します。ファイル全体である必要はありませんし、エラーだけではありません。また、ログファイルにスパムを送るタスクが実行されていない状態で問題を再現する必要があります。
{.is-danger}

## インデクサまたはトラッカーのテスト

インデクサまたはトラッカーをテストすると、デバッグまたはトレースログで使用されたURLを見つけることができます。以下は成功したテストの例です。特定のURLと特定のパラメータを使用してインデクサにクエリを送信し、その応答を表示します。このURLをブラウザで試してみてください。`apikey=(removed)`を正しいapikey（例：`apikey=123`）に置き換えます。動作しますか？期待される結果が表示されますか？このFAQエントリは適用されますか？このURLでは、`cat=5030,5040,5045,5080`という特定のカテゴリが設定されていることがわかります。したがって、期待される結果が表示されない場合、これが1つの可能性です。また、`tvdbid=354629`というtvdbidで検索していることもわかります。したがって、エピソードがインデクサで正しく分類されていない場合、修正する必要があります。また、`season=1`と`ep=1`で特定のシーズンとエピソードで検索していることもわかります。したがって、インデクサでそれが正しくない場合、それらの結果は表示されません。動作するクエリの出力の例については、Manual Search XML Outputを参照してください。

- Manual Search XML Output

```xml
INDEXER SEARCH RESPONSE EXAMPLE NEEDED
```

***画像が必要***

![searches-indexers-and-trackers1.png](/assets/lidarr/searches-indexers-and-trackers1.png)
![searches-indexers-and-trackers2.png](/assets/lidarr/searches-indexers-and-trackers2.png)

- Trace Log Snippet

```none
Snippet of Trace Log for a Manual Search Needed
```

- Full Trace Log of a Search

```none
Full section of Trace Log for a Manual Search Needed
```

## 一般的な問題

以下は一般的な問題のいくつかです。

### メディアが監視されていない

曲が監視されていません。

### トラッカーがRawSearch Capsを必要としています

- Lidarrは「Kikis Delivery Service」を検索していますが、トラッカーには「Kiki's Delivery Service」の結果しかありません。
- これは、トラッカーが通常の標準化された検索をサポートしていないためです。
- 解決策は、トラッカーの定義の検索機能を更新し、`RawSearch`が必要でサポートされていることを示すようにすることです。
- Jackettはこのフラグをサポートしていますが、機能を追加するためにJackettに機能リクエストをオープンする必要があります。
- Prowlarrもこのフラグをサポートしていますが、機能を追加するためにProwlarrに機能リクエストをオープンする必要があります。

### カテゴリが間違っています

カテゴリが間違っていることは、インデクサ/トラッカーのマニュアル検索結果に表示されるが、.では表示されない結果の最も一般的な原因です。インデクサ/トラッカーは、検索結果にカテゴリを表示するはずであり、これが何が欠けているかを特定するのに役立ちます。JackettやProwlarrを使用している場合、各トラッカーには特定にサポートされているカテゴリのリストがあります。カテゴリを編集する際にブラウザウィンドウでリストを表示すると便利です。

### 間違った結果

インデクサは、完全に関連のない結果を返すことがあります。はパラメータを絞り込んで検索を行いますが、返される結果は完全に関連のないものです。または、一部の間違った結果を含むこともあります。前者は通常、インデクサの問題であり、トレースログから原因を特定できます。そのインデクサを無効にして問題を報告できます。後者は通常、カテゴリが正しくないリリースであり、インデクサ/トラッカーで報告できるものです。

### クエリは成功しましたが、結果が返されませんでした

「クエリは成功しましたが、インデクサから結果が返されませんでした。これはインデクサまたはインデクサのカテゴリ設定の問題かもしれません。」というメッセージが表示される場合、

これは、インデクサが構成したカテゴリに含まれる結果をインデクサが返さなかったためです。

### 結果が見つかりません

Lidarrに表示されないが、サイトで見つかる結果がある場合、次のいくつかの可能性が考えられます。

- [カテゴリが間違っている-上記を参照](#wrong-categories)
- IDベースの検索が行われ、インデクサがリリースを正しくそのIDにマッピングしていない場合。これはインデクサだけが解決できる問題です。彼らはリリースが正しい適用可能なIDにマッピングされるようにする必要があります。
- Lidarrが検索している方法と同じ方法で検索していない場合。おそらく、インデクサで検索している用語がLidarrがクエリを行っている方法ではない可能性が高いです。Trace LogsからLidarrがクエリをどのように行っているかを確認できます。テキストベースのクエリは一般的に`q=words%20and%20things%20here`の形式であり、この文字列はHTTPエンコードされており、オンラインのHTMLエンコード/デコードツールで簡単にデコードできます。

### 証明書の検証

ほとんどのインデクサ/トラッカーにはhttps経由で接続する必要があるため、システム上で正常に機能する必要があります。つまり、タイムゾーンと時刻の両方が*正しく*設定されている必要があります。また、システムの証明書も最新である必要があります。

### レート制限に達する

VPNやプロキシを使用して実行している場合、他の多くの人々と競合しているかもしれません。その場合、、theXEM、および/またはインデクサとトラッカーのようなサービスを使用しようとする10人、100人、または1000人以上の人々と競合する可能性があります。レート制限とDDOS保護は、IPアドレスによって行われることが多く、VPN/プロキシの出口ポイントは*1つの*IPアドレスです。中国、オーストラリア、南アフリカなどの抑圧的な国以外では、VPN/プロキシは必要ありません。

RarbgはAPI内でレート制限が発生する傾向があり、結果が表示されないと表示されます。

### IP禁止

レート制限と同様に、特定のインデクサ（例：Nyaa）などはIPアドレスを完全に禁止する場合があります。これは通常、半永久的なものであり、解決策はISPまたはVPNプロバイダから新しいIPを取得することです。

### Jackettの/allエンドポイントの使用

Jackettの`/all`エンドポイントは便利ですが、それが唯一の利点です。それ以外は潜在的な問題がありますので、個々のトラッカーを追加する必要があります。または、Jackett & NZBHydra2の代替である[Prowlarr](/prowlarr)をチェックすることもできます。

[Jackett自体も/allは避けるべきであり、使用すべきではありません。](https://github.com/Jackett/Jackett#aggregate-indexers)

/allエンドポイントの使用には利点はありません（管理のオーバーヘッドが削減されること以外）、デメリットのみがあります。

- インデクサ固有の設定（カテゴリ、検索モードなど）を制御できなくなります。
- 検索モード（IMDB、クエリなど）を混在させると、品質の低い結果が発生する可能性があります。
- インデクサ固有のカテゴリ（\>= 100000）は使用できません。
- 遅いインデクサは全体の結果を遅くします。
- 合計結果は1000に制限されます。

Jackettにさらにトラッカーを追加するにつれて、結果が切り取られる可能性がますます高くなるため、各インデクサはページネーションがサポートされている場合は1000件、サポートされていない場合は100件に制限されます。最後に、`/all`の中の*1つ*のトラッカーがエラーを返すと、はそれを無効にして結果が表示されなくなります。

### 単一のエントリとしてのNZBHydra2の使用

NZBHydra2を単一のインデクサエントリ（つまり、NZBHydra2の複数のインデクサに対する1つのNZBHydra2エントリ）として使用する場合、Jackettの`/all`エンドポイントと同じ問題が発生します。

### リストされていない問題

また、一般的なアクセス許可とネットワーキングのトラブルシューティングコマンドについては、[ガイド](/permissions-and-networking)を参照することもできます。それ以外の場合は、discordのサポートチームと相談してください。これが一般的な問題である可能性がある場合は、ウィキに追加することを提案してください。

## エラー

インデクサを追加する際に表示される一般的なエラーのいくつかは次のとおりです。

### The underlying connection was closed: An unexpected error occurred on a send

これは、インデクサが現在の.NETバージョンでサポートされていないSSLプロトコルを使用しているため、[Lidarr => System => Status](/lidarr/system#status)で発見されたエラーです。

### The request timed out

Lidarrはインデクサから応答を受け取っていません。

```none
    System.NET.WebException: The request timed out: ’https://example.org/api?t=caps&apikey=(removed) —> System.NET.WebException: The request timed out
```

```none
2022-11-01 10:16:54.3|Warn|Newznab|Unable to connect to indexer

[v4.3.0.6671] System.Threading.Tasks.TaskCanceledException: A task was canceled.
```

これは次の原因でも発生する可能性があります。

- VPNの設定が正しくないか使用されている
- プロキシの設定が正しくないか使用されている
- ローカルのDNSの問題 - 異なるDNSプロバイダに変更してみてください
- ローカルのIPv6の問題 - 通常、IPv6は有効になっていますが、機能していません
- Privoxyの使用とその設定が正しくない