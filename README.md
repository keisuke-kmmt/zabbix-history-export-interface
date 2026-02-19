# zabbix-history-export-interface

ZabbixのAPIを使用してヒストリーデータをエクスポートするシングルページWebインターフェース

[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-blue)](https://keisuke-kmmt.github.io/zabbix-history-export-interface/)

## 概要

このツールは、Zabbix APIを使用してヒストリーデータを取得し、CSVまたはJSON形式でエクスポートできる単一のHTMLファイルです。ブラウザ上で動作し、サーバーインストールは不要です。

## デモ / Webページとして確認

**🌐 [オンラインデモを開く](https://keisuke-kmmt.github.io/zabbix-history-export-interface/)**

上記のリンクから、Webページとして直接アクセスして使用できます。
自分のZabbix環境に接続して、履歴データをエクスポートできます。

## 機能

- 🔐 Zabbix APIを使用した認証
- 🖥️ ホストとアイテムの選択
- 🏢 **ホスト全体エクスポート**（複数ホスト対応）
- 📅 時間範囲の指定
- 📊 履歴データの表示
- 💾 CSV/JSON形式でのエクスポート
- 📱 レスポンシブデザイン（モバイル対応）

## 使い方

### Webページとして使用（推奨）

1. **[オンラインデモ](https://keisuke-kmmt.github.io/zabbix-history-export-interface/)** にアクセス
2. 自分のZabbix環境の接続情報を入力して使用

### ローカルで使用

以下のいずれかの方法で使用できます：

#### 方法1: ファイルを直接開く
1. `index.html` をダウンロード
2. ブラウザで直接開く（ダブルクリック）

#### 方法2: ローカルサーバーで実行
```bash
# Python 3を使用する場合
python3 -m http.server 8000

# Node.jsのhttp-serverを使用する場合
npx http-server

# その後、ブラウザで http://localhost:8000 を開く
```

### 操作方法

#### 個別アイテム選択モード

1. Zabbix接続情報を入力
   - Zabbix URL: `https://your-zabbix-server/api_jsonrpc.php`
   - ユーザー名
   - パスワード
2. 「接続」ボタンをクリック
3. エクスポートモードで「個別アイテム選択」を選択
4. ホストを選択
5. アイテムを選択（複数選択可）
6. 時間範囲を指定
7. 「履歴データ取得」をクリック
8. CSVまたはJSONでエクスポート

#### ホスト全体エクスポートモード（新機能）

1. Zabbix接続情報を入力して接続
2. エクスポートモードで「ホスト全体エクスポート」を選択
3. ホストを選択（Ctrl/Cmdキーで複数選択可）
4. 時間範囲を指定
5. 「ホスト全体の履歴データ取得」をクリック
6. 選択したホストの全アイテムの履歴が自動取得されます
7. CSVまたはJSONでエクスポート

## 要件

- モダンなWebブラウザ（CompressionStream API対応）
  - Chrome 80+
  - Edge 80+
  - Safari 16.4+
  - Firefox 113+
- Zabbix 4.0以降（API access必須）
- インターネット接続（CORSが有効な環境）

### ブラウザ互換性について

このツールはブラウザネイティブのCompressionStream APIを使用してZIPファイルを生成します。
外部ライブラリに依存しないため、完全にスタンドアロンで動作し、オフライン環境でも使用できます。

CompressionStream APIは比較的新しいAPIのため、古いブラウザでは動作しません。
上記の要件を満たすブラウザでご使用ください。

## オフライン環境での使用

このツールは外部依存がないため、オフライン環境でも簡単に使用できます。

### セットアップ方法

1. **ファイルのダウンロード**
   
   `index.html` をダウンロード（GitHubから、またはGitクローン）

2. **オフライン環境への配置**
   
   `index.html` をオフライン環境にコピー

3. **使用方法**
   
   オフライン環境で `index.html` をブラウザで開くだけです。
   外部ライブラリは不要です。

### 動作の仕組み

- すべての機能がブラウザネイティブAPIで実装されています
- ZIP生成にCompressionStream APIを使用
- 外部CDNやライブラリへの依存がありません
- インターネット接続なしで完全に動作します（Zabbix APIへの接続は必要）

## トラブルシューティング

### 「CompressionStream APIをサポートしていません」エラー

このエラーが表示される場合、ブラウザが古い可能性があります：

- Chrome/Edge: バージョン80以上に更新してください
- Safari: バージョン16.4以上に更新してください  
- Firefox: バージョン113以上に更新してください

### 「Incorrect user name or password」エラー

このエラーが表示される場合、以下を確認してください：

1. **認証情報の確認**
   - ユーザー名とパスワードが正しいか確認
   - Zabbix Webインターフェースで同じ認証情報でログインできるか試す

2. **Zabbix環境の確認**
   - アカウントがロックされていないか確認
   - ユーザーにAPI accessの権限があるか確認

3. **Zabbixバージョンの確認**
   - Zabbix 5.4以降を使用している場合、このツールは対応しています
   - Zabbix 5.2以前を使用している場合、パラメータの互換性問題がある可能性があります

### 接続エラー

- **URLの確認**: `https://your-zabbix-server/api_jsonrpc.php` の形式になっているか
- **CORSの設定**: Zabbixサーバーでクロスオリジンリクエストが許可されているか
- **ネットワーク**: Zabbixサーバーにアクセスできるネットワーク環境か

### アカウントがブロックされている

- しばらく待ってから再試行
- Zabbix管理者に連絡してアカウントのロックを解除してもらう

## セキュリティ

- このツールはクライアントサイドで動作し、認証情報は保存されません
- HTTPSを使用することを強く推奨します
- 本番環境で使用する場合は、適切なアクセス制御を設定してください

## GitHub Pages設定方法

リポジトリをフォークした場合、以下の手順でGitHub Pagesを有効化してください：

1. GitHubリポジトリの **Settings** タブを開く
2. 左メニューから **Pages** を選択
3. **Source** セクションで以下を設定：
   - Source: **GitHub Actions** を選択
4. 変更をコミット・プッシュすると自動的にデプロイされます

デプロイ後、`https://<username>.github.io/<repository-name>/` でアクセス可能になります。

## ライセンス

MIT License - 詳細は [LICENSE](LICENSE) を参照してください
