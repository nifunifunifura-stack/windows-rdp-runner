GitHub Actionsを使ったWindows 11 RDP環境 🖥️（Tailscale対応）
GitHub Actionsを利用して、Tailscale VPN経由で無料かつ安全なWindows 11リモートデスクトップ（RDP）環境を構築するワークフローです。

開発、テスト、Windowsアプリケーションへのリモートアクセスなどに最適です。スマートフォンを含む、さまざまなデバイスからアクセスできます。
🔄 大幅アップデート（2025年11月）
⚠️ Ngrokを完全に削除
このリポジトリから、Ngrokを使用したトンネリング機能と関連する依存関係を完全に削除しました。
✨ Tailscaleに変更した理由
セキュリティ面のメリット
- 🔒 エンタープライズレベルの暗号化：WireGuardプロトコルによるエンドツーエンド暗号化
- 🏠 プライベートメッシュネットワーク：インターネット上に公開URLを作成しない
- 🛡️ ゼロトラストアーキテクチャ：認証されたデバイスのみ接続可能
- 🎯 細かなアクセス制御：ロールベースの権限管理とACL
コストと利用しやすさ
- 🆓 クレジットカード不要：Tailscaleの無料プランで個人利用が可能
- 💳 Ngrokの制限：継続的なアクセスや高度なセキュリティ機能にはクレジットカードが必要
- ♾️ 個人利用は無制限：恣意的な接続回数制限やタイムアウトなし
使いやすさ
- 📦 簡単なデバイス管理：Tailscaleのダッシュボードですべての接続デバイスを確認可能
- 🔌 自動再接続：接続が切れた場合も自動的に復旧
- 📱 マルチプラットフォーム対応：Windows、Mac、Linux、iOS、Androidで利用可能
参考：YouTubeのチュートリアルから着想を得ています。
✨ 主な機能
- 無料のWindows Server 2022（GitHub Actions Runner）
- メモリ7GB、CPU 2コア
- SSDストレージ14GB
- 高速インターネット接続
- ソフトウェアの事前インストール（VS Code、Git、Node.js、Pythonなど）
- 安全なTailscale VPNによるプライベート接続
- 最大6時間のセッション利用
- カスタムパスワードに対応
- マルチプラットフォーム対応（Windows、Mac、Linux、Android、iOS）
- GitHub OAuth連携による簡単なセットアップ
🚀 クイックセットアップ
1. リポジトリをForkする
ページ右上の Fork ボタンをクリックして、自分のGitHubアカウントにリポジトリをコピーします。
2. Tailscaleアカウントを作成する
1. Tailscale公式サイトにアクセス
2. 「Start connecting devices」をクリック
3. GitHubアカウントでサインアップ（OAuth連携が簡単なので推奨）
4. 個人利用の場合、クレジットカードは不要
3. Tailscale認証キーを生成する
1. Tailscaleのダッシュボードを開く
2. Settings → Keys に移動
3. 「Generate auth key」をクリック
4. デフォルト設定のまま「Generate key」をクリック
5. 生成されたキーをコピーする（tskey-auth-... で始まる文字列）
4. GitHub Secretsに登録する
1. Forkしたリポジトリを開く
2. Settings → Secrets and variables → Actions に移動
3. 「New repository secret」をクリック
4. 以下の内容を入力する。
項目	設定値
Name（名前）	TAILSCALE_AUTH_TOKEN
Value（値）	コピーしたTailscale認証キー

5. 「Add secret」をクリックして保存します。
5. ワークフローを実行する
1. GitHubリポジトリの「Actions」タブを開く
2. 「Windows 11 RDP with Tailscale」ワークフローを選択
3. 「Run workflow」をクリック
4. 必要に応じてカスタムパスワードを設定する（デフォルト：P@ssw0rd123!）
5. もう一度「Run workflow」をクリックして実行する
6. デバイスにTailscaleをインストールする
1. 使用しているOSに対応したTailscaleをダウンロードする。
- Windows / Mac：tailscale.com/download
- Android：Google Playストア
- iOS：App Store
- Linux：パッケージマネージャーまたは公式サイト
2. セットアップ時に、手順2で使用したものと同じアカウントでログインする
3. GitHub ActionsのRunnerがTailscaleネットワークに表示されるまで待つ
7. RDPで接続する
1. GitHub Actionsのワークフローログから接続情報を確認する
2. 任意のRDPクライアントを使用する。
- Windows：リモートデスクトップ接続
- Mac：Microsoft Remote Desktop
- Linux：Remmina、xfreerdp
- Android / iOS：Microsoft Remote Desktopアプリ
3. ログに表示されたTailscaleのIPアドレスを入力する
4. 指定されたユーザー名とパスワードでログインする
📋 接続情報
デフォルトのログイン情報
項目	内容
ユーザー名	runneradmin
パスワード	P@ssw0rd123!（または設定したカスタムパスワード）
IPアドレス	ワークフローログに表示（例：100.x.x.x）

システム仕様
項目	仕様
OS	Windows Server 2022（最新版）
RAM	7GB
CPU	2コア
ストレージ	14GB SSD
ネットワーク	Tailscale VPN経由の高速インターネット
GPU	ソフトウェアレンダリングのみ（専用GPUなし）

📱 スマートフォンでの接続方法
Android端末
1. Google PlayストアからMicrosoft Remote Desktopをインストール
2. Google PlayストアからTailscaleをインストール
3. Tailscaleに自分のアカウントでログイン
4. Remote Desktopアプリで新しい接続を追加
5. ワークフローログに表示されたTailscaleのIPアドレスを入力
6. 以下の認証情報を入力する。
- ユーザー名：runneradmin
- パスワード：設定したパスワード
iOS端末（iPhone / iPad）
1. App StoreからMicrosoft Remote DesktopとTailscaleをインストール
2. Tailscaleにログイン
3. RDPアプリで新しいデスクトップ接続を追加
4. TailscaleのIPアドレスとログイン情報を入力
🛠️ 事前インストール済みソフトウェア
RDP環境には、以下のソフトウェアがあらかじめインストールされています。
- Google Chrome、Microsoft Edge
- Visual Studio Code
- Git
- Node.js、npm
- Python 3.x
- PowerShell 7
- Windows Terminal
- .NET Framework
- その他多数の開発ツール
🚀 開発予定：デスクトップアプリケーション
現在、以下の機能を備えたPyQt5製デスクトップアプリケーションを開発予定です。
- ⚙️ ワンクリックセットアップ：すべての構築作業を自動化
- 🔑 キー管理：Tailscale認証キーを安全に保存・管理
- 📊 リアルタイム監視：RDPセッションの状態をリアルタイムで確認
- 📁 GitHub連携：OAuthログインとワークフロー管理
- 💻 複数アーキテクチャ対応：x86（32bit）とx64（64bit）のWindowsに対応
- 📦 簡単な配布：GitHub Releasesから実行ファイル（.exe）をダウンロード可能
🔧 トラブルシューティング
よくある問題
「Tailscale authentication failed」（Tailscale認証に失敗する）
- TAILSCALE_AUTH_TOKEN Secretが正しく設定されているか確認する
- 認証キーの有効期限が切れていないか確認する
- Tailscaleアカウントの状態を確認する
「Cannot connect to RDP」（RDPに接続できない）
- 接続元デバイスにTailscaleがインストールされ、ログイン済みであることを確認する
- ワークフローログに表示された正しいTailscale IPを使用しているか確認する
- 両方のデバイスが同じTailscaleネットワークに接続されているか確認する
- 別のRDPクライアントを試す
「Workflow fails to start」（ワークフローが開始できない）
- GitHub Actionsが有効になっているか確認する
- .github/workflows/ にワークフローファイルが存在するか確認する
- リポジトリに必要な権限があるか確認する
📝 重要事項
制限事項
- 最大6時間：セッションは6時間経過すると自動的に終了する
- 永続ストレージなし：セッション終了時にファイルが失われる
- 専用GPUなし：GitHub Actions Runnerには専用グラフィックカードがない
- ネットワーク依存：接続する両方のデバイスでTailscaleが必要
セキュリティ上の推奨事項
- 強力なカスタムパスワードを使用する
- RDP環境に機密情報を保存しない
- Tailscaleネットワーク内に不正なデバイスがないか監視する
- Tailscale ACLを使用してアクセス制御を強化する
- 認証キーを安全に保管し、定期的に更新する
利用上の注意
- 開発およびテスト目的で使用すること
- GitHubの利用規約と公平な利用ポリシーを遵守すること
- マイニング、違法行為、本番環境での利用は禁止
- アカウント制限を避けるため、リソース使用量に注意すること
🎆 以前のNgrok版との比較
比較項目	Tailscale（現在）	Ngrok（旧方式）
セキュリティ	プライベートVPN、WireGuard暗号化	公開トンネル、基本認証
コスト	個人利用は無料	一部機能でクレジットカードが必要
セットアップ	OAuth＋認証キー	手動でトークンを管理
モバイル対応	専用アプリあり	Webベースのみ
安定性	自動再接続	手動でトンネルを管理
プライバシー	外部公開なし	公開エンドポイントが必要

🤝 コントリビューション（開発への参加）
誰でも開発への貢献を歓迎します。
- バグやセキュリティ上の問題を報告する
- モバイル対応の改善を提案する
- 新機能のPull Requestを送信する
- 利用例やフィードバックを共有する
- 今後公開予定のデスクトップアプリケーションの開発を支援する
📄 ライセンス
このプロジェクトはMITライセンスのもとで公開されています。

詳細はリポジトリ内の LICENSE ファイルを確認してください。
⚠️ 免責事項
このプロジェクトは教育および開発目的で提供されています。

利用者は以下の規約や法律を遵守する責任があります。
- GitHub利用規約
- Tailscale利用規約
- 各地域の法律や規制
このツールの不適切な使用について、開発者は責任を負いません。
🌟 プロジェクトへの応援
このプロジェクトが役に立った場合は、GitHubで ⭐ Star を付けて応援してください！

Tailscaleで安全なリモートアクセスを実現しましょう！ 🚀🔒
