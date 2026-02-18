# JSZip ライブラリ

このディレクトリには、オフライン環境で使用するためのJSZipライブラリを配置します。

## セットアップ方法

オフライン環境で使用する場合は、以下の手順でJSZipライブラリをダウンロードして配置してください：

1. 以下のURLからJSZip 3.10.1のminifiedファイルをダウンロード:
   ```
   https://unpkg.com/jszip@3.10.1/dist/jszip.min.js
   ```

2. ダウンロードしたファイルを `jszip.min.js` という名前でこのディレクトリに配置

3. ファイル配置後、index.htmlはCDNに接続できない場合に自動的にこのローカルファイルを使用します

## コマンドラインでのダウンロード例

```bash
# wgetを使用する場合
wget https://unpkg.com/jszip@3.10.1/dist/jszip.min.js -O lib/jszip.min.js

# curlを使用する場合
curl https://unpkg.com/jszip@3.10.1/dist/jszip.min.js -o lib/jszip.min.js
```

## 注意事項

- CDNに接続できる環境では、このローカルファイルは使用されません
- ローカルファイルがない場合でもCDNから読み込みを試みます
- 両方とも利用できない場合は、エラーメッセージが表示されます
