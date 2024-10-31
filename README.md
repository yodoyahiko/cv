## 目次
1. 職務経歴概要
2. 主な業務経歴
3. 経験分野内容のまとめ
4. 使用経験のある機器・ソフトウェアのまとめ
5. 資格について
 
## 職務経歴概要
項番１から直近の経歴を記載
1. 2020年8月〜現在 株式会社カオナビにてSREとして参画中
2. 2018年9月〜2020年7月 アイレット株式会社 クラウドインテグレーション事業部　職種インフラエンジニア　APNプレミアムパートナーで正社員として参画
3. 2015年9月～2018年8月　パーソルテクノロジースタッフ株式会社　 正社員として就業 職種インフラエンジニア
    1. 2015年9月～2017年10月　富士フイルムソフトウエア株式会社 ECサイト・医療システムのインフラ設計・構築・運用プロジェクトに客先常駐として参画
    2. 2018年3月～2018年8月　クリエーションライン株式会社　クラウド構築・運用プロジェクトに客先常駐として参画
4. 2012年5月～2014年12月　株式会社ナバック　正社員として就業 職種フロントSE
5. 2011年7月～2011年10月　職業訓練学校 Webクリエーター科でHTML、CSS、Photoshop、Illustratorについて学ぶ
6. 2006年3月～2011年6月　個人事業主としてWebサイト立ち上げと運営

## 主な業務経歴

### 2020年11月〜現在　株式会社カオナビにてAWSを用いたHRTechインフラ基盤のSREを担当
- 期間2020年11月〜 (SRE)
- 役割：メンバー
- 体制：9名

##### 使用製品・技術
- クラウドAWS：EC2,RDS,ElastiCache(Redis),Athena,Savings Plans,Reserved Instance,ALB,Route53
- AWSデプロイツール：Terraform,Ansible
- バージョン管理ツール：GitLab
- プロジェクト管理ツール：JIRA
- コミュニケーションツール：Slack

#### S3バケットのストレージ容量最適化プロジェクト
- 期間：3ヶ月間
- 役割：要件定義・スケジュール管理・実装
- 体制：1名

##### 使用製品・技術
- クラウドAWS：S3,S3 Storage Lens
- AWSデプロイツール：Terraform
- バージョン管理ツール：GitLab
- スクリプト言語：Python

##### プロダクト課題提起・実施プロセス
- セキュリティやコンプライアンスに関するデータ保持期間の要件を確認。無作為にデータが無制限に保存されていることが課題としてあげられた。
- 過去のオブジェクト参照状況を調査
- コスト削減効果を定量的に算出
- 運用部隊と協議し、必要なデータ保持期間を決定

##### ソリューション立案とアプローチ
- 事前検証：S3バージョニング機能による削除オブジェクト付与によるよる2週間の影響確認
- 段階的な削除：不要オブジェクトの特定とPythonコードでの削除手順の標準化
- ライフサイクルの設定：将来的な自動削除ルールの実装

##### 設計・構築
- バケット全体設計：削除マーカーを削除と未完了のマルチパートアップロード削除
- 個別のプレフィックス設計:個別要件によるオブジェクトの有効期限切れ

##### 施策期待効果
- S3バケットの最適化を行い大幅なコスト削減
- Terraformで構成管理し設計・構築の標準化を実現
- 不用データ削除により66%コスト削減

### CloudWatch Logs保存期間最適化プロジェクト
- 期間：3ヶ月間
- 役割：要件定義・スケジュール管理・実装
- 体制：1名

##### 使用製品・技術
- クラウドAWS：CloudWatch Logs
- AWSデプロイツール：Terraform
- バージョン管理ツール：GitLab
- スクリプト言語：Python

##### プロダクト課題提起・実施プロセス
- 対象サービスのリストアップと保存期間の洗い出し不用ロググループの特定
- 保存期間設定スクリプトの作成と適用
- 各サービス・環境ごとの保存期間設定作業
- 削除スクリプトの作成
- 各サービス・環境ごとの不要ロググループの特定と削除

##### ソリューション立案とアプローチ
- CloudWatch Logsの保存期間最適化によるコスト削減
- ログ保存期間の標準化

##### 設計・構築
- 設定確認スクリプトによる無制限にデータ保存されているCloudWatch Logsロググループの特定機能
- terraformモジュールによるログ設定の一元管理

##### 施策期待効果
- 年間換算で約$1,460の削減効果と自動化による効果の永続化
- 複数サービスや環境におけるログ保存期間の標準化


#### サービスのオートスケーリング機能実装プロジェクト
- 期間：2ヶ月間
- 役割：要件確認・スケジュール管理・実装
- 体制：1名

##### 使用製品・技術
- クラウドAWS：EC2 Auto Scaling,CodeDeploy,Lambda(Python),EventBridge,SNS
- AWSデプロイツール：Terraform
- バージョン管理ツール：GitLab
- プロジェクト管理ツール：Redmine
- コミュニケーションツール：Slack

##### プロダクト課題提起
- サービスのデータ量は顧客数が増えていくことや大規模顧客などの増加に伴い年々増加傾向にあるのではないかと考えた。
- サービスはロードバランサーを透過するのでこの構成要素のデータを見れば前年比で今後どういう状態になっていくのか見える化ができると思い仮説実証し課題設定した。
- データから課題として前年比でアクセス数の増加やアクセスの継続性があったので今後負荷の高い期間において最大台数を長期間継続させるケースが発生する仮説を立てた。
- EC2を常時最大稼働台数並べると安定性が向上する一方で長期間インスタンスを起動させた場合EC2のAWSコストも前年比で約40%以上増加することが想定できた。

##### ソリューション立案
- 課題解決案として運用コストを最も低く、負荷に応じて動的にEC2の台数の増減できる仕組みを検討したがこちらは検討後に案から外した。
- 理由は運用チームがステージング環境と本番環境へblue/green デプロイメントを行っていて、EC2の自動の増減とデプロイが重複した場合、安定の信頼性を担保するためEC2の増減を優先させる処理が設計に入ってくることが想定としてあった。このときの問題点として、デプロイ待ちが発生し機能の追加の遅延などの別の課題が発生しうると思い日中の考慮事項をいくつか入れなければならない動的スケーリングは、別の運用コスト増加の懸念があり対象外とした。
- 次に運用で利用していない業務時間外のEC2の台数削減が出来ないかデータを確認した。ロードバランサーのメトリクスからサービスは日中に負荷が高く深夜は通年ほとんど使われてないことを観測できた。

##### 設計・構築
- AWSの機能のソリューションとして、スケジューリングでのオートスケーリング機能を実装すればAWSコストを抑えつつ日中のデプロイ運用にも影響なく安定稼働実現で三方良しの仕組み化が出来ると考え、設計・構築・テストを行った。
- blue/green デプロイメント上でのオートスケーリングは過去やったことがなく、想定より2倍程度考慮事項が増え難航したがテスト環境をterraformで構築したことにより破壊と想像を何度も早く行うことでスケジュール遅延なしに本番構築できた。
- オートスケーリングは運用保守担当者のいない夜間帯に動作するため、LambdaによるAutoScalingの監視を実装した。

##### 施策期待効果
施策の期待効果として約41%のコスト削減を行った。

#### 2021年1月〜2021年6月　AWSを用いたリモートワークでの開発ブラウザテスト環境構築
- 期間2021年1月〜2021年6月 （設計・構築）
- 役割：メンバー
- 体制：2名

##### 使用製品・技術
- クラウドAWS：VPC,NATGateway,EC2,Amazon WorkSpaces,AWS Managed Microsoft AD,NLB
- AWSデプロイツール：Terraform,Ansible,CodeCommit,CodePipeline,CodeBuild,CodeDeploy
- バージョン管理ツール：GitLab
- プロジェクト管理ツール：JIRA
- コミュニケーションツール：Slack

##### 2020年8月〜11月　AWSを用いたHRTechサーバーレスのサービスのインフラ設計・構築を担当
- 期間2020年8月～11月（設計・構築）
- 役割：メンバー
- 体制：2名

##### 使用製品・技術
- クラウドAWS：Route53,WAF,API Gateway,VPC,ALB,AWS Fargate,Lambda,ElastiCache(Redis),Lambda,S3
- AWSデプロイツール：Terraform
- バージョン管理ツール：GitLab
- プロジェクト管理ツール：JIRA
- コミュニケーションツール：Slack

### 2018年9月〜2020年7月　アイレット株式会社 クラウドインテグレーション事業部

#### AWSを用いたFinTechサービスのインフラ要件定義・設計を担当
- 期間2020年1月～〜2020年7月
- 役割：メンバー
- 体制：6名

##### 使用製品・技術
- クラウドAWS：WAF,ALB,AWS Fargate,Amazon MSK
- AWSデプロイツール：Terraform
- バージョン管理ツール：GitHub
- プロジェクト管理ツール：Backlog
- コミュニケーションツール：Slack

#### AWSを用いたWebサービスインフラ構築・運用を担当
- 期間2018年9月～2019年12月
- 役割：メンバー
- 体制：6名

##### 使用製品・技術
- OS：AamaoznLinux,CentOS,Windows
- クラウドAWS：Route53,WAF,CloudFront,VPC,ELB,ACM,EC2,ECS,RDS,S3,Amazon QuickSight
- バージョン管理ツール：GitHub
- プロジェクト管理ツール：Backlog
- コミュニケーションツール：Slack

### 2015年9月～2018年8月　パーソルテクノロジースタッフ株式会社

#### プライベートクラウドの運用プロジェクトを担当
- 期間2018年3月～2018年8月
- 役割：メンバー
- 体制：8名
- CloudStackのリグレッション試験
- CloudStackの障害試験
- CloudStackのエラーログ解析
- CloudStackでのサーバ構築

##### 使用製品・技術
- OS：WindwosServer、Linux
- ハイパーバイザー：VMware、KVM
- クラウド：CloudStack
- バージョン管理ツール：GitLab

##### ECサイト・医療システムのインフラ設計・構築・運用プロジェクトを担当
- 期間2015年9月～2017年10月
- 役割：メンバー
- 体制：11名
- サーバの脆弱性対応
- サーバの障害2次対応
- 詳細設計書作成
- 障害対応手順書作成
- ベンダーコントロール
- ロードバランサーの運用（BIG-IP）
- ファイヤーウォールの運用（BIG-IP）
- データベースサーバ運用（Oracle）
- データベースサーバ構築・運用（SQLSever）
- ストレージの運用（EMC isilon）
- パブリッククラウドでのサーバ構築・運用(WindwosServer、Linux)
- オンプレでのサーバ構築・運用
- サーバ監視設定（Zabbix、Nagios）
- 監視サーバ運用（Zabbix、Nagios）
- セキュリティ　ミドルウェアの脆弱性対応　ドメイン証明書更新

##### 使用製品・技術
- サーバ：WindwosServer2008、2012、CentOS、RedHat
- ミドルウェア ： Apache、IIS、SQLServer、Postfix
- ロードバランサー：BIG-IP
- ファイアーウォール：BIG-IP
- クラウド ： Microsoft Azure、Nifty Cloud
- 仮想環境 ： VMware、vSphere
- スクリプト ： Bash、PowerShell

### 2012年5月～2014年12月　株式会社ナバック

#### 不動産向け勘定・顧客管理システムのインフラ設計・構築・運用プロジェクト
- 期間2014年4月～2014年11月　
- 役割：リーダー　フロントSE
- 体制：4名　
- 拠点数：6店舗
- 要件定義・顧客折衝
- ベンダーコントロール
- サーバ設計・構築
- ネットワークLAN設計・構築

##### 使用製品・技術
- サーバ：WindwosServer2012、Linux
- データベース：SQLServer2012、MySQL

#### 不動産向けネットワーク運用・構築を担当
- 期間2013年6月～2014年4月　
- 役割：サブリーダー　フロントSE
- 体制：4名　
- 拠点数：10店舗
- 詳細設計
- 要件に基づき各種ネットワーク構築
- 設定資料に基づきCofingの作成、Cofingの設定

##### 使用製品・技術
- NW機器：NEC（IX2025）、Ruckus Wireless(ZoneFlex7343・ZoneDirector1100）

#### 不動産向け勘定・顧客管理システムのインフラ設計・構築・運用プロジェクトを担当　　
- 期間2013年7月～2013年10月　
- 役割：リーダー　フロントSE
- 体制：4名
- 要件定義・顧客折衝
- ベンダーコントロール
- サーバ設計・構築
- ネットワークLAN設計・構築
- POS連動の要件調整、構築、運用
- 障害発生時の原因切り分け

##### 使用製品・技術
- サーバ:Windows Server、Linux
- スイッチ：Catalyst 2960-L

#### 不動産向け勘定・顧客管理システムのインフラ構築・運用プロジェクトを担当
- 期間2013年10月～2013年7月　
- 役割：メンバー
- 体制：3名
- サーバ設定
- ルーター設定

##### 使用製品・技術
- サーバ:Windows Server、Linux
- ルーター:YAMAHA（RTX1200）

#### 社内システムのプロジェクトを担当
- 期間2013年1月～2014年12月　
- 役割：サブリーダー
- 体制：3名
- ISMS委員会の参加
- ルータの入替え、ルータのログの監視
- サーバのバックアップの監視
- パラメーターシート、ネットワーク物理構成図、ネットワーク論理構成図などのドキュメント管理

##### 使用製品・技術
- ルーター：YAMAHA（RTX810）
- スイッチ：Buffalo社製（BS-GS2048）
- アクセスポイント：Buffalo社製（WAPS-AG300H）
- サーバ：WindowsServer2008、CentOS


#### 不動産向け勘定・顧客管理システムのインフラの構築・運用プロジェクトを担当
- 期間2013年3月～2013年5月　
- 役割：メンバー
- 体制：3名
- サーバ設定
- 障害対応

##### 使用製品・技術
- Buffalo社製スイッチ（BS-GS2048）
- サーバ：WindowsServer2008、CentOS

#### 不動産向けシステム構築・運用のプロジェクトを担当
- 期間2013年5月～2013年7月　
- 役割：メンバー
- 体制：3名
- サーバ設定
- 障害対応

##### 使用製品・技術
- サーバ：Windows Server、CentOS
- KIOSK：NCR社製（自動チェックイン機KIOSK）

#### 不動産向け勘定・顧客管理システムの構築・運用　　
- 期間2013年1月～2013年3月　
- 役割：メンバー
- 体制：4名
- サーバ設定
- 障害対応

##### 使用製品・技術
- Windows Server
- CentOS
- NW機器：NEC（UNIVERGE SV9300）

#### Webサイト立ち上げと運営
- 期間2006年3月～2011年6月
- 役割：ディレクター（個人事業主）
- 体制：1名
- Webサイトの立ち上げ
- Webサイトの記事更新
- アクセス解析
- ドメイン更新
- VPSサーバ運用

##### 使用製品・技術
- WordPress、HTML、CSS、CentOS


## 経験分野内容のまとめ
- パブリッククラウドのコスト削減やシステム管理業務の最適化を行うSRE業務
- パブリッククラウドを利用したインフラの設計・構築・運用の経験
- プロジェクトのリーダー・サブリーダー経験
- フロントSEとして顧客折衝の経験
- ISMS（情報セキュリティマネジメントシステム）のシステム管理者

## 使用経験のある機器・ソフトウェア一覧
以上の経歴から使用経験のある機器・ソフトウェアは下記
### AWSコンポーネント
- Route 53
- WAF
- CloudFront
- VPC
- ELB
- ACM
- EC2
- ECS
- RDS
- S3
- QuickSight
- Amazon MSK
- Lambda

### ネットワーク機器
- YAMAHAルータ (RTX1200、RTX810、NVR500)
- NECルータ(UNIVERGE IX2025)
- Ciscoスイッチ(Catalyst 2960-L)
- Buffaloアクセスポイント(WAPS-APG600H、WAPS-AG300H)
- Buffaloスイッチ(BS-POE-G2124M、BS-GS2048)
- Ruckus Wirelss アクセスポイント(ZoneFlex 7343)
- Ruckus Wirelss コントローラー(ZoneDirector 1100)　　　
- アライドスイッチ（CentreCOM GS924M V2）
- アライドスイッチ(CentreCOM GS924M V2)
- CTIシステム(IF6000)

### サーバ
- WindowsSever 2008、2008 R2、2012、2012 R2
- CentOS 5、6、7系
- AamazonLinux,AamaoznLinux2

### データベース
- Microsoft SQL Server
- MySQL
- Oracle

### Webサーバ
- Apache
- IIS
- Nginx

### メール
- Postfix

### ストレージ
- EMC isilon

### ハイパーバイザー
- VMware
- KVM

### クラウド
- AWS
- Nifty Cloud
- Cloud Stack
- Microsoft Azure

### 監視ツール
- CloudWatch
- DataDog
- Nagios
- Zabbix

### スクリプト
- Bash
- Python

## 資格について
- 2018/08 取得後有効期限により失効 Cisco Certified Network Associate (640-801J)
- 2019/06 取得後有効期限により失効 AWS Certified Cloud Practitioner
- 2020/02 取得後有効期限により失効 AWS Certified Solutions Architect - Associate
