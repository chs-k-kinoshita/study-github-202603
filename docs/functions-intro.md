# 各種機能の紹介 Index
- [PublicリポジトリとPrivateリポジトリ、Fork](#PublicリポジトリとPrivateリポジトリ、Fork)
- [Issue、Pull Request](#Issue、PullRequest)
- [GitHub Actions](#GitHub-Actions) ※CI/CD等の自動化の肝となる、かなり重要な機能
- [AdvancedSecurity](#AdvancedSecurity)
- [Codespaces](#Codespaces)
- [Gist](#Gist)
- [GitHub Pages](#GitHub-Pages)
- [Wiki](#Wiki)
- [Appendix:特定の役割を持つマークダウンファイル](#特定の役割を持つマークダウンファイル)

※ ここで紹介しきれていない機能もいろいろあると思います（Projectとか）

# PublicリポジトリとPrivateリポジトリ、Fork
- 作成時に指定、Settingの「Change repository visibility」設定で後からも変更可能
- Publicの場合、全世界に公開される
  - ※仮に管理権限を持ったAWS IAMユーザーのアクセスキー＆シークレットキーが書かれたコードをPublicリポジトリにアップしてしまうと恐ろしいことに
- Private（非公開）の場合、自身(Owner)と招待されたコラボレーター(Collaborators)、および組織の権限設定で許可されたユーザーのみが参照可能（権限がない人がリポジトリのURLを開いても404 NotFound）
- ひと昔と違い、今はFreeプランでもPrivateリポジトリを無制限に作成可能
- Fork機能: 他のOSSプロジェクト等のリポジトリからForkして自身のアカウント上にコピー可能
  - 元プロジェクトのCollaboratorでなくても、自分のアカウント上での作業内容からプルリクを通じて変更を提案できる

# Issue、PullRequest
- Issue: タスク管理のための機能(Redmineなどの機能で例えると"チケット"に相当)。
  - ラベル: 分類・優先度付け
  - マイルストーン: バージョンごとに管理
- Pull Request: 通称「プルリク」。変更をレビューしてもらい、マージ（統合）により取り込んでもらうための機能。
  - Reviewerを指定可能
    - GitHub Copilotの有料プランをサブスクしている場合はAI(Copilot)にレビューをさせることもできる
  - ※自分でレビューするためのセルフプルリクも私は普通にする
- テンプレート化して作成時の入力を簡略化できる
  - [参考:リポジトリ用に Issue テンプレートを設定する](https://docs.github.com/ja/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
  - [参考:リポジトリ用のプルリクエストテンプレートの作成](https://docs.github.com/ja/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
- 未経験の人は下記URLの公式トレーニング(演習)をやってみることでイメージわくと思います
  - [演習 - GitHub のガイド ツアー](https://learn.microsoft.com/ja-jp/training/modules/introduction-to-github/6-guided-tour-of-github?ns-enrollment-type=learningpath&ns-enrollment-id=learn.github-foundations)
  - [演習 - pull request のレビュー](https://learn.microsoft.com/ja-jp/training/modules/manage-changes-pull-requests-github/3-review-pull-requests)

# GitHub Actions
- CI/CD（継続的インテグレーション/継続的デリバリー）プラットフォームです。
  - pushやプルリクからのマージをトリガーにビルド・自動テスト・デプロイを自動化など
  - DependabotやAIエージェント(Copilot)が裏でタスクを実行する際の実行環境としても使われる
- AWSのサービスでいうとCode Pipeline＋Code Build＋Code Deployのイメージ。
- yamlファイルでワークフローを定義。
- (例として、ReactアプリをAzure Static WebAppにGitHub Actionsでビルド＆デプロイを実演 ※時間があれば）

# AdvancedSecurity
- （リポジトリの）Settings＞Security＞Advanced Security
- Dependabot:
  - graph: ライブラリ依存関係の可視化
    - 表示は Insightsタブ＞Dependency graph
  - alerts: 依存ライブラリの脆弱性を自動検出・通知する機能
    - リポジトリの依存パッケージに既知の脆弱性がないかスキャン
    - [GitHub Advisory Database](https://github.com/advisories)と照合して問題を検出
  - security updates
    - アラートを受けて、改善の提案（プルリクの作成）まで自動化
  - version updates
    - セキュリティ以外の定期的な依存関係更新も自動化
- CodeScan:
  - 脆弱性を含んだコードを自動でチェック
  - publicリポジトリ、あるいは組織向け有料プランのみ利用可能
- SecurityScan
  - 機密情報(アクセスキー、APIキーなど)がコードに含まれていないか自動でチェック
  - publicリポジトリ、あるいは組織向け有料プランのみ利用可能
- 下記の公式トレーニング(演習)をやってみることでイメージわきやすい
  - [演習 - リポジトリのサプライ チェーンをセキュリティで保護する](https://learn.microsoft.com/ja-jp/training/modules/maintain-secure-repository-github/3-security-strategy-essentials?ns-enrollment-type=learningpath&ns-enrollment-id=learn.github-foundations-2)
  - [コード スキャンの構成の演習](https://learn.microsoft.com/ja-jp/training/modules/configure-code-scanning/5-exercise)

# Codespaces
- ブラウザ上で利用できるVSCodeのイメージ（裏ではDevContainersのDockerコンテナ上で稼働）
  - [Codespaces のドキュメント](https://docs.github.com/ja/codespaces)
  - [DevContainers](https://containers.dev/)
- 制限（コア時間）内で利用可能。有料プランで制限拡張。
- 構成はデフォルトで起動される「素」の状態からカスタマイズ可能
  - ".devcontainer/devcontainer.json"

# Gist
- コードやテキストを手軽に共有・保存するためのサービス
  - リポジトリには紐づかない（アカウントに紐づく）
    - 機能のURL: https://gist.github.com/アカウント名
  - リポジトリと同様にバージョン履歴管理やclone/pull/pushなどの操作が可能
  - Webページやブログにコードを埋め込み可能
- 主な用途:
  - コードのサンプル共有
  - メモやドキュメントの一時共有
- Public GistとSecret Gist
  - Public Gist：誰でも閲覧可能（検索にも表示）
  - Secret Gist：URLを知っていれば閲覧可能
    - 検索されないだけでURLを知っていれば誰でもアクセス可能なことに注意 ※Privateリポジトリとの混同注意

# GitHub Pages
- 静的Webページをホスティングできるサービス
  - [参考: GitHub Pages とは](https://docs.github.com/ja/pages/getting-started-with-github-pages/what-is-github-pages)
  - 利用例: API仕様のオンラインドキュメント公開等
- PagesはGitHubアカウント単位の１つと、リポジトリ単位で１つ作成可能
- 公開URL構成
  - アカウント単位: ```https://アカウント名.github.io``` ※ "アカウント名.github.io"の名前でリポジトリを作る
  - リポジトリ単位: ```https://アカウント名.github.io/リポジトリ名```
- 例:
  - [このリポジトリのGitHub Pages](https://chs-k-kinoshita.github.io/study-github-202603)
  - [GenUのGitHub Pages](https://aws-samples.github.io/generative-ai-use-cases/)
- 個人向けFreeプランではpublicリポジトリでのみ利用可能

# Wiki
- markdownでソースコードとは別管理でドキュメントを記載可能。詳細省略。
- 個人向けFreeプランではpublicリポジトリでのみ利用可能

# 特定の役割を持つマークダウンファイル

- 下記いづれかのディレクトリパスに配置するきまり（読み込みの優先順もこの通り ※上から優先）。
  - ".github"ディレクトリ
  - ルートディレクトリ
  - "docs"ディレクトリ
- "About"欄に表示される

## README.md
- プロジェクトの概要、使用方法、インストール手順
## CODE_OF_CONDUCT.md
- コミュニティの行動規範
## CONTRIBUTING.md
- コントリビューションガイドライン、プルリクエストの作成方法
## LICENSE.md（または LICENSE ※拡張子なし）
- ソフトウェアの使用、変更、配布に関する法的条件を明示
- 知的財産権の保護と利用条件の明確化
## SECURITY.md
- プロジェクトのセキュリティ脆弱性の報告方法を明示
- セキュリティ関連の方針や手順を文書化