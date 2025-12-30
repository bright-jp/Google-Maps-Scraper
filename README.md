# Google Maps スクレイパー

## 目次
- [無料のGoogle Maps スクレイパー](#free-google-maps-scraper)
  - [セットアップとインストール](#setup-and-installation)
  - [スクレイパーの使用方法](#how-to-use-the-scraper)
  - [出力](#output)
- [スクレイピングでよくある課題](#common-scraping-challenges)
- [解決策: Bright Data Google Maps Scraper API](#solution-bright-data-google-maps-scraper-api)
  - [Google Maps Scraper API の使用](#using-google-maps-scraper-api)
  - [APIパラメータでデータ収集をカスタマイズする](#customizing-data-collection-with-api-parameters)

## 無料のGoogle Maps スクレイパー
この無料スクレイパーを使用して、Google Maps からビジネスのレビューを抽出できます。数ステップで、レビュー投稿者の詳細、評価、レビュー本文、写真などを取得できます。

### セットアップとインストール
始める前に、次の前提条件がインストールされていることを確認してください:
- Python 3.9+
- Playwright（ブラウザ自動化用）

次の手順でセットアップします:
1. リポジトリをローカルマシンにクローンします
2. `free-scraper` ディレクトリに移動します
3. 必要な依存関係をインストールします:

    ```bash
    pip install playwright
    playwright install
    ```
### スクレイパーの使用方法
スクレイパーの使い方を順に説明します:

1. `main.py` を開き、ターゲットの Google Maps URL を追加します:

    ```python
    urls = [
            "https://www.google.com/maps/place/Joe's+Pizza+Broadway/@40.7546835,-73.989604,17z/data=!3m1!5s0x89c259ab3e91ed73:0x4074c4cfa25e210b!4m8!3m7!1s0x89c259ab3c1ef289:0x3b67a41175949f55!8m2!3d40.7546795!4d-73.9870291!9m1!1b1!16s%2Fg%2F11bw4ws2mt?entry=ttu",
            "https://www.google.com/maps/place/Googleplex/@37.4220583,-122.0878991,17z/data=!4m8!3m7!1s0x808fba02425dad8f:0x6c296c66619367e0!8m2!3d37.4220541!4d-122.0853242!9m1!1b1!16zL20vMDNiYnkx?hl=en&entry=ttu",
            # Add as many URLs as you need
        ]
    ```
2. 次のコマンドでスクリプトを実行します:

    ```bash
    python main.py
    ```
### 出力
スクレイパーは結果を [free_scraper_output.json](https://github.com/luminati-io/Google-Maps-Scraper/blob/main/sample_data/free_scraper_output.json) に保存します。内容は次のとおりです:
```json
{
    "reviewer_name": "Jacqueline",
    "reviewer_link": "https://www.google.com/maps/contrib/108281841745817069467/reviews?hl=en-GB",
    "reviewer_image": "https://lh3.googleusercontent.com/a-/ALV-UjUzl62rTNZOxsKGxvlnjM3leUg7DZostYzDJvG_8DUSNEtC7p-X=w36-h36-p-rp-mo-ba4-br100",
    "rating": 5,
    "date": "a week ago",
    "text": "Went for lunch on a Tuesday at around 12:45pm. As usual, there was a line, but it moved really quickly and I was able to get my pizza 10 minutes later. Don't let the line deter you from trying Joe's! The pizza is great as always and the staff are nice. Never disappointed. I tried the caprese pizza and it was great!\n\nThere are a lot of people inside and outside so it can get hectic, but turnover for seats is quite quick and I got a seat on the bench outside almost right away.",
    "photos": [
        "https://lh5.googleusercontent.com/p/AF1QipMChGwUdQgWF9NAqdvss36KeuBZw_DAiuZy5yJj=w300-h225-p-k-no",
        "https://lh5.googleusercontent.com/p/AF1QipNvachPq2HyJU0_3hs0DsRDRChaHZrQDDKOc3hz=w300-h225-p-k-no"
    ],
    "likes_count": "1"
}
```

各レビューのエントリには次が含まれます:
- **レビュー投稿者の詳細**: 名前、プロフィールリンク、アバター画像
- **レビュー内容**: 星評価、投稿日、レビュー本文（全文）
- **メディア**: 添付写真がある場合のURL
- **エンゲージメント**: レビューが獲得した「いいね」の数

## スクレイピングでよくある課題
Google Maps からのデータのスクレイピングは非常に難しい場合があります。よく遭遇する問題は次のとおりです:
1. **動的コンテンツの読み込み:** Google Maps は、ユーザーがスクロールするとレビューが XHR/API 呼び出し経由で取得される動的読み込みの仕組みを使用しています。これらの動的リクエストを適切に処理し、コンテンツの読み込みを待機しないと、スクレイパーは部分的なデータしか取得できない可能性があります。
2. **DOM構造の変更:** Google は DOM 構造、class 名、data 属性を頻繁に更新します。そのため、構造変更に適応するようスクレイピングロジックを定期的にメンテナンスする必要があります。
3. **レート制限と検知:** Google Maps のスクレイピングはアンチボット防御を作動させる可能性があり、その結果、レート制限または IPアドレス のBANが発生する場合があります。 

## 解決策: Bright Data Google Maps Scraper API
信頼性の高い大規模なデータ抽出が必要な場合は、[Bright Data Google Maps Scraper API](https://brightdata.jp/products/serp-api/google-search/maps) を使用してください。より優れている理由は次のとおりです:
- プロキシ管理が不要です
- 世界中の任意の場所からスクレイピングできます
- 195か国にわたる 72M+ の実在IPにアクセスできます
- 複数のデータ配信オプション（S3、Cloud Storage など）
- GDPR および CCPA 準拠
- 24/7 のテクニカルサポート

さらに、試用のために **API呼び出し20回が無料** で利用できます。

## Google Maps Scraper API の使用
URL を指定するだけで、詳細な Google Maps レビューを収集できます。

<img width="700" alt="bright-data-web-scraper-api-google-maps-reviews" src="https://github.com/luminati-io/Google-Maps-Scraper/blob/main/google-maps-review-example.PNG">

> Google Maps Scraper API のセットアップに関する詳細ガイドは、[Step-by-Step Setup Guide](https://github.com/luminati-io/Google-Maps-Scraper/blob/main/scraper_api_setup.md#setting-up-google-maps-scraper-api) をご確認ください。

**主な入力パラメータ:**

| **Parameter** | **Type** | **Description**                         | **Required** |
|---------------|----------|-----------------------------------------|--------------|
| `url`         | string   | Google Maps のビジネスURL               | Yes          |
| `days_limit`  | number   | レビューを取得する対象日数 | No           |

**出力データのサンプル:**

```json
{
    "url": "https://www.google.com/maps/place/Apple+Apple+Park+Visitor+Center/@37.3327772,-122.0079593,17z/data=!4m18!1m9!3m8!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!2sApple+Apple+Park+Visitor+Center!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg!3m7!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg?entry=ttu",
    "place_id": "ChIJ0aPn18W1j4ARgC9zTSPeQRc",
    "place_name": "Apple Apple Park Visitor Center",
    "country": "US",
    "address": "10600 N Tantau Ave, Cupertino, CA 95014",
    "review_id": "ChdDSUhNMG9nS0VJQ0FnSUMzcDdqMHJRRRAB",
    "reviewer_name": "Krzysztof Wojtczak",
    "reviews_by_reviewer": 32,
    "photos_by_reviewer": "12",
    "reviewer_url": "https://www.google.com/maps/contrib/110797405132582450368/reviews?hl=en",
    "local_guide": true,
    "review_rating": 5,
    "review": "Fajnie można spędzić czas, czilując na tarasie z kawką 🤙",
    "review_date": "2024-11-09T22:18:01.713Z",
    "number_of_likes": 0,
    "response_of_owner": null,
    "response_date": null,
    "photos": [
      "https://lh5.googleusercontent.com/p/AF1QipOtSDFfVpLL5GopXJzoFbTapha0G91nmEx5aSus",
      "https://lh5.googleusercontent.com/p/AF1QipPcr5_TU6MWhAu1_K54DbxywZ4O88Q_qT7NSnhv",
      "https://lh5.googleusercontent.com/p/AF1QipNLM5jHD0iDozGHsax9ydGAWUI_pn_fujQ3Q4Wr",
      "https://lh5.googleusercontent.com/p/AF1QipPcKPwXyHDawuClpTpfV3zE7vMFO0UabmdjX9IG"
    ],
    "timestamp": "2024-11-10T07:37:58.326Z",
    "input": {
      "url": "https://www.google.com/maps/place/Apple+Apple+Park+Visitor+Center/@37.3327772,-122.0079593,17z/data=!4m18!1m9!3m8!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!2sApple+Apple+Park+Visitor+Center!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg!3m7!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg?entry=ttu",
      "days_limit": 30
    }
  }
```
出力全体は、[このサンプルJSONファイル](https://github.com/luminati-io/Google-Maps-Scraper/blob/main/sample_data/api_scraper_output.json) をダウンロードして確認できます。

**コード例:**

次は、Google Maps のレビューを収集し、結果を JSON ファイルに保存する Python スクリプトです:

```python
import requests
import json
import time


class BrightData:
    def __init__(self, api_token):
        self.api_token = api_token
        self.headers = {
            "Authorization": f"Bearer {api_token}",
            "Content-Type": "application/json",
        }

    def collect_reviews(self, urls_data):
        """
        Collect Google Maps reviews using BrightData API
        """
        # 1. Trigger data collection
        print("Starting data collection...")
        trigger_response = self._trigger_collection(urls_data)
        snapshot_id = trigger_response.get("snapshot_id")
        print(f"Snapshot ID: {snapshot_id}")

        # 2. Wait for data to be ready
        print("Waiting for data...")
        while True:
            status = self._check_status(snapshot_id)
            print(f"Status: {status}")

            if status == "ready":
                # Check if data is actually available
                data = self._get_data(snapshot_id)
                if data and len(data) > 0:
                    break
            time.sleep(10)  # Wait 10 seconds before next check

        # 3. Get and save the data
        print("Saving data...")
        filename = f"api_scraper_output.json"
        with open(filename, "w", encoding="utf-8") as f:
            json.dump(data, f, indent=2, ensure_ascii=False)
        print(f"✓ Data saved to {filename}")
        print(f"✓ Collected {len(data)} reviews")
        return data

    def _trigger_collection(self, urls_data):
        """Trigger data collection"""
        response = requests.post(
            "https://api.brightdata.com/datasets/v3/trigger",
            headers=self.headers,
            params={"dataset_id": "gd_luzfs1dn2oa0teb81",
                    "include_errors": "true"},
            json=urls_data,
        )
        return response.json()

    def _check_status(self, snapshot_id):
        """Check collection status"""
        response = requests.get(
            f"https://api.brightdata.com/datasets/v3/progress/{snapshot_id}",
            headers=self.headers,
        )
        return response.json().get("status")

    def _get_data(self, snapshot_id):
        """Get collected data"""
        response = requests.get(
            f"https://api.brightdata.com/datasets/v3/snapshot/{snapshot_id}",
            headers=self.headers,
            params={"format": "json"},
        )
        return response.json()


if __name__ == "__main__":
    # Initialize with your API token
    brightdata = BrightData("<YOUR_API_TOKEN>")

    # Define URLs to collect reviews from
    urls_to_collect = [
        {
            "url": "https://www.google.com/maps/place/Apple+Apple+Park+Visitor+Center/@37.3327772,-122.0079593,17z/data=!4m18!1m9!3m8!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!2sApple+Apple+Park+Visitor+Center!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg!3m7!1s0x808fb5c5d7e7a3d1:0x1741de234d732f80!8m2!3d37.332773!4d-122.0053844!9m1!1b1!16s%2Fg%2F11rjtz4vtg?entry=ttu",
            "days_limit": 30,
        },
        {
            "url": "https://www.google.com/maps/place/Joe's+Pizza+Broadway/@40.7546835,-73.989604,17z/data=!3m1!5s0x89c259ab3e91ed73:0x4074c4cfa25e210b!4m8!3m7!1s0x89c259ab3c1ef289:0x3b67a41175949f55!8m2!3d40.7546795!4d-73.9870291!9m1!1b1!16s%2Fg%2F11bw4ws2mt?entry=ttu",
            "days_limit": 25,
        },
    ]

    # Collect reviews
    reviews = brightdata.collect_reviews(urls_to_collect)
```

**コードの仕組み:**
1. **API Token が必要:** まず API token が必要です。まだお持ちでない場合は、[Google Maps Scraper API setup guide](https://github.com/luminati-io/Google-Maps-Scraper/blob/main/scraper_api_setup.md#setting-up-google-maps-scraper-api) に従ってください。
2. **データ収集の開始:** コードに API token を渡すと、指定したパラメータでデータ収集を開始します。これにより、リクエストを追跡するために使用する `snapshot_id` が返されます。
3. **結果を待機:** データ収集の完了まで数分かかります。この間、コードは `snapshot_id` のステータスを継続的に確認します:
    - ステータス "running" = データはまだ収集中です
    - ステータス "ready" = データ収集が完了し、JSON ファイルに保存されました
4. **追加パラメータ:** `_trigger_collection` 関数に追加のパラメータを指定して、データ収集をカスタマイズできます。利用可能なパラメータや各種データ配信方法については、[次のセクション](https://github.com/luminati-io/Google-Maps-Scraper?tab=readme-ov-file#customizing-data-collection-with-api-parameters) をご確認ください。

### APIパラメータでデータ収集をカスタマイズする
次の API パラメータを使用して、データ収集をカスタマイズできます:

| **Parameter**       | **Type**   | **Description**                                                                                   | **Example**                                           |
|---------------------|------------|---------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| `limit`             | `integer`  | 各入力に対して返される結果数を制限します。                                            | `limit=10`                                           |
| `include_errors`    | `boolean`   | トラブルシューティングのため、出力にエラーレポートを含めます。                                      | `include_errors=true`                                |
| `notify`            | `url`      | 収集が完了した際に通知を送信するURLです。                                  | `notify=https://notify-me.com/`                      |
| `format`            | `enum`     | データ配信の形式です。対応形式: JSON, NDJSON, JSONL, CSV。                          | `format=json`|

💡**追加の配信方法:** データは [webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook) 経由、または [API](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-api) 経由で配信することも選択できます。