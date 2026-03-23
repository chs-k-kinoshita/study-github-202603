# 料金プランに関するまとめ

- GitHubとGitHub Copilotでそれぞれの料金プラン（個人向け、組織向け）がある
  - GitHub、GitHub Copilotでそれぞれ無料プランあり
  - GitHubの有料プランを契約してもGitHub Coplitの有料機能を使えるわけではない
  - GitHubはFreeのままでGitHub Coplilotだけ有料プランを使う、ということも可能（当然逆もあり）
- 特にPublicリポジトリ利用ではFreeプラン(GitHub)でも多くの機能が解放されている
  - Privateリポジトリ利用の場合は制限が多くなる（特にFreeプラン）

# Freeプランで出来ることまとめ(2026-03)

- 無制限
  - リポジトリの作成(privateリポジトリ含む)
  - Collaboratorの招待
  - Issue管理、プルリクエストなどの基本機能
  - Dependabot（AdvancedSecurityの機能）
  - Gist（リポジトリと紐づかない機能）
- Publicリポジトリのみで無制限
  - GitHub Actions ★重要
  - Code Scan、Secret Protection（AdvancedSecurityの機能） ★重要
  - GitHub Packages
  - Pages, Wiki
- 制限つきでPrivateリポジトリでも利用可能
  - GitHub Actions (月2000分)
  - GitHub Packages（500MBストレージ）
- 制限つきで利用可能（Public, Private関わらず）
  - Codespaces（月120コア時間）
- GitHub CopilotもFreeプランでお試し利用可能
  - ただし、いろいろ制限付き(下記)なので本格的に開発で使うならおそらく足りなくなる
    - 1 か月あたり 50 件のエージェント モードまたはチャットリクエスト
    - 1 か月あたり 2,000 件のコード補完
- Freeプラン利用の限りでは課金（サブスク）設定は不要（GitHub, GitHub Copilot共通）
- アカウントのSettings＞Billing and licensing からプレミアムリクエストやActions消費時間などの状況確認が可能
