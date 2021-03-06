# mdl_webpay

[EC-CUBE](http://www.ec-cube.net)用のWebPayの決済モジュールです。

## 機能

- [WebPay](https://webpay.jp)にメールアドレスとパスワードを登録するだけですぐ試せます
- [トークン機能](https://webpay.jp/docs/payments_with_token)を用いることで EC-CUBE のサーバでカード情報を一切扱いません
- EC-CUBE の登録ユーザと WebPay の顧客を紐付けることにより、ログインしていれば次回以降はカード情報を入力せず利用できます
- EC-CUBE 内の注文、ユーザデータと WebPay の課金、顧客データを ID で対応づけて管理できます
- カード情報は WebPay のサーバで安全に管理されます。 EC-CUBE のサーバで厳しいカード情報の保存要件を満たす必要はありません

## 注意事項

- トークン決済に JavaScript が必要なため、携帯電話端末では利用できません
- PHP 5.3 以上でのみ動作します。PHP 5.2 はすでにサポートが終了しており、安全でないためサポートしません
- EC-CUBE 2.13 以上での動作を保証します

## インストール方法

- このリポジトリの内容をダウンロードし、 EC-CUBE 本体の `data/downloads/module/mdl_webpay` に配置してください。

```
cd EC-CUBE/data/downlaods/module
git clone https://github.com/webpay/mdl_webpay.git
```

- `mdl_webpay` ディレクトリ内で `composer install` を実行します。
  Composer のインストール方法は[Composer](https://getcomposer.org/doc/00-intro.md)を参考にしてください。

```
cd mdl_webpay
composer.phar install
```

- install_webpay.php を実行してデータベースに決済モジュールを登録します。

```
php install_webpay.php
```

- 実行して出力された URL をブラウザで開き、非公開鍵と公開可能鍵を設定します。
  最初はかならずテスト用の鍵をつかって動作を確認してください。

- 「基本情報管理＞支払方法設定」に「クレジットカード決済」ができていることを確認し、設定してください。

- 「基本情報管理＞配送方法設定」から「クレジットカード決済」が利用できるようにしてください。

## 利用方法

- 試しになにかの商品を購入し、支払方法に「クレジットカード決済」を指定すると、カード情報を入力する画面に遷移します。

- クレジットカード情報を入力し、購入できることを確認してください。

- WebPay のダッシュボードで、正しく課金が作成されたことを確認してください。
