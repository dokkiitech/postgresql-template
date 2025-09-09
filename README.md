# PostgreSQL & pgAdmin Docker Template

このプロジェクトは、Dockerを使用してPostgreSQLデータベースと管理ツールであるpgAdminを簡単に起動するためのテンプレートです。

## 前提条件

*   Docker
*   Docker Compose

## 🚀 使い方

### 1. 環境変数の設定

まず、プロジェクトのルートにある`.env.template`ファイルをコピーして、`.env`という名前のファイルを作成します。このファイルにデータベースの接続情報などを記述します。

```bash
cp .env.template .env
```

作成した`.env`ファイルを開き、必要に応じて内容を編集してください。

```
# PostgreSQL接続情報
POSTGRES_USER=user
POSTGRES_PASSWORD=password
POSTGRES_DB=mydatabase

# pgAdmin接続情報
PGADMIN_DEFAULT_EMAIL=admin@example.com
PGADMIN_DEFAULT_PASSWORD=admin
```

### 2. コンテナの起動

プロジェクトのルートディレクトリで、以下のコマンドを実行します。

```bash
docker-compose up -d
```

これにより、PostgreSQLとpgAdminのコンテナがバックグラウンドで起動します。

### 3. コンテナの停止

コンテナを停止するには、以下のコマンドを実行します。

```bash
docker-compose down
```

データを完全に削除したい場合は、`-v`オプションを付けて実行してください。

```bash
docker-compose down -v
```

## 接続情報

### PostgreSQL

- **ホスト**: `localhost`
- **ポート**: `5432`
- **ユーザー**: `.env`ファイルで設定した`POSTGRES_USER`
- **パスワード**: `.env`ファイルで設定した`POSTGRES_PASSWORD`
- **データベース**: `.env`ファイルで設定した`POSTGRES_DB`

### pgAdmin

1.  **Webアクセスとログイン**
    - **URL**: [http://localhost:5050](http://localhost:5050)
    - **ログインEmail**: `.env`ファイルで設定した`PGADMIN_DEFAULT_EMAIL` (デフォルト: `admin@example.com`)
    - **ログインPassword**: `.env`ファイルで設定した`PGADMIN_DEFAULT_PASSWORD` (デフォルト: `admin`)

2.  **データベースサーバーの登録**
    pgAdminに初回ログイン後、手動でPostgreSQLサーバーを登録する必要があります。
    - ダッシュボードで「Add New Server」をクリックします。
    - **General** タブで、サーバーの任意の名前を入力します (例: `local-postgres`)。
    - **Connection** タブに切り替え、以下の情報を入力します。
      - **Host name/address**: `host.docker.internal`
      - **Port**: `5432`
      - **Maintenance database**: `.env`の`POSTGRES_DB`の値 (デフォルト: `mydatabase`)
      - **Username**: `.env`の`POSTGRES_USER`の値 (デフォルト: `user`)
      - **Password**: `.env`の`POSTGRES_PASSWORD`の値 (デフォルト: `password`)
    - 「Save」をクリックして接続を保存します。