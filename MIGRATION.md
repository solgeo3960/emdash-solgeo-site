# WordPress → EmDash 移行メモ

## ページの管理場所

| URL | 管理場所 |
| --- | --- |
| `/service/ch-hp/` ほかサービス系・中国情報系 16ページ | EmDash 管理画面「固定ページ」(見出し・本文・セクションを編集可) |
| `/`、`/service/`、`/japan-web/`、`/aboutus/`、`/contact/`、`/privacy-policy/` | `src/html/pages/*.html`(コードで管理) |
| グローバルメニュー | EmDash 管理画面「メニュー」(primary) |
| リダイレクト | EmDash 管理画面「リダイレクト」 |

URL は WordPress 時代のパーマリンクをそのまま維持しています。

## 初回セットアップ

1. `pnpm install` → `pnpm dev` → `http://localhost:4321/_emdash/admin` のセットアップで **「サンプルコンテンツを含める」にチェック**(これで 16 ページ・メニュー・リダイレクトが入ります)。
2. 管理画面の Forms で、スラッグ `contact` のフォームを作成し、項目を次の名前で追加してください。
   - `name`(テキスト・必須) / `email`(メール・必須) / `message`(テキストエリア・必須)
   - 通知先: `info@solgeo.co.jp`
3. 本番でメール通知を送るには、メール送信プラグイン(`email:deliver` を提供するもの)の設定が必要です。未設定でも送信内容は管理画面の Submissions に保存されます。

## 既知の点(WordPress 時代から引き継いだもの)

- メニューの「About China」(`/about-china/`)はページが存在せず 404 です。
- `page-jp-web.php` 相当のページは下書き(非公開)として登録しています。
- Stories(カスタム投稿タイプ)はトップページでコメントアウトされていたため移行していません。
