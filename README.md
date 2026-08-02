# 中山醫學大學附設醫院 SmartCoder 公開展示

[![在 Colab 開啟](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dechnology/csh-smartcoder-demo/blob/main/csh_smartcoder_api_demo.ipynb)

點上方按鈕開啟 Colab，再選「執行階段」→「全部執行」即可完成展示；不需輸入 API key，也不需設定環境變數。

> 請只使用 Notebook 內建的合成案例。請勿輸入真實病歷、姓名、身分證號、病歷號或其他個人資料。

## 展示 API

- Base URL：`https://fhircsh.itri-nlp.tw/code_api/smartcoder-demo`
- 送出編碼：`POST /api/v1/snomed/coding`
- 查詢結果：`GET /api/v1/snomed/results/{request_id}`
- 認證：Notebook 已內建公開展示用 `X-API-Key`

這個 key 不是正式環境憑證。展示服務與院內服務分離，有獨立記錄與請求限流；必要時可更換。若多人同時操作而收到 `429`，請稍候再執行。

## 驗收條件

Notebook 會自動確認：

- `POST` 成功且編碼結果不為空
- 使用同一個 `request_id` 執行 `GET` 成功
- Colab CORS 回應正確

