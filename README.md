# 青木まりこ現象の公開データ分析

書店で便意を催すといわれる「青木まりこ現象」の**書店特有性や関連要因**を、公開資料から探索する研究です。原因の特定は目的としていません。

## 対象資料と主な結果

| 資料 | 確認できたこと | 注意点 |
| --- | --- | --- |
| 森永乳業（2024）の公表調査 | 書店での便意経験29.8%。お通じの悩みあり46.0%、なし19.2% | 異なる設問・未調整の関連。個票解析ではない |
| 松田（2003）の観察40件 | 平均滞在時間：書店18.24分、図書館34.97分 | 各20件、便意は未測定。探索的検定p=0.273 |
| 米国BLS ATUS（2023〜2025） | 公開個票から施設分類別の活動時間を再集計 | 書店を単独識別不可。1訪問の滞在時間ではない |

**現状では書店特有性・原因は判断できません。** Google Trendsは検索関心の背景資料で、便意の発生率ではありません。測定対象の異なる資料を単純に合算しません。

[仮説と根拠](docs/notes/hypothesis_evidence_matrix.md) · [松田データの検証](docs/notes/aoki_dwell_analysis_report.md) · [ATUSの解釈](docs/notes/atus_colab_report_2023_2025.md)

## 再現方法

- [Notebook 01：書店と図書館の滞在時間](https://colab.research.google.com/github/Roki0i/aoki-mariko-research/blob/main/notebooks/01_dwell_time.ipynb)
- [Notebook 02：ATUSの活動時間](https://colab.research.google.com/github/Roki0i/aoki-mariko-research/blob/main/notebooks/02_atus.ipynb)

ローカル実行（Python 3.10以上）：

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

入力は `data/`、分析コードは `notebooks/`、結果は `results/` にあります。研究メモ・出典は `docs/` を参照してください。
