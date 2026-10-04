# マハロカーズ WEB特設LP 公開作業指示書

このフォルダは、株式会社マハロカーズ（京都のレクサス専門店）の
Google広告専用ランディングページ(LP)一式です。
GitHub Pages で公開するための作業をお願いします。

## フォルダ構成

- `index.html` … LP本体（CSS・JSは内蔵）
- `cars.json` … 在庫データ（在庫更新はこのファイルだけ編集する）
- `images/car1.jpg`〜`car6.jpg` … 車両写真（仮素材）
- `README.md` … 人間向けの説明

## 先に守ってほしいルール

- **パスワード・トークンを私に聞いたり、ファイルに書いたりしない。** 認証は私が `gh auth login` 済みの状態を使う
- **リポジトリを作る前に、必ず私に確認を取る**（アカウント名・リポジトリ名・Public であること）
- `index.html` の以下は**変更しない**
  - `<meta name="robots" content="noindex, nofollow">`（広告専用ページのため検索に出さない）
  - フォームの `action`（formsubmit.co 宛）と、hidden の `_subject` / `流入経路`
  - 電話の合言葉「WEB特設ページを見た」の文言
- `GTM-XXXXXXX` は私が実際のIDを伝えるまで**そのまま残す**

## 作業1：アカウント確認（最初に必ず実施）

1. `gh auth status` を実行する
2. ログイン中のアカウントが **`topas-code1997`** であることを確認する
3. 別アカウント（例：`kanetsuki01`）だった場合は**作業を止めて、私に報告する**。勝手に切り替えたり作成したりしない

## 作業2：リポジトリ作成と push

私の確認を取ったうえで実施する。

1. このフォルダで `git init`、初回コミット（`README.md` `CLAUDE.md` も含めてよい）
2. `topas-code1997` 配下に **Public** リポジトリ `mahalocars-gs-lp` を作成して push（デフォルトブランチは `main`）

## 作業3：GitHub Pages の有効化

1. `main` ブランチのルート（`/`）を公開元にして Pages を有効化する（`gh api` 等）
2. ビルド完了を待つ（数分かかる場合あり）

## 作業4：公開後の動作確認

1. 公開URL（`https://topas-code1997.github.io/mahalocars-gs-lp/`）に `curl -I` で 200 が返ることを確認
2. `cars.json` が取得できること、`images/` の画像が取得できることを確認
3. 確認結果と公開URLを私に報告する

ローカル確認が必要な場合は `python3 -m http.server` を使うこと
（`file://` で直接開くと `cars.json` の読み込みが失敗するため）。

## 後日の作業（私から指示があったときだけ実施）

- **GTM IDの差し替え**：`index.html` 内の `GTM-XXXXXXX`（2箇所）を、私が伝えたIDに置換 → commit → push
- **在庫の更新**：`cars.json` の追加・変更・削除、売約済みは `"status": "sold"`（LP上は非表示になる）→ commit → push
- **写真の差し替え**：私が用意した画像を `images/` に同名で上書き → commit → push

## この作業の対象外（私が自分でやる）

- Googleタグマネージャーの設定、Google広告のアカウント開設・出稿設定
- formsubmit.co の確認メールのリンククリック
- 独自ドメインの取得・DNS設定

## 補足

- 車両写真は既存サイトのスクリーンショットから仮に切り出したもの。画質は高くないので、後で差し替える予定
- 古物商許可番号は載せず、公式サイト（mahalocars.jp）へのリンクで代替している。勝手に追記しない
