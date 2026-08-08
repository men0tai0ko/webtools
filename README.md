# webtools

無料で使える簡易Webツール集(静的HTML、ビルド不要)。GitHub Pagesで公開しています。

## 収録ツール

- [AIコスト計算機](https://men0tai0ko.github.io/webtools/ai-cost-calculator/)([ソース](ai-cost-calculator/)) — Claude・GPT・GeminiのAPI料金をトークン数から概算計算し、モデル別に1回あたり・月間コストを比較
- [給与手取り計算機](https://men0tai0ko.github.io/webtools/salary-calculator/)([ソース](salary-calculator/)) — 額面年収から社会保険料・所得税・住民税を差し引いた手取り年収・月収を概算計算
- [AI副業タイプ診断](https://men0tai0ko.github.io/webtools/side-hustle-quiz/)([ソース](side-hustle-quiz/)) — 5問の質問から、向いているAI活用副業のタイプを診断(外部API不使用、全てブラウザ内で完結)
- [AIプロンプトテンプレ集](https://men0tai0ko.github.io/webtools/prompt-library/)([ソース](prompt-library/)) — 記事作成・仕事効率化・SNS発信ですぐ使えるプロンプトをカテゴリ・キーワード検索してコピーできる(外部API不使用)
- [フリーランス消費税・請求書計算機](https://men0tai0ko.github.io/webtools/freelance-tax-calculator/)([ソース](freelance-tax-calculator/)) — 請求書の税込・税抜計算と、インボイス登録した場合の消費税納税額(2割特例・簡易課税)を概算比較
- [画像圧縮・リサイズツール](https://men0tai0ko.github.io/webtools/image-compressor/)([ソース](image-compressor/)) — 画像をブラウザ内(Canvas API)だけで圧縮・リサイズ。サーバー送信なし、外部API不使用
- [WAVマスタリングスタジオ](https://men0tai0ko.github.io/webtools/mastering-studio/)([ソース](mastering-studio/)) — EQ・マルチバンドコンプ・ステレオ幅調整・ITU-R BS.1770本格LUFS正規化をWeb Audio APIだけで実装。WAV/MP3(lamejs)で書き出し可能
- [見積書・請求書作成ツール](https://men0tai0ko.github.io/webtools/invoice-generator/)([ソース](invoice-generator/)) — 発行者・請求先・品目・消費税・振込先を入力して見積書/請求書を作成し、`window.print()`でPDF保存(外部PDFライブラリ不使用、発行者情報のみlocalStorageに保存)

## 今後の追加候補(未実装)

- **文章セルフチェック/類似度比較ツール** — note読者コメント(2026-08-07、記事「仕事での気づき」)がきっかけ。「Web全体との照合」「AI検出」は外部有料APIが必要かつ精度面のリスクもあるため対象外。代わりに、①自分の文章にAI文にありがちな表現パターン(接続詞の多用・文長の均一さ等)がないかをブラウザ内で分析する「セルフチェック」、②2つの文章(下書き vs 参照元など)をn-gram等で比較する「類似度比較」の2機能に絞れば、外部API不使用のまま実装可能。実装時はこの2機能構成を踏襲する。

## 開発

各ツールは `<ツール名>/index.html` に単一ファイルで実装。外部ビルドツール不要、ブラウザで直接開いて確認できます。

- 価格データ(`ai-cost-calculator/index.html` 内の `models` 配列)は各社の価格改定に応じて随時更新してください。
- 税率・保険料率(`salary-calculator/index.html` 内の各種定数)は年度が変わるたびに国税庁・協会けんぽ・厚生労働省の最新情報に合わせて更新してください。
- `side-hustle-quiz/index.html` 内の `NOTE_ARTICLE_URL` は、診断結果からの誘導先(現在は有料記事 article_01 の個別URLを設定済み)。
- `prompt-library/index.html` 内の `prompts` 配列にプロンプトを追加すると、検索・カテゴリフィルタに自動で反映されます。
- `freelance-tax-calculator/index.html` の2割特例は2026年9月30日までの経過措置です。期限を過ぎたら該当箇所の表示・計算ロジックを見直してください。
- `mastering-studio/` は他ツールと異なり単一HTML構成ではなく、MP3エンコーダ`lame.min.js`(lamejs、MITライセンス、npm経由で取得)を同フォルダに同梱しています。クロスオーバー周波数(200Hz/2.5kHz)やコンプの閾値・レシオのマッピング係数は`index.html`内の`buildProcessingChain`にハードコードされています。
- `invoice-generator/` はPDF生成にjsPDF等のライブラリを使わず、`window.print()` + `@media print`で「印刷してPDFとして保存」させる方式を採用(日本語フォント埋め込み問題を回避するための意図的な設計判断)。混合税率(8%/10%が混在する請求書)には対応していない点に注意。
