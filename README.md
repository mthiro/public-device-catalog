# public-device-catalog

公開可能な「推奨試験端末カタログ」を置く **Public** リポジトリ。アプリ (`MobileDeviceManager`) の **Public モード** はここから `raw.githubusercontent.com` 経由で `devices.json` を取得する。

## 対比: Private データとの違い

| 項目 | Private (`private-device-catalog`) | Public (`public-device-catalog`) |
|---|---|---|
| 可視性 | Private | Public |
| 認証 | Fine-grained PAT | 不要 |
| 取得先 | Contents API (`api.github.com`) | `raw.githubusercontent.com` (CDN) |
| 代表的データ | シリアル、貸出者、ステータス | モデル名、OS、検証ポイント |
| レート制限 | 5000 req/h (PAT) | 実質無制限 (CDN) |
| CDN キャッシュ | なし (常に最新) | あり (5 分程度の遅延可能性) |
| コミットメタデータ | Commits API (PAT) | Commits API (未認証 60/h) |

## 想定ユースケース

- 推奨試験端末カタログの社外公開 (OSS プロダクトのサポート対象リスト)
- QA チェックリスト、動作確認済み端末一覧
- マスタデータ (国/通貨/タイムゾーン等、公開可能なもの)

## devices.json のスキーマ

Private 版と同じ `devices.schema.json` を共有します (`serial` は "PUBLIC" 等の定数で埋めるだけ)。
