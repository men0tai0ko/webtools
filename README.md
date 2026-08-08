# webtools

無料で使える簡易Webツール集(静的HTML、ビルド不要)。GitHub Pagesで公開しています。

[トップページ(全ツール一覧)](https://men0tai0ko.github.io/webtools/)([ソース](index.html))

## 収録ツール

- [AIコスト計算機](https://men0tai0ko.github.io/webtools/ai-cost-calculator/)([ソース](ai-cost-calculator/)) — Claude・GPT・GeminiのAPI料金をトークン数から概算計算し、モデル別に1回あたり・月間コストを比較
- [給与手取り計算機](https://men0tai0ko.github.io/webtools/salary-calculator/)([ソース](salary-calculator/)) — 額面年収から社会保険料・所得税・住民税を差し引いた手取り年収・月収を概算計算
- [AI副業タイプ診断](https://men0tai0ko.github.io/webtools/side-hustle-quiz/)([ソース](side-hustle-quiz/)) — 5問の質問から、向いているAI活用副業のタイプを診断(外部API不使用、全てブラウザ内で完結)
- [AIプロンプトテンプレ集](https://men0tai0ko.github.io/webtools/prompt-library/)([ソース](prompt-library/)) — 記事作成・仕事効率化・SNS発信ですぐ使えるプロンプトをカテゴリ・キーワード検索してコピーできる(外部API不使用)
- [フリーランス消費税・請求書計算機](https://men0tai0ko.github.io/webtools/freelance-tax-calculator/)([ソース](freelance-tax-calculator/)) — 請求書の税込・税抜計算と、インボイス登録した場合の消費税納税額(2割特例・簡易課税)を概算比較
- [画像圧縮・リサイズツール](https://men0tai0ko.github.io/webtools/image-compressor/)([ソース](image-compressor/)) — 画像をブラウザ内(Canvas API)だけで圧縮・リサイズ。サーバー送信なし、外部API不使用
- [WAVマスタリングスタジオ](https://men0tai0ko.github.io/webtools/mastering-studio/)([ソース](mastering-studio/)) — EQ・マルチバンドコンプ・ステレオ幅調整・ITU-R BS.1770本格LUFS正規化をWeb Audio APIだけで実装。WAV/MP3(lamejs)で書き出し可能
- [見積書・請求書作成ツール](https://men0tai0ko.github.io/webtools/invoice-generator/)([ソース](invoice-generator/)) — 発行者・請求先・品目・消費税・振込先を入力して見積書/請求書を作成し、`window.print()`でPDF保存(外部PDFライブラリ不使用、発行者情報のみlocalStorageに保存)
- [QRコード生成ツール](https://men0tai0ko.github.io/webtools/qr-generator/)([ソース](qr-generator/)) — テキスト/URL・Wi-Fi・メール・電話番号のQRコードを生成し、サイズ・誤り訂正レベル・配色を調整してPNGでダウンロード(`qrcode-generator`ライブラリをローカル同梱)
- [カラーパレット&コントラストチェッカー](https://men0tai0ko.github.io/webtools/color-tools/)([ソース](color-tools/)) — 画像から主要な配色をCanvas APIで自動抽出し、WCAG AA/AAA基準のコントラスト比を判定(外部API・ライブラリ不使用)
- [文字数&原稿用紙換算・Markdownプレビュー](https://men0tai0ko.github.io/webtools/note-writing-tools/)([ソース](note-writing-tools/)) — 文字数・原稿用紙換算(400字/200字詰め)・読了時間の目安を計算し、簡易Markdownをリアルタイムプレビュー(自前実装、外部ライブラリ不使用)
- [パスワード生成&強度チェッカー](https://men0tai0ko.github.io/webtools/password-generator/)([ソース](password-generator/)) — `crypto.getRandomValues`による安全な乱数でパスワードを生成し、既存パスワードの強度をエントロピーベースで判定(サーバー送信・保存一切なし)
- [文章セルフチェック&類似度比較ツール](https://men0tai0ko.github.io/webtools/text-self-check/)([ソース](text-self-check/)) — 紋切り型の接続・結び・ヘッジ表現の頻度、文長のばらつき、文末表現の偏りをチェック。2つの文章の文字n-gram類似度(Dice係数)と一致箇所ハイライトも表示(AI検出ではなく紋切り型表現の可視化として明確に位置づけ)

## 開発

各ツールは `<ツール名>/index.html` に単一ファイルで実装。外部ビルドツール不要、ブラウザで直接開いて確認できます。

- 価格データ(`ai-cost-calculator/index.html` 内の `models` 配列)は各社の価格改定に応じて随時更新してください。
- 税率・保険料率(`salary-calculator/index.html` 内の各種定数)は年度が変わるたびに国税庁・協会けんぽ・厚生労働省の最新情報に合わせて更新してください。
- `side-hustle-quiz/index.html` 内の `NOTE_ARTICLE_URL` は、診断結果からの誘導先(現在は有料記事 article_01 の個別URLを設定済み)。
- `prompt-library/index.html` 内の `prompts` 配列にプロンプトを追加すると、検索・カテゴリフィルタに自動で反映されます。
- `freelance-tax-calculator/index.html` の2割特例は2026年9月30日までの経過措置です。期限を過ぎたら該当箇所の表示・計算ロジックを見直してください。
- `mastering-studio/` は他ツールと異なり単一HTML構成ではなく、MP3エンコーダ`lame.min.js`(lamejs、MITライセンス、npm経由で取得)を同フォルダに同梱しています。クロスオーバー周波数(200Hz/2.5kHz)やコンプの閾値・レシオのマッピング係数は`index.html`内の`buildProcessingChain`にハードコードされています。
- `invoice-generator/` はPDF生成にjsPDF等のライブラリを使わず、`window.print()` + `@media print`で「印刷してPDFとして保存」させる方式を採用(日本語フォント埋め込み問題を回避するための意図的な設計判断)。混合税率(8%/10%が混在する請求書)には対応していない点に注意。
- `qr-generator/` は`qrcode-generator`(kazuhikoarase、MIT、npm経由で取得)の`qrcode.js`+`qrcode_UTF8.js`を同梱。日本語等マルチバイト文字を含めるには`qrcode_UTF8.js`の読み込みが必須(`qrcode.stringToBytes`をUTF-8版に上書きする仕組み)。QRコードの描画は`isDark()`/`getModuleCount()`から自前でcanvasに描画しており(ライブラリ付属の`renderTo2dContext`は配色固定のため使っていない)、クワイエットゾーンは4モジュール固定。
- `color-tools/` の配色抽出は外部ライブラリを使わず、画像を最大150px程度に縮小してから各チャンネルを8段階に量子化してバケット集計し、出現頻度上位6色を抽出する自前ロジック(`extractPalette`関数)。コントラスト比はWCAG 2.xの相対輝度計算式をそのまま実装。
- `note-writing-tools/` のMarkdownパーサー(`renderMarkdown`関数)は見出し・強調・リスト・引用・コードブロック・リンク・区切り線のみに対応した簡易実装。ネストしたリストやテーブルには非対応。文字数は`Array.from(text).length`でサロゲートペア(絵文字等)を正しく1文字として数えている(`.length`だとUTF-16コード単位で数えて2文字になってしまうため)。
- `password-generator/` の乱数生成は`Math.random()`ではなく`crypto.getRandomValues()`を使用し、`secureRandomIndex`関数で剰余バイアスを除去(棄却法)。文字種の最低1文字保証は「生成後に欠けたクラスを上書き修正する」方式だと別のクラスの唯一の文字を誤って消してしまうバグを実装時に踏んだため、「各文字種を先に確保してからFisher-Yatesでシャッフルする」方式に変更済み(2026-08-08、500試行×複数文字数長で0件失敗を確認)。新しい生成ロジックを書く際はこの失敗パターンを踏まないよう注意。
- `text-self-check/` は形態素解析(単語分割)を一切使わず、①紋切り型表現は固定フレーズリストとの単純な部分一致カウント、②類似度比較は文字n-gram(2/3文字)+Dice係数で実装。どちらも精度は粗いが外部ライブラリ・APIなしで実現できる設計。UIでは「AI検出ツールではない」ことを明示的に免責しており、この位置づけを崩さないこと(過去に「AI検出」自体は精度面のリスクで不採用と判断した経緯があるため)。
