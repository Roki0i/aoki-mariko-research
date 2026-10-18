# ATUS 2023–2025 | 公式データ保管

以下のBLS公式ZIP 6件を `data/atus/zips/` に登録しています。ZIPは展開しません。

| 年 | Activity | Respondent |
|---|---|---|
| 2023 | `atusact-2023.zip` | `atusresp-2023.zip` |
| 2024 | `atusact-2024.zip` | `atusresp-2024.zip` |
| 2025 | `atusact-2025.zip` | `atusresp-2025.zip` |

- 出典: [BLS ATUS公開データ](https://www.bls.gov/tus/data.htm)
- 個別の公式URL: [sources.csv](sources.csv)
- 必要変数: Activity `TUCASEID, TEWHERE, TUACTDUR24` / Respondent `TUCASEID, TUFINLWGT`
- `notebooks/02_atus.ipynb` は公開GitHubのRaw URLからZIP6件を認証なしで自動取得します。トークン設定・手動アップロードは不要です。
- ファイル名・サイズ・Git blobハッシュ・ZIP整合性・内部データ名を検証します。
- GitHubアクセスに失敗した場合は原因を表示して停止し、BLS取得や手動アップロードには切り替わりません。
- 元ZIPを変更した場合はノートブックの`EXPECTED_ZIPS`（サイズ・ハッシュ）も更新してください。
- ZIPの配布内容・利用条件・更新状況はBLSで確認してください。元データを再公開する際は公開範囲にも注意してください。

### 研究上の注意

`TEWHERE=7` は「その他店舗・モール」であり、書店のみではありません。`TUACTDUR24` を使った1日場所分類別の合計時間は、個別の入店から退店までの滞在時間ではありません。便意はATUSに記録されていません。
