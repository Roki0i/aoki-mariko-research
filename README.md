# 青木まりこ現象のデータ分析

書店に入ると便意を感じるとされる「青木まりこ現象」について、公開済みの行動観察資料と公的統計を用いて、施設別の活動時間を記述的に比較する卒業研究です。本リポジトリはコード、分析用データ、生成済みの表・図の正本です。

## 研究課題

1. 松田（2003）の行動観察データでは、書店と図書館の滞在時間にどのような違いがみられるか。
2. American Time Use Survey（ATUS）では、図書館、その他店舗・モール、スーパー、飲食店・バーの1日の日誌上の活動時間にどのような違いがみられるか。

いずれも施設別の時間を記述・比較する分析であり、便意が生じる原因や施設滞在の因果効果を推定するものではありません。

## 使用データ

- **分析①**：松田千春（2003）「情報探索におけるブラウジング行動：図書館と書店における行動観察を基にして」の表5–8から整理した40件。確認済みデータは [`data/processed/matsuda_40_data_checked.csv`](data/processed/matsuda_40_data_checked.csv) に保存しています。
- **分析②**：米国労働統計局（BLS）の [American Time Use Survey](https://www.bls.gov/tus/data.htm) 2023–2025年公開利用ファイル。ActivityとRespondentの公式ZIP 6件を [`data/atus/zips/`](data/atus/zips/) に保存しています。取得元は [`data/atus/sources.csv`](data/atus/sources.csv) を参照してください。
- **参考資料**：Google Trendsの書き出しデータと、文献・報道資料の整理表。これらは上記2分析の集計値には使用していません。
- **検討中の公開調査**：森永乳業（2024）の[公表集計の確認メモ](docs/notes/morinaga_2024_survey_review.md)と[設問別集計CSV](data/processed/morinaga_2024_published_aggregates.csv)。同調査の集計を転記した参考資料で、元の個票データではありません。

## リポジトリ構成

```text
notebooks/           Google Colab / Jupyter用の分析ノートブック
data/atus/           ATUSの出典情報と公式ZIP
data/processed/      確認済みの松田（2003）40件データ
data/google_trends/  Google Trendsの書き出しデータ
results/tables/      分析で生成した集計表
results/figures/     分析で生成した図
docs/notes/          分析結果の説明
docs/references/     文献・報道資料の整理表
```

## Google Colabで実行する

- [分析①：松田（2003）の書店・図書館比較を開く](https://colab.research.google.com/github/Roki0i/aoki-mariko-research/blob/main/notebooks/01_dwell_time.ipynb)
- [分析②：ATUS 2023–2025年分析を開く](https://colab.research.google.com/github/Roki0i/aoki-mariko-research/blob/main/notebooks/02_atus.ipynb)

Colabで上から順にすべてのセルを実行してください。分析②は公開GitHubのRaw URLからATUS ZIP 6件を認証なしで取得します。GitHubトークン、APIキー、Google Driveのマウント、手動アップロードは不要です。

## ローカルで再現する

Python 3.10以降を対象とし、Python 3.12で実行確認しています。ノートブックはGoogle Colabにも対応しています。

```bash
git clone https://github.com/Roki0i/aoki-mariko-research.git
cd aoki-mariko-research
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS / Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter notebook
```

各ノートブックを開き、上から順に全セルを実行します。分析①と分析②は独立しており、どちらから実行しても構いません。ATUSのダウンロード済み中間データは `data/raw/atus/`、集計用の中間CSVは `data/processed/atus/` に生成され、Git管理から除外されます。表・図・分析メモは `results/` と `docs/notes/` に生成されます。

## 分析結果

### 分析①：松田（2003）

- [分析メモ](docs/notes/aoki_dwell_analysis_report.md)
- [場所区分別集計表](results/tables/matsuda_group_summary.csv)
- [施設別集計表](results/tables/matsuda_facility_summary.csv)
- [場所区分別の箱ひげ図](results/figures/aoki_dwell_group_boxplot.png)
- [施設別の箱ひげ図](results/figures/aoki_dwell_facility_boxplot.png)

### 分析②：ATUS 2023–2025

- [3年統合の集計表](results/tables/atus_location_summary_pooled_2023_2025.csv)
- [年別の集計表](results/tables/atus_location_summary_by_year_2023_2025.csv)
- [無加重分布の箱ひげ図](results/figures/atus_location_boxplot_2023_2025.png)
- [調査ウェイトを用いた加重平均の図](results/figures/atus_weighted_means_2023_2025.png)
- [集計結果の分析メモ](docs/notes/atus_colab_report_2023_2025.md)

3年統合の加重平均は、Library 89.14分（n=141）、Other store / mall 60.68分（n=3,860）、Grocery store 45.74分（n=3,534）、Restaurant / bar 66.22分（n=4,882）です。

## 仮説と証拠の対応

森永乳業（2024）・松田（2003）・ATUS（2023〜2025）の3資料の比較可能性、仮説H1〜H3への対応、未解決の研究課題を[仮説・証拠対応表](docs/notes/hypothesis_evidence_matrix.md)にまとめています。便意の原因や書店特有性を直接証明するものではありません。

## 研究上の制約

### ATUS

- ATUSでは書店を単独で識別できません。`Other store / mall` は書店だけの分類ではありません。
- `TUACTDUR24` を用いた値は、1日の日誌上で各施設カテゴリーに分類された活動時間の合計であり、訪問1回の入店から退店までの滞在時間ではありません。
- 便意・排便欲求は測定されていないため、施設滞在が便意に与える因果効果は推定できません。
- 集計対象は、その施設カテゴリーで少なくとも1活動を記録した日誌です。非訪問者の0分を含む人口全体平均ではありません。
- 同じ回答者が複数の施設カテゴリーに含まれる場合があり、カテゴリー別の標本数は相互排他的ではありません。
- 図書館の標本数は他施設より少ないため、単純比較には注意が必要です。
- 年別数値の変化について、複雑標本設計を考慮した信頼区間や検定を実施していないため、統計的に有意な傾向とは断定できません。
- 加重平均の図はATUSの最終ウェイトを使用します。箱ひげ図は無加重の分布であり、両者は同じ集計方法ではありません。

### 松田（2003）

- 対象は40人で、観察施設数も限られています。個人と施設の非独立性や選択バイアスに注意が必要です。
- 便意そのものは測定されていません。
- 統計的な有意差が認められないことは、差が存在しないことの証明ではありません。
