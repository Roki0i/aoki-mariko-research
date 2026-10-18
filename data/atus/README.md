# ATUS 2023–2025 | 公式データ保管

**現在このフォルダにはZIP本体を登録していません。** BLS公式データの入手後、以下の6ファイルを `data/atus/zips/` にアップロードしてください。ZIPは展開しません。

| 年 | Activity | Respondent |
|---|---|---|
| 2023 | `atusact-2023.zip` | `atusresp-2023.zip` |
| 2024 | `atusact-2024.zip` | `atusresp-2024.zip` |
| 2025 | `atusact-2025.zip` | `atusresp-2025.zip` |

- 出典: [BLS ATUS公開データ](https://www.bls.gov/tus/data.htm)
- 個別の公式URL: [sources.csv](sources.csv)
- 必要変数: Activity `TUCASEID, TEWHERE, TUACTDUR24, TUACTIVITY_N` / Respondent `TUCASEID, TUFINLWGT`
- GitHubリポジトリはPrivateのままにし、Colabからは限定された認証トークンで読み込みます。
- Colabシークレット `ATUS_GITHUB_TOKEN` に **Fine-grained PAT / Contents: Read-only / このリポジトリのみ**のトークンを保存し、ノートブックからのアクセスを許可します。トークンはGitHubに書かないでください。
- 必要ファイルがない場合、ノートブックはBLS取得、その後手動アップロードに切り替わります。
- BLS自動取得は環境によってHTTP 403になる場合があります。手動でブラウザから公式ZIPを入手してください。
- ZIPの配布内容・利用条件・更新状況はBLSで確認してください。元データを再公開する際は公開範囲にも注意してください。

### 研究上の注意

`TEWHERE=7` は「その他店舗・モール」であり、書店のみではありません。`TUACTDUR24` を使った1日場所分類別の合計時間は、個別の入店から退店までの滞在時間ではありません。便意はATUSに記録されていません。
