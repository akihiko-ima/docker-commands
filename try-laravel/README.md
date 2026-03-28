- DockerコンテナでLaravelプロジェクトを新規作成
```bash
docker compose run php composer create-project --prefer-dist laravel/laravel .
```

```bash
docker compose up -d
```

#### パーミッションエラーの時
```bash
docker compose run php chmod -R 0777 /var/www/html/bootstrap
docker compose run php chmod -R 0777 /var/www/html/storage
```
