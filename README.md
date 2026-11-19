# AI残業部 — Web拠点サイト基盤（GitHub Pages + Jekyll）

「AI残業部」の Web 正本サイト一式。**現時点ではソース構築のみで、未公開。** GitHub リポジトリへアップロードすれば GitHub Pages の標準 Jekyll ビルドで公開できる構成にしてある。
方針の正本は `files/AI残業部_SEO-AIO戦略と成長の仕組み.md`（Web＝正本、note＝派生、X＝需要センサー）、ブランド情報の正本は `files/AI残業部_立ち上げキット.md`。

## カスタムドメイン（aizangyobu.com）適用時の手順メモ

ドメインは取得済みだが、今回は適用しない。適用する際は:

1. `_config.yml` の `url` を `"https://aizangyobu.com"` に変更する（`baseurl` は `""` のまま）
2. リポジトリ直下に `CNAME` ファイルを新規作成し、中身を `aizangyobu.com` の1行だけにする（現時点では CNAME ファイルは置いていない）
3. DNS 側で GitHub Pages 向けレコードを設定する
4. Search Console / GA を登録し、XML サイトマップと構造化データ（Organization / Article）の検出を確認する

## 構成

| パス | 内容 |
|---|---|
| `_config.yml` | サイト名「AI残業部」・タグライン「残業は、AIがする。」・シリーズ順・外部チャネル URL（単一の参照元）・GA4 測定 ID（空欄＝タグ出力なし）。カスタムドメイン適用メモをコメントで保持 |
| `_layouts/` | default / page / post（FAQ・同シリーズ関連記事つき）/ series（シリーズ説明＋カテゴリ一致記事の自動一覧。0本でも成立） |
| `_includes/` | head（Organization 構造化データ＋sameAs、記事のみ Article、GA4 は ID 設定時のみ）/ header / footer |
| `index.md` | トップページ（ブランド紹介、シリーズ4分類への導線、各チャネルへの導線、新着記事） |
| `profile.md` | 部長について（ペルソナ紹介＋FAQ 3問） |
| `series/` | シリーズ4分類のカテゴリページ雛形（konya-daiko / anzen-kakunin / asa-owatta / dogubako） |
| `_templates/article-template.md` | 記事テンプレート。結論先行・質問文見出し・定義文・一次情報ブロック・記事末 FAQ 3問以上（front matter）の型を骨格化 |
| `_drafts/` | 下書き置き場（公開ビルドに含まれない） |
| `assets/css/style.css` | 共通スタイル（濃紺＋ティール。他ブランドの意匠は流用していない） |

## SEO / AIO の実装メモ

- 記事の型: Answer First、質問文の見出し、定義文、一次情報ブロック、記事末 FAQ 3問以上、著者（編集部表記）と公開日・更新日の明示
- 構造化データ: Organization（sameAs で note / X / Zenn / YouTube / BOOTH / SUZURI を接続）と Article を必須実装。FAQPage は任意のため付けていない
- llms.txt は作らない（効果の実測否定があり、方針として投資対象にしない）
- 内部リンク: シリーズページと記事レイアウトの「同じシリーズの記事」で回遊を作る

## 運用上の注意

- 記事は `_templates/article-template.md` を `_posts/YYYY-MM-DD-slug.md` にコピーして作る
- 外部チャネルの URL を変える場合は `_config.yml` の `channels` だけを直す（本文は `site.channels.*` を参照している）
- 分離ルール: ほかのブランド（別メディア）への言及・リンクは入れない

## 画像素材について

サイト内の写真は、すべて Pexels の実写フリー素材（Pexels License、商用利用可・クレジット表記不要）を使用。AI生成画像は使っていない。人物の顔が大きく写るもの、企業ロゴが読めるものは選んでいない。

| ファイル | 配置先 | 素材 | 作者 | 写真ページ |
|---|---|---|---|---|
| `assets/images/hero-night-laptop.jpg` | トップ（ヒーロー） | 夜の部屋で光るノートPCとマグカップ、窓外の街の明かり | SHVETS production | https://www.pexels.com/photo/8037008/ |
| `assets/images/profile-desk-man.jpg` | 部長について | 薄暗い部屋でノートPCに向かう男性の手元 | Faye Tsui | https://www.pexels.com/photo/17511838/ |
| `assets/images/desk-1am.jpg` | シリーズ「朝には終わってた」 | 午前1時のデスク（ノートPC・モニター・ヘッドホン） | Julien Bachelet | https://www.pexels.com/photo/880989/ |

## ローカル検証について

- 2026-11-19 にローカルビルド検証を実施し、合格した（Jekyll 4.3.2 / Ruby 3.2.9）。詳細は `BUILD確認_2026-11-19.md`。
- 再ビルド手順: `export PATH="/opt/hostedtoolcache/Ruby/3.2.9/x64/bin:$PATH"` のうえで、このディレクトリで `LANG=C.utf8 LC_ALL=C.utf8 jekyll build`（Ruby は `~/local/ruby-3.2.9/` にポータブル配置、Jekyll 4.3.2 は gem で導入済み。UTF-8 ロケールが無いと日本語ファイル名の照合でエラーになるため必須）。
- GitHub Pages の標準ビルド（github-pages gem）で扱える範囲の Liquid・記法のみを使っている。初回アップロード時に Pages のビルド結果も確認すること。
