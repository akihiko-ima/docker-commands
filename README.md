# Docker commands メモ

## Dockerfileのドキュメント

[https://docs.docker.jp/index.html](https://docs.docker.jp/index.html)

### Docker compose

- イメージのビルド

Compose ファイルに定義したサービスのイメージをビルドします。

```bash
docker compose build --no-cache
```

`--no-cache` はビルドキャッシュを使わずに各手順を実行します。依存パッケージなどを含めて、イメージを最初から作り直したい場合に使います。

```bash
docker compose build --no-cache --pull
```

`--pull` はベースイメージの新しい版を取得してからビルドします。`--no-cache` と併用すると、キャッシュを使わず最新のベースイメージを使ったビルドを試みます。

- Compose ファイルの設定を検証し、展開後の設定を表示

```bash
docker compose config
```

- サービスの開始（backgroundで）

```bash
docker compose up -d
```

Compose ファイルのサービスに必要なコンテナを作成して起動します。`-d` は detached の略で、コンテナをバックグラウンドで実行し、コマンドを終了します。

- サービスの終了

```bash
docker compose down
```

Compose で作成したコンテナとネットワークを停止・削除します。通常、名前付きボリュームやイメージは削除されません。

- コンテナ・イメージ・ボリュームの削除

```bash
docker compose down -v --rmi all --remove-orphans
```

`-v` は Compose が管理する名前付きボリュームとコンテナに付属する匿名ボリュームを削除します。`--rmi all` はサービスが使用するイメージをすべて削除し、`--remove-orphans` は現在の Compose ファイルに定義されていない孤立コンテナも削除します。データやイメージも失われるため、実行前に必要なものがないか確認してください。

### Docker

- コンテナのシェルに接続するコマンド

```bash
docker exec -it <コンテナID or コンテナ名> /bin/bash
```

起動中のコンテナ内で指定したコマンドを実行します。この例では Bash シェルを開きます。`-i` は標準入力を開いたままにし、`-t` は対話操作用の端末を割り当てます。`<コンテナID or コンテナ名>` は対象のコンテナに置き換えてください。

- コンテナのログを確認

```bash
docker logs -f <コンテナID or コンテナ名>
```

コンテナが出力したログを表示します。`-f` は follow の略で、新しいログが出力されるたびに表示を続けます。終了するには `Ctrl+C` を押します。

- Dockerのコンテナ・イメージを全削除するコマンド
  - 停止中コンテナ・未使用イメージ・未使用ネットワーク・キャッシュをまとめて削除

```bash
docker system prune -a
```

`docker system prune` は使用されていない Docker リソースを削除し、`-a` は未使用イメージのうちタグの付いたものも対象にします。ボリュームはこのコマンドだけでは削除されません。削除対象を確認してから実行してください。
