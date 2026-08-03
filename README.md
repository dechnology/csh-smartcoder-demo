# 中山醫學大學附設醫院 SmartCoder 公開展示

[![在 Colab 開啟](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/dechnology/csh-smartcoder-demo/blob/main/csh_smartcoder_api_demo.ipynb)

點上方按鈕開啟 Colab，再選「執行階段」→「全部執行」即可完成展示；不需輸入 API key，也不需設定環境變數。

> 請只使用 Notebook 內建的合成案例。請勿輸入真實病歷、姓名、身分證號、病歷號或其他個人資料。

## 展示 API

- Base URL：`https://fhircsh.itri-nlp.tw/code_api/smartcoder`
- 送出編碼：`POST /api/v1/snomed/coding`
- 查詢結果：`GET /api/v1/snomed/results/{request_id}`
- 認證：Notebook 已內建可更換的公開展示用 `X-API-Key`，直接呼叫中山醫 SmartCoder 正式服務

這個公開 key 是正式服務的可撤換展示憑證，不是內部維運密鑰；展示結束後可直接輪替或停用。

Notebook 只送出原始合成病歷，不預填 SNOMED 或 ICD。正式服務會依序執行病歷整理、3 輪實體辨識、術語連結與 SNOMED 驗證。

## 驗收條件

Notebook 會自動確認：

- `POST` 成功，且有整理後病歷與 SNOMED 編碼結果
- `pipeline_version` 為完整 `txt_ner` 流程，NER 執行 3 輪
- 所有編碼來源皆為 `TXT_NER`，不接受預填碼或 fallback
- 使用同一個 `request_id` 執行 `GET`，且結果與 `POST` 一致
- Colab CORS 回應正確
