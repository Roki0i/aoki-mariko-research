# 青木まりこ現象 卒業研究

青木まりこ現象に関する卒業研究のうち、再現可能な分析コード、公開資料由来の小規模データ、集計結果、図表を整理した非公開リポジトリです。

## 構成

- `notebooks/`: 書店・図書館の滞在時間分析とATUS二次分析
- `data/reference/`: 公開資料を整理した参照データ
- `data/processed/`: 論文表から転記した小規模データと集計表
- `figures/`: 滞在時間分析の図表
- `reports/`: 分析結果と限界の要約

## 再現方法

Python 3.11を推奨します。

```bash
python -m venv .venv
pip install -r requirements.txt
```

その後、JupyterまたはGoogle Colabでノートブックを上から順に実行してください。ATUSノートブックはBLS公開データを取得します。自動取得できない場合はノートブック記載の公式URLから手動でダウンロードします。

## 取り扱い

- ノートブックの出力、実行回数、Colab実行者メタデータは削除済みです。
- アンケートフォーム、回答、個人情報、秘密情報、卒論本文の共同編集ファイル、Google Apps Scriptは含めていません。
- ATUSの元ZIP、個人日誌単位の加工データなど大容量・再取得可能なデータは含めていません。
- 参照データと第三者資料の利用条件は各配布元に従ってください。
- 本リポジトリの分析だけで青木まりこ現象の原因を特定することはできません。

## ATUSのGitHub ZIP保管

`data/atus/zips/` に2023–2025年の公式ZIPファイル6個を格納します。取得URL一覧は `data/atus/sources.csv` を参照してください。

- 2023年の既存集計 `data/processed/atus_location_summary.csv` は**2023年のみ**。3年分の集計結果と混同しないでください。
- ZIP未登録の段階では `data/atus/zips/.gitkeep` のみが存在します。ノートブックはGitHub取得ができなければBLS公式サイト、次にColabへの手動アップロードを試します。
- GitHubのPrivateリポジトリをColabから読む場合は、Fine-grained Personal Access Token を**このリポジトリに限定し、Contents: Read-only**にして作成し、Colabシークレット `ATUS_GITHUB_TOKEN` に登録します。**トークンをノートブック、GitHub、出力ログへ記載しないでください**。
- ZIPはBLS公表の公開研究データですが、ATUSは書店単独の分類や便意を記録していません。ATUSの元データを大きなCSVに展開してコミットする必要はありません。
