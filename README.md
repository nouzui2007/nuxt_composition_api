# Composition APIのサンプル

## VSCodeでコンテナに接続する

### 拡張機能

Remote Development

### コンテナを作ってアタッチする手順

1. VSCode左下の `Open a Remote Window` をクリック
1. `Open Folder in Container...` を選択
    1. すでにフォルダを開いている場合は、`Reopen in Container`を選択
1. このフォルダを選択

## アタッチしたらやること

最初にコンテナを作成したらインストールを行う。

```bash
yarn install
```

## 実行する

1. 左側のペインに `NPM SCRIPTS` を開く

1. `dev` にポイントし、実行ボタンをクリックする

1. ブラウザからアクセスする

    ```bash
    http://localhost:3000
    ```

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```
