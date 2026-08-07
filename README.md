# webtools

無料で使える簡易Webツール集(静的HTML、ビルド不要)。GitHub Pagesで公開しています。

## 収録ツール

- [AIコスト計算機](https://men0tai0ko.github.io/webtools/ai-cost-calculator/)([ソース](ai-cost-calculator/)) — Claude・GPT・GeminiのAPI料金をトークン数から概算計算し、モデル別に1回あたり・月間コストを比較
- [給与手取り計算機](https://men0tai0ko.github.io/webtools/salary-calculator/)([ソース](salary-calculator/)) — 額面年収から社会保険料・所得税・住民税を差し引いた手取り年収・月収を概算計算
- [AI副業タイプ診断](https://men0tai0ko.github.io/webtools/side-hustle-quiz/)([ソース](side-hustle-quiz/)) — 5問の質問から、向いているAI活用副業のタイプを診断(外部API不使用、全てブラウザ内で完結)
- [AIプロンプトテンプレ集](https://men0tai0ko.github.io/webtools/prompt-library/)([ソース](prompt-library/)) — 記事作成・仕事効率化・SNS発信ですぐ使えるプロンプトをカテゴリ・キーワード検索してコピーできる(外部API不使用)

## 開発

各ツールは `<ツール名>/index.html` に単一ファイルで実装。外部ビルドツール不要、ブラウザで直接開いて確認できます。

- 価格データ(`ai-cost-calculator/index.html` 内の `models` 配列)は各社の価格改定に応じて随時更新してください。
- 税率・保険料率(`salary-calculator/index.html` 内の各種定数)は年度が変わるたびに国税庁・協会けんぽ・厚生労働省の最新情報に合わせて更新してください。
- `side-hustle-quiz/index.html` 内の `NOTE_ARTICLE_URL` は、診断結果からの誘導先(現在は有料記事 article_01 の個別URLを設定済み)。
- `prompt-library/index.html` 内の `prompts` 配列にプロンプトを追加すると、検索・カテゴリフィルタに自動で反映されます。
