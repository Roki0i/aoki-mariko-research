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
