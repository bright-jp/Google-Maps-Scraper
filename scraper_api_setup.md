## Google Maps Scraper API のセットアップ

以下の手順に従って、Google Maps Scraper API をセットアップします。

1. **Bright Data アカウントにログインします。** **Web Scraper API** タブをクリックします。

2. 検索バーに **Map** と入力し、**Google Maps Reviews** を選択します。

   <img width="650" alt="bright-data-google-maps-scraper-api-search" src="https://github.com/user-attachments/assets/c4fd4d7c-fb9e-4d00-ba48-4cceb13475ee">

3. **Start setting an API call** をクリックして、API の設定を開始します。

   <img width="650" alt="bright-data-google-maps-scraper-api-setting-api-call" src="https://github.com/user-attachments/assets/e6dafe83-5a26-4bc1-b6e7-744c055a8e93">

4. **Get API Token** をクリックして、一意の API token を生成します。

   <img width="650" alt="bright-data-google-maps-scraper-api-get-api-token" src="https://github.com/user-attachments/assets/01313a95-b494-4222-98fc-80745d18f3f8">

5. **Refresh Token** をクリックして、新しく作成した API token を表示します。

   <img width="650" alt="bright-data-google-maps-scraper-api-refresh-token" src="https://github.com/user-attachments/assets/a680c95d-9302-4b3d-a839-09325664525b">

6. API token を安全に保存します。API 呼び出しを行うために必要です。

   <img width="650" alt="bright-data-google-maps-scraper-api-token" src="https://github.com/user-attachments/assets/db459bcb-e21b-49cd-85e4-d34801458bc2">

7. **Dataset ID** を確認するには、**Management APIs** タブに移動します。

   <img width="650" alt="bright-data-google-maps-scraper-api-dataset-id" src="https://github.com/user-attachments/assets/15143817-d83e-4273-a015-9d85b9c86b05">

8. **Data Collection APIs** タブで、Add inputs オプションを使用して、`URL` や `days_limit` などの複数の input を追加します。結果数の上限やエラーレポートを含めるかどうかなどのパラメータも調整できます。

   <img width="650" alt="bright-data-google-maps-scraper-api-add-inputs" src="https://github.com/user-attachments/assets/13fa3994-2cfd-45ef-84d9-78cf828eebc0">

9. パラメータを調整すると、右側に CURL コマンドが生成されます。このコマンドを使用して [Trigger Data Collection API](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/trigger-a-collection#request) を直接実行するか、コード内の [`_trigger_collection`](https://github.com/triposat/google-maps/blob/main/api-scraper/scraper.py) 関数に [これらのパラメータを渡す](https://github.com/triposat/google-maps?tab=readme-ov-file#customizing-data-collection-with-api-parameters) ことができます。