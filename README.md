# Django S3 Setup

## 環境準備

### IAMユーザーの作成

1. IAMユーザーを作成する
2. アクセスキーIDとシークレットキーを控えておく

### S3のバケット作成

1. AWS S3のバケットを作成
2. `バケット名` を入力し、控えておく
3. `オブジェクト所有者` の `ACL 有効` を選択する
4. `このバケットのブロックパブリックアクセス設定` の `パブリックアクセスをすべて ブロック` のチェックを外す
5. それ以外はデフォルトのままバケットを作成する

### 環境変数に設定

1. `.env.example` をコピーして `.env` を作成する
2. 以下の通り、環境変数をセットする

```
AWS_ACCESS_KEY_ID=[IAMユーザーのアクセスキーID]
AWS_SECRET_ACCESS_KEY=[IAMユーザーのシークレットキー]
AWS_STORAGE_BUCKET_NAME=[S3のバケット名]
```

### 開発環境で確認

1. `python manage.py collectstatic` で静的ファイルをS3にアップロードする
2. `python manage.py makemigrations && python manage.py migrate` でDBマイグレーションを実施する
3. `python manage.py runserver` で開発サーバーを起動し、`http://localhost:8000/admin` にアクセスする
4. 管理サイトのCSSが適用されていれば、S3へ正常にアップロードされている
5. `Blog posts` のデータを作成し、画像をアップロードする
6. `http://localhost:8000` にアクセスする
7. 画像が表示されていれば、S3への画像アップロードも正常に動作している
