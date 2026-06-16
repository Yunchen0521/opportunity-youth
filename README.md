# opportunity-youth

「青機會（Opportunity Map Taiwan）」iOS App 的機會資料來源。

整合政府、基金會與企業提供的台灣青年機會（補助、競賽、實習、創業、培力、海外交流、獎學金、圓夢計畫等）。所有資訊以各官方網站最新公告為準，App 僅整理與導流。

## 檔案

- `opportunities.json` — App 讀取的機會資料（App 會抓 `main` 分支的這個檔）。
- `sources.md` — 已查證的來源清單與策展紀錄。

## App 抓取網址

```
https://raw.githubusercontent.com/Yunchen0521/opportunity-youth/main/opportunities.json
```

更新機會時，改 `opportunities.json` 後 commit/push，App 下拉刷新即可取得最新資料，毋需改 App、毋需送審。

## 資料格式

```jsonc
{
  "version": "0.2.0",
  "updatedAt": "YYYY-MM-DD",
  "opportunities": [
    {
      "id": "唯一穩定字串",
      "title": "計畫名稱",
      "category": "subsidy|competition|internship|startup|training|exchange|scholarship|grant|venue|platform",
      "organizer": "主辦單位",
      "sourceType": "government|foundation|company",
      "summary": "三句話摘要",
      "description": "計畫內容",
      "eligibility": { "minAge": null, "maxAge": null, "identities": ["學生"], "regions": ["全國"] },
      "amount": "金額或 null",
      "deadline": "YYYY-MM-DD 或 null",
      "applyStartDate": "YYYY-MM-DD 或 null",
      "website": "官方連結",
      "location": null
    }
  ]
}
```

座標 `location` 僅用於有單一固定據點者（`venue` 或單址活動）；多點/全國/海外的機會 `location` 為 `null`。
