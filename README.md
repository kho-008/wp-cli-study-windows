# WindowsでWordPress環境構築（XAMPP）

## 参考

## ダウンロード&解凍
```bash
wget https://ja.wordpress.org/wordpress-6.1.1-ja.zip
# curl -OL https://ja.wordpress.org/wordpress-6.1.1-ja.zip
unzip wordpress-6.1.1-ja.zip
mv wordpress/ test/
```

## インストール
1. phpMyAdminでデータベース作成
    ```
    wptestdb
    utf8_general_ci
    ```
1. WordPress
http://localhost/test/
    ```
    wptestdb
    root
    パスワードなし
    ```

- [【2022年Windowsユーザー向け】XAMPPを使ってWordPresssをインストールする方法を解説 | CodeCampus](https://blog.codecamp.jp/how-to-install-wordpresss-using-xampp)
- [XAMPPを使ってローカルでWordPressを動かそう②【XAMPPでWPを動かす手順編】 | Tanweb.net](https://tanweb.net/2018/12/12/24470/)

## WP-CLI
- [Command line interface for WordPress | WP-CLI](https://wp-cli.org/ja/)
- [WordPressでWP-CLIを使って記事移行とかを少し楽にする | 株式会社LIG(リグ)｜DX支援・システム開発・Web制作](https://liginc.co.jp/569775)
- [【WP-CLI】WordPress開発を自動化しよう | eclairのブログ](https://eclair.blog/wp-cli/)
- [WordPress『 WP-CLI 』#2 インストール方法と使い方｜レンタルサーバーナレッジ](https://knowledge.cpi.ad.jp/cms/wordpresswp-cli2/)
- [WindowsでWP CLIを導入する手順 | 経験知](https://keikenchi.com/steps-to-deploy-wp-cli-on-windows)
- [WP-CLI v2：WordPressのターミナルからの管理](https://kinsta.com/jp/blog/wp-cli/)

## インストール
```PowerShell
cd C:\xampp\htdocs
curl.exe -OL https://ja.wordpress.org/wordpress-6.1.1-ja.zip
Expand-Archive -Path wordpress-6.1.1-ja.zip -DestinationPath .\
Rename-Item .\wordpress test
cd test
curl.exe -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
# ↓動作確認
C:\xampp\php\php wp-cli.phar --info
```

```bash
cd /mnt/c/xampp/htdocs && wget https://ja.wordpress.org/wordpress-6.1.1-ja.zip && unzip wordpress-6.1.1-ja.zip && mv wordpress/ test/ && cd test && curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && /mnt/c/xampp/php/php.exe wp-cli.phar --info
```

## コマンド一覧
- [WP-CLI Commands | WordPress Developer Resources](https://developer.wordpress.org/cli/commands/)

## WP-CLIでWordPressのインストール
エラーの対応がわからなかった

```PowerShell
mkdir C:\xampp\htdocs\test
cd C:\xampp\htdocs\test
curl.exe -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
C:\xampp\php\php wp-cli.phar core download --version=6.0.3 --locale=ja --quiet
C:\xampp\php\php wp-cli.phar config create --dbname=wptestdb --dbuser=root --dbhost=localhost --dbprefix=wp_
C:\xampp\php\php wp-cli.phar db create
C:\xampp\php\php wp-cli.phar core install --url=http://localhost/test --title="さいとたいとる" --admin_user=user --admin_password=passwd --admin_email=shigeo_wake@kitahamagm.co.jp
```
- [WP-CLI v2：WordPressのターミナルからの管理](https://kinsta.com/jp/blog/wp-cli/#wordpress)
- [WP-CLI で WordPress を日本語パッケージと同じ構成にする - Qiita](https://qiita.com/miya0001/items/96a684e2f819f9d8b4a4)
- [PowerShell で wget のようにファイルダウンロードをしたい - tech.guitarrapc.cóm](https://guitarrapc-tech.hatenablog.com/entry/2013/07/09/220710)
- [Windows Powershellでcurlを使うときの注意点](https://zenn.dev/yu1low/articles/f559f35c7087ef)

## WP-CLIをcomposerでインストール
エラーの対応がわからなかった
```
Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

- [WordPressでWP-CLIを使って記事移行とかを少し楽にする | 株式会社LIG(リグ)｜DX支援・システム開発・Web制作](https://liginc.co.jp/569775)
- [XAMPP と Laravel Valet と WP-CLI で WordPress 開発環境を Windows に構築する | フレアーズ合同会社 | 三重県四日市市のウェブアプリ・サイト制作会社](https://flares.jp/report/453/)
- [Windows 環境に WP-CLI をインストール | Web Design Leaves](https://www.webdesignleaves.com/wp/wordpress/1421/)
- [よく使うcomposerコマンドとバージョン指定方法の備忘録 | tanden techblog](https://tanden.dev/%E3%82%88%E3%81%8F%E4%BD%BF%E3%81%86composer%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A8%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E6%8C%87%E5%AE%9A%E3%81%AE%E5%82%99%E5%BF%98%E9%8C%B2/)
- [【Laravel】Composer requireでエラー(Installation failed, reverting ./composer.json to its original content.)が出るけどrequireしたい！ - Qiita](https://qiita.com/anoonoll/items/5fab1e6682861a406570)
