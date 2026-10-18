# 青木まりこ現象のデータ分析

青木まりこ現象について、公開データを使って書店とその他施設の行動・活動時間などを比較する卒業研究です。

## 内容

- 松田（2003）の行動観察データによる書店・図書館の滞在時間比較
- ATUS 2023–2025年の場所別活動時間の3年統合・年別集計
- Google Trendsの検索動向データの保管

## 構成

- `notebooks/`：分析用Colabノートブック
- `data/`：参照データ・加工データ・ATUSの取得元
- `results/`：集計表と図表
- `docs/`：文献一覧と分析メモ

## 分析結果（ATUS 2023–2025）

Google Colabでの実データ分析結果を保存しています。元の2023年単年結果は変更していません。

- [3年統合の集計表](results/tables/atus_location_summary_pooled_2023_2025.csv)
- [年別の集計表](results/tables/atus_location_summary_by_year_2023_2025.csv)
- [集計結果の分析メモ](docs/notes/atus_colab_report_2023_2025.md)

3年統合の加重平均（分）：図書館89.14（n=141）、その他店舗・モール60.68（n=3,860）、スーパー45.74（n=3,534）、飲食店・バー66.22（n=4,882）。

**解釈の制約**：書店はATUSで単独分類されず、活動時間は訪問1回の滞在時間ではなく、便意の測定値もありません。図書館は標本が少ないため、値の単純比較・年次推移の一般化に注意が必要です。厳密な標本設計を考慮した信頼区間・検定は実施していません。

## 実行

Google ColabまたはPythonのJupyter環境を使用します。ノートブックは公開GitHubから開けます。

- [ATUS分析をColabで開く](https://colab.research.google.com/github/Roki0i/aoki-mariko-research/blob/main/notebooks/02_atus.ipynb)
- ATUSの6つのZIPは公開GitHubから認証なしで自動取得します。トークンも手動アップロードも不要です。
- Colab標準環境にはATUS分析で使う `numpy`、`pandas`、`matplotlib`、`requests`、`IPython` が通常含まれています。
- ローカルで実行する場合は、次のコマンドで必要なライブラリを導入してください。パッケージ本体ではなく、依存関係を`requirements.txt`で管理しています。

```bash
pip install -r requirements.txt
```

ATUSの元データの取得方法は [data/atus/README.md](data/atus/README.md) を参照してください。

※ ATUSの調査を使用しています。場所別の活動時間と入店から退店までの滞在時間は同じ指標ではありません。便意そのものはこのデータでは測定していません。
