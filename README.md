# SmartCoder 醫院正式服務 Colab

這個公開 repository 提供 12 家院別的 SmartCoder 正式整合 notebook。每份請求只送出 `request_id`、合成原始病歷與 `output_format=simple`，不預填 SNOMED CT 或 ICD-10 參考碼。

Notebook 會檢查完整病例整理、3 輪 NER、術語連結、SNOMED CT 驗證、results GET 一致性與 Colab CORS。只有所有檢查都完成時，才會顯示「正式流程驗收通過」。

> 僅限使用 notebook 內建的合成病例。請勿輸入真實病歷、姓名、身分證號、病歷號或其他個人資料。

## 已直接驗證

中山醫入口已於 2026-08-03 從正式 VM 直接完成 raw-note-only 全流程驗收。這本已配置可公開、可撤換的 Colab access token，可直接選「執行階段」→「全部執行」。

| 院別 | API base URL | Colab |
|---|---|---|
| 中山醫 `csh` | `https://fhircsh.itri-nlp.tw/code_api/smartcoder` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/csh_smartcoder_api.ipynb) |

## 正式入口已設定，完整流程待重新驗證

以下 notebook 已使用正式整合格式，但尚未用目前的 raw-note-only 條件重新驗收。執行時需要各院自己的 API key；repository 內不含這些非公開憑證。

| 院別／入口 | API base URL | Colab |
|---|---|---|
| 臺北榮總 `tvgh` | `https://fhircsh.itri-nlp.tw/code_api/tvgh` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/tvgh_smartcoder_api.ipynb) |
| 部立臺北醫院 `tph` | `https://fhircsh.itri-nlp.tw/code_api/tph` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/tph_smartcoder_api.ipynb) |
| 花蓮門諾 `hlm` | `https://fhirdevaz.itri-nlp.tw/hlm` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/hlm_smartcoder_api.ipynb) |
| 中國醫藥大學附設醫院 `cmmc` | `https://fhirdevaz.itri-nlp.tw/cmmc` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/cmmc_smartcoder_api.ipynb) |
| 臺中榮總 `tcvgh` | `https://fhirdevazure.itri-nlp.tw/tcvgh` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/tcvgh_smartcoder_api.ipynb) |
| 臺大 `ntuh` | `https://fhirdevazure.itri-nlp.tw/ntuh` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/ntuh_smartcoder_api.ipynb) |
| 員榮 `yuanrung` | `https://fhirdevaz.itri-nlp.tw/yuanrung` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/yuanrung_smartcoder_api.ipynb) |
| 長庚醫療體系 `cgh` | `https://fhirdevazure.itri-nlp.tw/cgh` | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/cgh_smartcoder_api.ipynb) |

## 服務目前不可用

以下 notebook 保留正式網址與完整驗收條件。服務恢復前會明確停止，不會把未完成流程標成通過。

| 院別／入口 | API base URL | 目前狀態 | Colab |
|---|---|---|---|
| 成大 `nckuh` | `https://fhircgh.itri-nlp.tw/code_api/nckuh` | 尚未完成新版切換 | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/nckuh_smartcoder_api.ipynb) |
| 高醫 `kmuh` | `https://fhircgh.itri-nlp.tw/code_api/kmuh` | 尚未完成新版切換 | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/kmuh_smartcoder_api.ipynb) |
| 馬偕醫療體系 `mmh` | `https://fhirmmh.itri-nlp.tw/code_api/smartcoder` | 服務目前未啟用 | [開啟 Colab](https://colab.research.google.com/github/dechnology/smartcoder-hospital-colab/blob/main/colab/hospitals/mmh_smartcoder_api.ipynb) |

## 驗收條件

- POST 與 GET 都回應成功，且 Colab CORS 正確。
- `polished_clinical_note` 不為空。
- `pipeline_version` 以 `|txt_ner` 結尾。
- `vote_attempts` 等於 3。
- 每筆編碼來源都只有 `TXT_NER`。
- 回應包含胸痛 SNOMED CT concept `29857009`。
- results GET 狀態為 `completed`，且編碼與 POST 回應一致。

中山醫可直接執行。其他已啟用入口可先設定 `SMARTCODER_API_KEY` 或 `API_AUTH_TOKEN`；未設定時，notebook 會安全地要求輸入。
