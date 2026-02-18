# zabbix-history-export-interface

ZabbixのAPIを使用してヒストリーデータをエクスポートするシングルページWebインターフェース

## 概要

このツールは、Zabbix APIを使用してヒストリーデータを取得し、CSVまたはJSON形式でエクスポートできる単一のHTMLファイルです。ブラウザ上で動作し、サーバーインストールは不要です。

## 機能

- 🔐 Zabbix APIを使用した認証
- 🖥️ ホストとアイテムの選択
- 📅 時間範囲の指定
- 📊 履歴データの表示
- 💾 CSV/JSON形式でのエクスポート
- 📱 レスポンシブデザイン（モバイル対応）

## 使い方

1. **index.html** をブラウザで開く
2. Zabbix接続情報を入力
   - Zabbix URL: `https://your-zabbix-server/api_jsonrpc.php`
   - ユーザー名
   - パスワード
3. 「接続」ボタンをクリック
4. ホストを選択
5. アイテムを選択（複数選択可）
6. 時間範囲を指定
7. 「履歴データ取得」をクリック
8. CSVまたはJSONでエクスポート

## 要件

- モダンなWebブラウザ（Chrome, Firefox, Safari, Edge等）
- Zabbix 4.0以降（API access必須）
- インターネット接続（CORSが有効な環境）

## セキュリティ

- このツールはクライアントサイドで動作し、認証情報は保存されません
- HTTPSを使用することを強く推奨します
- 本番環境で使用する場合は、適切なアクセス制御を設定してください

## ライセンス

MIT License - 詳細は [LICENSE](LICENSE) を参照してください
