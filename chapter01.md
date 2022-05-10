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

# 第１章 データ基盤におけるデータ セキュリティの重要性
<hr style="height:1px; background-color:#c0c0c0;">
大量のデータの利活用を前提にした DX の推進が求められる時代。データ利活用にはセキュリティを担保することも要求され、多層防御の中で、データの格納先であり、データの源泉であるデータ基盤でのセキュリティの重要性が高まっています。
まずは、データ セキュリティの全体像を紹介します。

## 1. NIST CSF（Cyber Security Framework）コア機能と Azure での対応
企業・組織が サイバーセキュリティ対策を向上させるための指針として、ISMS、CIS Controls、PCI DSS、NIST CSF などが活用されます。
データ基盤である SQL Database、Azure Synapse Analytics でもこれらのフレームワークを元にセキュリティ対策を実施することが求められます。

「重要インフラのサイバーセキュリティ対策を改善するためのフレームワーク」である [NIST CSF（Cyber Security Framework）は、IPA より翻訳版](https://www.ipa.go.jp/files/000071204.pdf)が公開されており、世界で多くの企業・組織で活用されています。
その 5 つのコア機能に対して、データ基盤 SQL Database, Azure Synapse Analytics での主な対策と利用できるサービスは以下のようになります。

 <table border="1">
    <tr>
      <th width="15%">機能</th>
      <th width="25%">内容</th>
      <th width="30%">Azure データ基盤での対応</th>
      <th width="30%">活用が可能なサービス</th>
    </tr>
    <tr>
      <td>識別・評価<br>Identify</td>
      <td>脅威検出／データ資産評価</td>
      <td>データ識別・分類、脆弱性評価</td>
      <td>Microsoft Purview Data Catalog（データ識別・分類）<br>Microsoft Sentinel（定期分析）<br>Microsoft Defender for SQL</td>
    </tr>
    <tr>
      <td rowspan="4">防御<br>Protect</td>
      <td>ネットワーク セキュリティ</td>
      <td>構成（VNET, プライベート リンク）<br>FW<br>IPS・IDS</td>
      <td rowspan="4"> </td>
    </tr>
    <tr>
      <td>認証</td>
      <td>ユーザー認証（AAD 認証／SQL 認証）</td>
    </tr>
    <tr>
      <td>アクセス制御</td>
      <td>DB でのアクセス制御設定（ロール、オブジェクト、行、列）<br>マスキング</td>
    </tr>
    <tr>
      <td>データ保護</td>
      <td>暗号化（NW 及び DB の暗号化）</td>
    </tr>
    <tr>
      <td>検知<br>Detect</td>
      <td>ログ モニタリング<br>フォレンジック</td>
      <td>データ識別・分類、脆弱性評価</td>
      <td>Microsoft Defender for SQL</td>
    </tr>
    <tr>
      <td>対応<br>Respond</td>
      <td>対応計画の作成、コミュニケーション、分析、低減、改善</td>
      <td> </td>
      <td>Microsoft Sentinel（インシデント対応）</td>
    </tr>
    <tr>
      <td>復旧<br>Recover</td>
      <td>復旧計画の作成、改善、コミュニケーション</td>
      <td> </td>
      <td> </td>
    </tr>
 </table>



※[NIST CSF（Cyber Security Framework）における機能とカテゴリーの識別子（IPA）](https://www.ipa.go.jp/files/000071204.pdf)

<br>

1. 識別・評価（ Identify ）

      セキュリティ対策の対象を識別し、脆弱性の評価を行うことがまず求められます。すべてのリソース、データを対象とすることは不可能であり、対策の強度が適切でなくなります。

      セキュリティ対策を決定する際に、このプロセスは重要ですが、データを取り扱うシステム担当とセキュリティ担当との間での連携が必要であり、その識別の難しさもあいまって、とりあえず全部を対象にしたい、といった要求がされることはよくあることと思います。またシステムは変化し、追加削除も行われるため、常に評価をアップデートし続けることが求められます。

2. 防御（ Protect ）

      守るべきデータ資産とその脆弱性に応じて、必要十分な防御対策を行います。

      防御においては、明らかにリスクであり不正と識別されるものを排除し、データ資産にアクセスさせないことになります。

      ここでは、ネットワークの境界防御がわかりやすく、ほとんどの企業、システムで最低限の対策として行われるものです。

      それに加えて、データ基盤では、データ基盤が提供するアクセス制御を適切に組み込むことを意識し設計する必要があります。

3. 検知（ Detect ）

      防御対策だけで 100% 守れるものではありません。防御をすり抜ける、不備を突く攻撃や、正当な操作の中に潜むリスクに対応する検知の対策も重要です。

      セキュリティ インシデントが起こることを前提として、データ基盤やシステム内での振る舞いを記録しログをモニタリングすることで、脅威やインシデント発生をいち早く検知し、被害を最小限に食い止めるための対応、復旧へとつなげていく必要があります。

     それぞれの防御対策が有効に機能しているか、新たな脆弱性がないか、といったセキュアな環境の維持のためにも欠かせません。

4. 対応（ Respond ）

      インシデント発生の予兆や、インシデント発生を検知するための組織としての対応体制を構築することが求められます。

5. 復旧（ Recover ）

<br>

![データ基盤のセキュリティ](/assets/IMG001_DatabaseSecurity_NIST_CSF.svg)

<br>

## 2. クラウド サービスでのセキュリティ

####Shared Responsibility の考え方
今や広く活用が進む、クラウド サービス。クラウド サービスでのセキュリティについて、Shared Responsibility の考え方は広く認識されるようになっています。

クラウド サービスとして提供される環境でのデータ資産に対するセキュリティについても、基本的な考え方である Shared Responsibility を確認し、データ基盤におけるデータ オーナーとしての責任を理解し対策を考えることが重要と言えます。

逆に、クラウド サービスを活用することで、クラウド プロバイダーに責任をシフトすることができ、すべての セキュリティリスクへ対応するために必要な膨大なリソースを、より効果的な対応に集中することができます。

ただし、クラウド環境のデプロイの種類に関係なく、以下については、<strong>利用者・ユーザーがすべて責任を負う</strong>ことを理解しなければなりません。

* <strong>データ
* エンドポイント
* Account
* アクセス管理</strong>

データ基盤では基本的にユーザー側にその責任があることを認識することが重要です。
<br>

![Shared Responsibility](/assets/IMG002_SharedResponsibility.svg)

<https://docs.microsoft.com/ja-jp/azure/security/fundamentals/shared-responsibility>

<br>

### Azure SQL Database 用の Azure セキュリティ ベースラインの活用
クラウド ベンダーから提供されているベスト プラクティスを活用することで、セキュリティ対応を一から設計し対策を構築するよりも、早くそして確実にセキュアなデータ基盤を構築、運用することができます。

**Azure SQL Database 用の Azure セキュリティ ベースライン**
<https://docs.microsoft.com/ja-jp/security/benchmark/azure/baselines/sql-database-security-baseline>

      ネットワークのセキュリティ
         NS-1:　内部トラフィック用のセキュリティを実装する
         NS-2:　プライベート ネットワークをまとめて接続する
         NS-3:　Azure サービスへのプライベート ネットワーク アクセスを確立する
         NS-6:　ネットワーク セキュリティ規則を簡略化する
         NS-7:　セキュリティで保護されたドメイン ネーム サービス ( DNS )
      ID 管理
        IM-1:　Azure Active Directory を中央 ID および認証システムとして標準化する
        IM-2:　アプリケーション ID を安全かつ自動的に管理する
        IM-3:　アプリケーションのアクセスに Azure AD シングル サインオン ( SSO ) を使用する
        IM-7:　意図しない資格情報の公開を排除する
      特権アクセス
        PA-1:　高い特権を持つユーザーを保護および制限する
        PA-3:　ユーザー アクセスを定期的に確認して調整する
        PA-6:　特権アクセス ワークステーションを使用する
        PA-7:　Just Enough Administration (最小限の特権の原則) に従う
        PA-8:　Microsoft サポートの承認プロセスを選択する
      アセット管理
        AM-1:　セキュリティ チームが資産のリスクを確実に可視化できるようにする
        AM-2:　セキュリティ チームが資産インベントリとメタデータに確実にアクセスできるようにする
        AM-3:　承認された Azure サービスのみを使用する
      ログと脅威検出
        LT-1:　Azure リソースの脅威検出を有効にする
        LT-2:　Azure ID とアクセスの管理のために脅威検出を有効にする
        LT-3:　Azure ネットワーク アクティビティのログ記録を有効にする
        LT-4:　Azure リソースのログ記録を有効にする
        LT-5:　セキュリティ ログの管理と分析を一元化する
        LT-6:　ログの保持期間を構成する
        LT-7:　承認された時刻同期ソースを使用する
      体制と脆弱性の管理
        PV-1:　Azure サービスのセキュリティで保護された構成を確立する
        PV-2:　Azure サービスのセキュリティで保護された構成を維持する
        PV-3:　コンピューティング リソースにセキュリティで保護された構成を確立する
        PV-8:　定期的に攻撃シミュレーションを実施する
      エンドポイント セキュリティ
        ES-2:　一元管理された最新のマルウェア対策ソフトウェアを使用する
        ES-3:　マルウェア対策ソフトウェアと署名が確実に更新されるようにする
      バックアップと回復
        BR-1:　定期的な自動バックアップを保証する
        BR-2:　バックアップ データを暗号化する
        BR-3:　カスタマー マネージド キーを含むすべてのバックアップを検証する
        BR-4:　キー紛失のリスクを軽減する

<br><br>

