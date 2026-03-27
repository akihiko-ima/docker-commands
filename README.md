## Docker commands メモ

- イメージのビルド

```bash
docker compose build --no-cache
```

- サービスの開始（backgroundで）

```bash
docker compose up -d
```

- サービスの終了

```bash
docker compose down
```

- コンテナ・イメージ・ボリュームの削除

```bash
docker compose down -v --rmi all --remove-orphans
```