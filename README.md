# Dockerized PostgreSQL

このプロジェクトは、Dockerを使用してPostgreSQLデータベースを簡単に起動するためのテンプレートを提供します。

## 前提条件

*   Docker
*   Docker Compose

## セットアップ

1.  `.env`ファイルを編集して、PostgreSQLのユーザー名、パスワード、データベース名をカスタマイズします。
2.  `.env.template`をコピーして.envに名称を変更したものを使用してください

    ```
    POSTGRES_USER=user #DBに接続するためのユーザー名
    POSTGRES_PASSWORD=password #DBに接続するためのパスワード
    POSTGRES_DB=mydatabase #DBの名前
    ```

## 使用方法

### PostgreSQLの起動

プロジェクトのルートディレクトリで、以下のコマンドを実行します。

```bash
docker-compose up -d
```

これにより、PostgreSQLコンテナがバックグラウンドで起動します。

### データベースへの接続

PostgreSQLデータベースには、以下の情報を使用して接続できます。

*   **ホスト**: `localhost`
*   **ポート**: `5432`
*   **ユーザー**: `.env`ファイルで設定した`POSTGRES_USER`の値 (デフォルト: `user`)
*   **パスワード**: `.env`ファイルで設定した`POSTGRES_PASSWORD`の値 (デフォルト: `password`)
*   **データベース**: `.env`ファイルで設定した`POSTGRES_DB`の値 (デフォルト: `mydatabase`)

### PostgreSQLの停止

PostgreSQLコンテナを停止するには、以下のコマンドを実行します。

```bash
docker-compose down
```

これにより、コンテナが停止し、関連するネットワークとボリュームが削除されます。ただし、`db_data`ボリュームは永続化されているため、データは保持されます。
