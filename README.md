## Docker commands メモ

## Dockerfileのドキュメント
[https://docs.docker.jp/index.html](https://docs.docker.jp/index.html)

#### Docker compose 
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

#### Docker

- コンテナのシェルに接続するコマンド
```bash
docker exec -it <コンテナID or コンテナ名> /bin/bash
```

- コンテナのログを確認
```bash
docker logs -f <コンテナID or コンテナ名> 
```

- Dockerのコンテナ・イメージを全削除するコマンド
    - 停止中コンテナ・未使用イメージ・未使用ネットワーク・キャッシュをまとめて削除
```bash
docker system prune -a
```
