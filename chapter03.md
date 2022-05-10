<!-- 表の基本スタイル -->
<style>
table[border="1"]{
	border-spacing:0;
	margin-top: 5px;
	margin-bottom: 5px;
	border: none;
  width: 800px; /* 表サイズ */
}

table[border="1"] td,table[border="1"] th{
	padding:5px 8px;
	background:#FFF;
	border: none;
	border-top: 1px solid #999;
	border-left: 1px solid #999;
}

table[border="1"] th{
	background:#f9f9f9;
}
table[border="1"] tr:last-child th,table[border="1"] tr:last-child td{
    border-bottom: 1px solid #999;
}
table[border="1"] th:last-child,table[border="1"] td:last-child{
    border-right: 1px solid #999;
}

.tbl{
    width: 800px;
}

.listtbl,.listtbl td,.listtbl th{
    border-right: none !important;
    border-left: none !important;
}

.memotbl,.memotbl td,.memotbl th{
    border-right: none !important;
    border-left: none !important;
}

</style>
<!-------------------->

# 第３章 Microsoft Defender for SQL で実現するデータベース セキュリティ
<hr style="height:1px; background-color:#c0c0c0;">

データ基盤でのデータ セキュリティを実現し運用し続けるためには、時間もコストもかかることがネックとなります。セキュリティの中でもデータ基盤レイヤでの対策を理解した要員、体制を維持することはハードルが高いのが現実です。

Microsoft Defender for SQL は、データ基盤で効果的なセキュリティを効率的に実現します。

<br>

#### <u> Microsoft Defender for SQL で実現できること </u>

##### 1. セキュリティ インシデントの検知・アラート（監査）　[「SQL Advanced Threat Protection」](#1-sql-advanced-threat-protection)
##### 2. 脆弱性の診断と推奨アクションの提起　[「SQL 脆弱性評価」](#2-sql-脆弱性評価)

<br>

## 1. SQL Advanced Threat Protection
<https://docs.microsoft.com/ja-jp/azure/azure-sql/database/threat-detection-overview>

セキュリティ対策の中で「検知」対策はあまり重要なものと意識されてきませんでしたが、セキュリティインシデントが起こることを前提にした多層防御が求められる中、特にデータ基盤での「検知」対策は必ず実査すべきものといえます。

何をログとして取得すればよいのか、また取得する方法がわからないためログすらも取得しない、あるいはログを取得しても労力のわりに成果が形になって表れることが少なく、結果的に、ログを取得するだけでモニタリングまで行えていない、となりがちです。

そういった「検知」対策の悩みにこたえるインテリジェントなサービスが、Microsoft Defender for SQL の Advanced Threat Protection です。

![Advanced Threat Protection 何が実現できるのか](/assets/IMG009_CheckIcon.png)<strong> 何が実現できるのか？</strong>

データ基盤、データベースでのリスクである、不審なデータベース アクティビティ、潜在的な脆弱性、SQL インジェクション攻撃や、異常なデータベース アクセスやクエリのパターンを、異常なアクティビティとして検知し、セキュリティ アラートを上げます。

さらに、Microsoft Defender for Cloud に統合して管理することで、不審なアクティビティの詳細と、脅威の調査や危険性の軽減のために推奨される対処方法まで提示されます。

![Advanced Threat Protection どんなメリットがあるのか ](/assets/IMG009_CheckIcon.png)<strong> どんなメリットがあるのか？</strong>

こういったデータベース セキュリティに必要とされる、データベース セキュリティの専門的な知識、経験は必要なく誰でもどの SQL 環境でも利用できます。また、そのための高度に難易度の高い、セキュリティ監視システムを導入して管理する必要もありません。

![Advanced Threat Protection どうすれば利用できるのか ](/assets/IMG009_CheckIcon.png)<strong> どうすれば利用できるのか？</strong>

Microsoft Defender for SQL を有効にしていただくだけですぐに利用できるようになります。

また、より完全で高度な調査やリスク監視を実現する場合は、SQL の「監査」機能を有効にし、データベース イベントを Azure ストレージ アカウントに監査ログを書き込み、モニタリング範囲を広く深くしていただくことが推奨されます。

監査設定について
: Azure SQL Database と Azure Synapse の監査
<https://docs.microsoft.com/ja-jp/azure/azure-sql/database/auditing-overvie>
Azure SQL Managed Instance の監査
<https://docs.microsoft.com/ja-jp/azure/azure-sql/managed-instance/auditing-configure>

<br>

### Advanced Threat Protection のインテリジェントな分析手法

Defender for Cloud は、攻撃者によって脆弱性の悪用手法が次々に生み出され、複雑化していく中で、その検出アルゴリズムを迅速に更新し、脅威の環境の変化に対応しています。

Defender for Cloud では、誤検知を減らして真の脅威を検出するために、Azure のリソースやネットワークから、ログ データを収集し、分析、統合しています。接続されているパートナー ソリューション (ファイアウォールやエンドポイント保護ソリューションなど) とも連動。Defender for Cloud は、これら情報を分析し、複数の情報源から得た情報との関連性も探りながら、脅威を特定しています。

<p><img alt="Defender for Cloud Data collection and presentation" src="/assets/IMG010_DefenderForCloudDataCollectionPresentation.png" width="434" height="476"></p>

Defender for Cloud では、シグネチャ ベースの手法とは比較にならない高度なセキュリティ分析を利用できます。ビッグ データや機械学習といった革新的なテクノロジーでクラウド環境全体にわたってあらゆるイベントを評価します。
手作業に頼った手法、これまでの攻撃の進化を予測する手法では特定できない脅威でも検出することができるのです。

<br>

###  1.1. Microsoft Defender for SQL を有効にする
Azure、ハイブリッド、その他のクラウド プラットフォームで実行されているワークロードのセキュリティ体制管理と脅威保護のためのツール Microsoft Defender for Cloud の中で、Microsoft Defender for SQL は高度な SQL セキュリティ機能のための統合パッケージです。
Microsoft Defender for Cloud は、Azure SQL Database、Azure SQL Managed Instance、Azure Synapse Analytics で使用可能です。データベースの潜在的な脆弱性の検出及び軽減する機能、データベースに対する脅威を示す異常な行動を検出する機能が含まれ、これらの機能を 1 つの場所で有効にし、管理することができます。

Microsoft Defender for Cloud の Microsoft Defender for SQL プランを ON にして有効にします。サブスクリプション レベル、リソース レベルで設定が可能です。

https://docs.microsoft.com/ja-jp/azure/azure-sql/database/azure-defender-for-sql

<br>

##### Azure ポータルでの「サブスクリプション レベル」での設定手順

1. サービスで、[ Microsoft Defender for Cloud ] を選択
[ 環境設定 ] から、サブスクリプション] の右のメニューから [ 設定の編集 ] をクリックして設定画面を開く 

<p><img alt="Defemder for Cloud 設定 ポータル メニュー" src="/assets/IMG011_DefenderSetting1.png"></p>

2. 「データベース」をオンにして保存します。

<p><img alt="Defemder for Cloud 設定" src="/assets/IMG013_DefenderSetting3.png"></p>

<br>

### 1.2. Advanced Threat Protection for Azure SQL Database を構成する

Azure portal で Advanced Threat Protection を設定・構成します。

PowerShell を使用して Advanced Threat Protection を設定することも可能です。

##### 1.2.1. Microsoft Defender for SQL がまだ有効になっていない場合は、[ Enable Microsoft Defender for SQL ] をチェックし有効にします。

<p><img alt="Microsoft Defender for SQL 設定1" src="/assets/IMG014_DefenderSQLSetting1.png"></p>

##### 1.2.2. [ 構成 ] をクリックし Microsoft Defender for SQL の構成を設定します。

<p><img alt="Microsoft Defender for SQL 設定2" src="/assets/IMG015_DefenderSQLSetting2.png"></p>

##### 1.2.3. [ Advanced Threat Protection 設定 ] で、[ Defender for Cloud のサブスクリプションのメール設定に連絡先の詳細を追加します ] をクリックして、通知の連絡先を指定します。

<p><img alt="Microsoft Defender for SQL 設定3" src="/assets/IMG016_DefenderSQLSetting3.png"></p>

◇ メールの受信者
異常なデータベース アクティビティの検出時に通知を受け取るユーザーを設定
・ロールで指定
・[ 追加のメール アドレス（コンマで区切って入力）]  
◇ [ 通知の種類 ] で通知送信を実行するアラートの重大度をカスタマイズする
<br>
[ 保存 ] して [ × ] で画面を終了します。

<br>

### 1.3. SQL Database と Azure Synapse Analytics での Advanced Threat Protection アラートの活用
<https://docs.microsoft.com/ja-jp/azure/defender-for-cloud/alerts-reference#alerts-sql-db-and-warehouse>

Microsoft Defender for SQL を有効にすることで、即座にアラートを活用することができます。

[「第２章 2. データ基盤、データベースでのリスクとセキュリティのポイント」](/chapter02.md/#2-データ基盤データベースでのリスクとセキュリティのポイント)で紹介したデータ基盤でのリスク例に対して、SQL Advanced Threat Protection のアラートがどのように対応できるかをご紹介します。

<br>

#### 【リスク１】SQLインジェクション

Web サイトコンテンツ管理システム（CMS）で提供された、コメントフォームなどに対するスパムをブロックするプラグインに SQL インジェクションの脆弱性があった。
ユーザーエージェントをデータベースの独自テーブルに格納するため、ユーザーが SQL クエリを準備するなどが必要で、その SQL 処理にユーザーが意図しない SQL 文を紛れ込ませるというもの。この脆弱性を利用することは比較的容易で、記事を書き換えたり、意図しない投稿がされたり、データベースを削除する、といったことが可能だった。

**Advanced Threat Protection のアラート**

「 SQL インジェクションの可能性」のアラートにより、テストフェーズで事前に検知したり、早期に攻撃を発見して対応を可能にします。

**※A possible vulnerability to SQL Injection（SQL インジェクションにつながる可能性のある脆弱性）** 
: 攻撃前 PreAttack　重要度 中

データベースでエラーのある SQL ステートメントが生成された。SQL インジェクション攻撃に対する脆弱性がある可能性を意味します。

* エラーのあるステートメントが生成される要因
  - アプリケーション コードの欠陥によって誤った SQL 文を生成
  - アプリケーション コードまたはストアド プロシージャで、SQL 文を生成する際にユーザー入力をサニタイズせず、SQL インジェクションに悪用される可能性のある誤った SQL 文を生成

**※SQL インジェクションの可能性**
: 攻撃前 PreAttack　重要度 高

SQL インジェクションの脆弱性が確認されたアプリケーションを攻撃する、アクティブなエクスプロイトが発生している。<br>
攻撃者が脆弱なアプリケーション コードまたはストアド プロシージャを使用して、悪意のある SQL 文の注入を試みていることを意味します。

<br>

#### 【リスク２】アカウントとパスワードの漏えい、搾取

広く公開される EC サイトで、ある日、大量の更新操作が記録され、データベースの更新ログ領域が爆発した。ユーザー アカウント・パスワードが奪取（広く知れ渡ったものでの辞書攻撃）されていて、当該アカウントによる大量の更新操作が行われたことによる被害だった。
購入行為ではなかったので、大きな問題にはならなかったが、アクセスしづらくなるなど、サービスへの影響が発生した。

**Advanced Threat Protection のアラート**

ブルートフォース攻撃の検知で、アカウント・パスワードの搾取を検知します。また、流出したアカウント・パスワードを使ったと思われる異常行動も監視します。

**※Suspected brute force attack（ブルート フォース攻撃の可能性）**
: 攻撃前 PreAttack　重要度 高

ブルートフォース攻撃の可能性を検出。

**※Suspected successful brute force attack（ブルート フォース攻撃が成功した可能性）**
: 攻撃前 PreAttack　重要度 高

明らかにブルートフォースアタックが行われた後、ログインに成功。

◇ Microsoft Sentinel でオリジナルなアラート ルールとして、以下のような検知ルールを作成することも効果的です。

・同一アカウントによる短時間での大量ログイン
・同一アカウントによる短時間での大量の SQL 実行

<br>

#### 【リスク３】内部リスク

システム運用を委託するグループ会社の派遣エンジニアによって、直接データベースから顧客個人情報を大量に取得し、名簿業者に複数回に渡って売却された。
組織的な問題として個人情報へのアクセス権を申請承認して付与する仕組みはあったが、アクセス権限の見直しが行われていなかった。また内部不正を想定しておらず、管理体制が十分ではなかった。
個人情報を細分化などして、アクセス権を細かく設定したり、データ使用目的別にマスキングしたりするなどのデータベースでのアクセス制御も十分ではなかった。データベースのアクセス ログは取得していたが、定期的にモニタリングされることはなく、流出した個人情報が転売先で利用されたことによって発覚した。

**Advanced Threat Protection のアラート**

大量のデータで、アカウント・パスワードの搾取を検知します。また、流出したアカウント・パスワードによる異常行動も監視します。

**※Unusual export location（通常とは異なるエクスポート場所）**
: 不正転送 Exfiltration　重要度 高

SQL Server から大量のデータを通常と異なる場所にエクスポート。

◇ Microsoft Sentinel でオリジナルなアラート ルールとして、以下のような検知ルールを作成することも効果的です。

・重要データのあるテーブルに対する、大量データの取得操作
・管理者など権限のある DB ユーザーによる操作のログは定期的に確認しておくことも重要です。

<br>

#### Microsoft Defender for SQL の Advanced Threat Protection のアラート リスト<br>
<https://docs.microsoft.com/ja-jp/azure/defender-for-cloud/alerts-reference>


 <table class="listtbl">
    <tr>
      <th>アラート（アラートの種類）</th>
      <th>攻撃戦術<br>MITRE tactics</th>
      <th>重要度</th>
    </tr>
    <tr>
      <td>A possible vulnerability to SQL Injection（SQL インジェクションにつながる可能性のある脆弱性）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Attension.png"> </td>
    </tr>
    <tr>
      <td>Attempted logon by a potentially harmful application（潜在的に有害なアプリケーションによりログオンが試行されました）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Log on from an unusual Azure Data Center（通常とは異なる Azure データ センターからのログオン）</td>
      <td align="center">探査<br>Probing</td>
      <td align="center"> <img src="/assets/IMG017_Notice.png"> </td>
    </tr>
    <tr>
      <td>Log on from an unusual location（通常とは異なる場所からのログオン）</td>
      <td align="center">悪用<br>Exploitation</td>
      <td align="center"> <img src="/assets/IMG017_Attension.png"> </td>
    </tr>
    <tr>
      <td>Login from a principal user not seen in 60 days（プリンシパル ユーザーからのログインが 60 日以内に確認されていません）</td>
      <td align="center">悪用<br>Exploitation</td>
      <td align="center"> <img src="/assets/IMG017_Attension.png"> </td>
    </tr>
    <tr>
      <td>Login from a suspicious IP（疑わしい IP からのログイン）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Attension.png"> </td>
    </tr>
    <tr>
      <td>Potential SQL Brute Force attempt（SQL ブルートフォース攻撃試行の可能性）</td>
      <td align="center">探査<br>Probing</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>SQL インジェクションの可能性</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Potentially Unsafe Action（安全でない可能性のあるアクション）</td>
      <td align="center">―</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Suspected brute force attack using a valid user（有効なユーザーを使用したブルート フォース攻撃の可能性）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Suspected brute force attack（ブルート フォース攻撃の可能性）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Suspected successful brute force attack（ブルート フォース攻撃が成功した可能性）</td>
      <td align="center">攻撃前<br>PreAttack</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
    <tr>
      <td>Unusual export location（通常とは異なるエクスポート場所）</td>
      <td align="center">不正転送<br>Exfiltration</td>
      <td align="center"> <img src="/assets/IMG017_Warning.png"> </td>
    </tr>
 </table>

  
<br><br>
<div style="background: #fff; border: 1px #ccc solid; box-shadow: 0 2px 3px 0 #ddd; font-size: 100%; padding: 20px;">
<span style="color:#000000;font-weight:bold;">Microsoft Sentinel で、以下のようなデータベースのログ監視、アラート ルール定義を活用できます。</span>
<ul>
  <li type="disc">Failed Logon Attempts on SQL Server　ログイン試行による失敗ログイン</li>
  <li type="disc">Failed Logon on SQL Server from Same IPAddress in Short time Span　同じ IP アドレスからの短時間でのログイン試行（失敗ログイン）</li>
  <li type="disc">Multiple Failed Logon on SQL Server in Short time Span　短時間での複数の失敗ログイン</li>
  <li type="disc">New User created on SQL Server　新規ユーザーの作成</li>
  <li type="disc">User added to SQL Server SecurityAdmin Group　セキュリティ管理者グループのユーザー作成</li>
  <li type="disc">SQL User deleted from Database　ユーザーの削除</li>
  <li type="disc">User removed from SQL Server SecurityAdmin Group　セキュリティ管理者グループからのユーザー削除</li>
  <li type="disc">User removed from SQL Server Roles　SQL Server ロールからのユーザー削除</li>
  <li type="disc">User Role altered on SQL Server　ユーザーのロール変更</li>
  <li type="disc">Response rows stateful anomaly on database - hunting query　異常な動的レコード応答</li>
  <li type="disc">Anomalous Query Execution Time　異常なクエリ実行回数</li>
  <li type="disc">Boolean Blind SQL Injection　ブール値ブラインドによる SQL インジェクション</li>
  <li type="disc">Prevalence Based SQL Query Size Anomaly　異常なサイズのクエリ率（割合）</li>
  <li type="disc">Suspicious SQL Stored Procedures　怪しいストアドプロシージャ</li>
  <li type="disc">Time Based SQL Query Size Anomaly　異常なサイズのクエリ実施時間</li>
  <li type="disc">Affected rows stateful anomaly on database - hunting query　異常に動的に影響を受けるレコード</li>
</ul>
</div>

<br>

### 1.4. 疑わしいイベントの検出とアラートの調査
セキュリティ アラートは、Azure Portal の Microsoft Defender for Cloud 概要ページ上部にある [ セキュリティ アラート ] で確認できます。また、これらのアラートへの対応も Azure Portal で行うことができます。

<https://docs.microsoft.com/ja-jp/azure/defender-for-cloud/managing-and-responding-alerts>

<p><img alt="Microsoft Defender for Cloud 概要" src="/assets/IMG018_SecurityAlert1.png"></p>

<p><img alt="セキュリティ アラート" src="/assets/IMG019_SecurityAlert2.png"></p>

<br><br>

## 2. SQL 脆弱性評価
<https://docs.microsoft.com/ja-jp/azure/azure-sql/database/sql-vulnerability-assessment?tabs=azure-powershell>

SQL 脆弱性評価は、データ基盤、データベースのセキュリティの状態を可視化するサービスです。セキュリティ プロセスにおける「識別・評価 Identify」の脆弱性評価として活用できます。

システム導入時点での評価だけでなく、運用フェーズでも、常に最新の状態を評価することは重要です。しかし、システムリリース後に常に監視しセキュリティ レベルをアップデートすることは困難です。リソースを割くことも難しくなります。

このサービスを利用することで、常に最新で最適なセキュリティの状態を維持することができます。

この脆弱性評価には、セキュリティの問題を解決し、データベースのセキュリティを強化するために実践できる手順も含まれていることもポイントです。

常に変化し変更の追跡が難しいデータベース環境を監視し、そのセキュリティ対応を維持しさらに改善します。

脆弱性評価は、Azure SQL Database に組み込まれているスキャン サービスで、セキュリティの脆弱性にフラグを付ける、ナレッジベースのルールを使います。

誤った設定、過剰なアクセスの許可設定、保護されていない機密データなど、データベース セキュリティのベスト プラクティスからの逸脱した状況を明らかにし警告します。

SQL 脆弱性評価のルールは Microsoft のベスト プラクティスに基づいて、データベース及びその中に格納された機微データにとって最大のリスクとなるセキュリティ問題に着目して定義されています。データベース レベルの問題と、サーバーのファイアウォール設定やサーバー レベルの権限などのサーバー レベルのセキュリティ問題の両方がカバーされます。

スキャンの結果には、各々の問題を解決するために実践できる手順が含まれ、またカスタマイズした修復用のスクリプトも適宜提供されます。また、初期にデフォルトで定義されるベースラインから、環境に応じて、次回以降に適用したいベースラインを再定義・設定することにより、環境に合わせて評価レポートをカスタマイズすることができます。

ベースラインの判定項目

* アクセス許可の構成

* 機能の構成

* データベース設定

<br>

### 2.1. 脆弱性評価を構成する

Azure portal で 脆弱性評価 を設定・構成します。

##### 2.1.1. Azure SQL Database、SQL Managed Instance データベース、または Azure Synapse の特定のリソースにアクセスし、[ セキュリティ ] > [ Microsoft Defender for Cloud ] をクリックして開きます。**

<p><img alt="脆弱性評価1" src="/assets/IMG020_VulnerabilityCheck1.png"></p>

##### 2.1.2. [ Microsoft Defender for SQL ] にある [ 構成 ] をクリックし、サーバー全体またはマネージド インスタンスの Microsoft Defender for SQL 設定画面を開きます。**

<p><img alt="脆弱性評価2" src="/assets/IMG021_VulnerabilityCheck2.png"></p>

<p><img alt="脆弱性評価3" src="/assets/IMG022_VulnerabilityCheck3.png"></p>

◇ストレージ アカウントの構成

データベースに対するスキャン結果が格納されるストレージ アカウントを構成します。

◇定期的なスキャンの設定

週単位のスキャンを自動的に実行するように脆弱性評価を構成する場合、[ 定期的な反復スキャン ] を [ オン ] に設定します。 

結果は、[ スキャン レポートの送信先 ] で指定したメール アドレスに送信されます。[ 管理者とサブスクリプションの所有者にもメール通知を送信する ] を有効にすると、管理者とサブスクリプションの所有者にもメール通知を送信することもできます。

オンデマンドでの脆弱性スキャンの実行も可能です。変更などがあった場合に実施することをお勧めします。

<br>

### 2.2. 脆弱性の修復
脆弱性スキャンを行った結果のレポートが Azure portal に表示されます。

レポートには次のものが表示されます。

- セキュリティ状態の概要
- 検出された問題の数
- リスクの重要度別の概要
- 詳細な調査の結果一覧

<p><img alt="脆弱性スキャン結果レポート" src="/assets/IMG023_VulnerabilityCheck4.png"></p>

<p><img alt="脆弱性スキャン結果詳細" src="/assets/IMG024_VulnerabilityCheck5.png"></p>

**検出された脆弱性を修復する**

脆弱性のスキャンの結果として問題があると判定された項目は「失敗したチェック」として一覧表示されます。

評価結果一覧には、（判定ポイントである）セキュリティ チェック、適用対象、セキュリティのカテゴリ、リスクの重要度が表示されています。評価結果一覧の項目をクリックすると詳細が表示されます。その内容を確認し、影響やセキュリティ チェックが失敗となった理由を把握しセキュリティ上で問題となるかどうかを判断します。

詳細ページには、問題の解決方法を説明する実行可能な修復情報も含まれています。

脆弱性のスキャンで使用される一連の組み込みルールは以下を参照してください。

SQL 脆弱性評価ルール リファレンス ガイド
<https://docs.microsoft.com/ja-jp/azure/azure-sql/database/sql-database-vulnerability-assessment-rules>

<br>

### 2.3. 拡張機能

* 評価レポートのエクスポート
    脆弱性をスキャンした結果を Excel レポートとして作成することができます。またこのレポートをダウンロードし、組織内やセキュリティ担当者間で共有することで、セキュリティの向上に役立てることも可能です。
<br>
* スキャン履歴の表示

    以前に実行されたすべての脆弱性スキャンの履歴と、それぞれのスキャンの詳細な結果を確認することができます。
<br>
* Microsoft Defender for Cloud で検出された特定の項目を無効にする (プレビュー)

    組織のニーズとして、検出結果を修復するのではなく無視する必要がある場合は、必要に応じて検出結果を無効にできます。
    例えば、重大度が中以下、パッチを適用できない、といった場合、その検出結果を無効化ルールで定義することで、検出結果の一覧には表示しないようにすることができます。
    無効化された検出結果は、セキュリティ スコアに影響を与えたり、不要なノイズを生成したりすることはありません。

<br><br>

## 3. 脅威検知とログ モニタリングのテスト

テストケースを使って、Advanced Threat Protection による脅威検知のアラートや、Microsoft Sentinel によるモニタリング レポートをすぐに体験することができます。
Microsoft から提供されている Shell や、検証のためのコマンド例をご紹介します。

「Azure VM 上の SQL Server」を対象にした場合、以下の、脅威アラート用サンプル操作のコマンドと、Sentinel でのモニタリング用の Hunting Query を使って簡単にテスト、検証いただけます。

#### 3.1. 脅威検知のアラートのテスト
Microsoft Defender for Cloud Blog [Validating Alerts on Microsoft Defender for SQL on machines](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/validating-alerts-on-microsoft-defender-for-sql-on-machines/ba-p/3070714) より、脅威となる操作を模擬的に実行し体感することができます。

https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/validating-alerts-on-microsoft-defender-for-sql-on-machines/ba-p/3070714

* 脅威検知の留意事項
ニアリアルタイムでの通知ですので、即時ではない場合があります。
過検知および大量の通知を抑えるため、内部で事後のイベントを通知しない設計になっているため、繰り返した場合には、アラートを上げないケースがあります。

<br>

##### 手順
1. 「Azure VM 上の SQL Server」を用意する
2.  Log Analytics agent を「Azure VM 上の SQL Server」に適用する
3.  Microsoft Defender for Cloud の環境を設定する
4. テスト用スクリプトを、対象の「Azure VM」上で PowerShell で「SqlAdvancedThreatProtectionShell」をインポートし、テストケースを実行する
<br>

###### ◆SQLインジェクション

インポートしたテストケース「Test-SqlAtpInjection」を実行します。

アラート メール例
<p><img alt="アラートメールイメージ" src="/assets/IMG025_AlrertMail1.png"></p>

<br>

###### ◆ブルートフォース

インポートしたテストケース「Test-SqlAtpBruteForce」を実行します。



sqlcmd ユーティリティを使ってログイン失敗を短時間に繰り返すことでも簡単にテストできます。
例えば、以下のような、パスワードエラーのログイン試行を 30 回程度実行すると、脅威が検知されアラートが実行されます。「Azure SQL (Managed Instance 含む)」でもご利用いただけます。

sqlcmd ユーティリティでのログイン試行例 :

      Sqlcmd -U dbuser -P 123456 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 123456789 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 12345 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P qwerty -S usersql.database.windows.net
      Sqlcmd -U dbuser -P password -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 12345678 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 111111 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 123123 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 1234567890 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 1234567 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P qwerty123 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 0 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 1q2w3e -S usersql.database.windows.net
      Sqlcmd -U dbuser -P aa12345678 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P abc123 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P password1 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 1234 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P qwertyuiop -S usersql.database.windows.net
      Sqlcmd -U dbuser -P 123321 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P password123 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass01 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass02 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass03 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass04 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass05 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass06 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass07 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass08 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass09 -S usersql.database.windows.net
      Sqlcmd -U dbuser -P pass10 -S usersql.database.windows.net


アラート メール例
<p><img alt="アラートメールイメージ" src="/assets/IMG026_AlrertMail2.png"></p>

<br><br>

<div style="margin:0em ;display:inline-block;position:relative;top:3px;padding:0 .5em;height:1.5em;line-height:1.5em;color:#ffffff;background:#800000;font-weight:bold;text-align:center;border-radius:5px 5px 0 0;">Tips : 安全は構築するもの</div><div style="background: #fff; border: 1px #ccc solid; box-shadow: 0 2px 3px 0 #ddd; font-size: 100%; padding: 20px;"> 
<span style="color:#ff0000;font-weight:bold;">攻撃は、その "隙" をつく！</span><br>
<span>「Azure VM 上の SQL Server」を作成から数時間たたないうちに、よく知られている DB ユーザーである、<strong>「sa」によるログイン試行</strong> のアラートを受信。<br>
Microsoft Sentinel で、ログイン失敗アクションを確認したところ「sa」によるログイン試行が数十回繰り返されていました。<br>
検証用の環境なので、特にアクセス元を制限せず、インターネットに公開されていた環境ですが、SQL Server 環境作成からわずかの間で、すぐにブルートフォース攻撃を受けるという危険性を実感しました。</span>
</div>

<br><br>

#### 3.2. モニタリング レポート

「Azure VM 上の SQL Server」と「Azure SQL データベース」では、監査設定方法が異なり、そのため監査ログの送信先、管理先が異なります。


「Azure VM 上の SQL Server」は、<strong>Event</strong> （Windows Eventsに書き込みするように設定されたSQL Audit events のログ）でログが確認できます。Microsoft Sentinel によるモニタリングについては「Azure VM 上の SQL Server」では Event のログを使って行うことができます。
以下のサイトを参考に、SQLEvent 関数を作成し [Huntging Query](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/monitoring-sql-server-with-azure-sentinel/ba-p/1502960) を利用してよくあるパターンのログ レポートを容易に確認することができます。
https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/monitoring-sql-server-with-azure-sentinel/ba-p/1502960

※「Azure SQL データベース」は、<strong>AzureDiagnostics</strong> でログが確認できます。Microsoft Sentinel によるモニタリングについては「Azure SQL データベース」では AzureDiagnostics のログを使って行うことができます。

「Azure VM 上の SQL Server」と「Azure SQL データベース」は、出力フォーマットが異なり、条件や出力カラムが異なっています。

ログイン失敗の例 （出力項目は一部の例です）：
* <strong>Event</strong> では、以下のように出力されます。
[ RenderedDescription ]
<span style="color:#ff0000;">Login failed</span> for user 'dbnusername'. Reason: Password did not match that for the login provided. [CLIENT: aaa.xxx.yyy.zzz] 
[ EventData ]
<Data>dbusername</Data><Data> Reason: Password did not match that for the login provided.</Data><Data> [CLIENT: aaa.xxx.yyy.zzz]</Data>
* <strong>AzureDiagnostics</strong> では、以下のように出力されます
[ action_id_s ]
<span style="color:#ff0000;">DBAF</span>
[ succeeded_s ]
FALSE
[ client_ip_s ]
aaa.xxx.yyy.zzz
[ server_principal_name_s ]
dbnusername
[ additional_information_s ]
<login_information><error_code>18456</error_code><error_state>8</error_state></login_information>









