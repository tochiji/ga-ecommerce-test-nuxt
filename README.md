# ga-ecommerce-test-nuxt

Nuxt を使って Google アナリティクスの拡張 e コマースをテストするためのレポジトリ

## インストール

```bash
# ローカルにインストール
$ git clone "https://github.com/tochiji/ga-ecommerce-test-nuxt.git"
$ cd ga-ecommerce-test-nuxt
```


## .env の設定

「.env」という名前のファイルを作成し、下記内容を入力してください。

```bash
# .envファイル
# テストしたいGAのID（プロパティID）を入力
GAID=UA-XXXXXXXXX-X
```

## ローカルで起動する

```bash
# 依存ファイルを全てインストールする
$ npm install

# localhost:3000でローカルサーバー起動
$ npm run dev

# build for production and launch server
# $ npm run build
# $ npm start

# generate static project
# $ npm run generate
```
For detailed explanation on how things work, checkout [Nuxt.js docs](https://nuxtjs.org).