# Lumen Player 視頻源配置

[📖 English Version](README_EN.md)

本目錄包含 Lumen Player 的視頻源訂閱配置檔案。每個 JSON 檔案定義一組視頻源，使用者可在應用程式中匯入以聚合多個影視站點的內容。

---

## 📁 檔案一覽

| 檔案名稱 | 說明 | 適用場景 | 訂閱 URL |
|----------|------|---------|----------|
| `sources.json` | 通用視頻源（海外適用） | 推薦，無地區限制 | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources.json` |
| `sources-cn.json` | 中國大陸視頻源 | 部分源需要大陸 IP | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources-cn.json` |
| `sources-18.json` | 成人內容視頻源（18+） | 僅限成人使用者 | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources-18.json` |

---

## 📋 各檔案視頻源詳情

### `sources.json` — 通用視頻源

| 名稱 | 類型 | 搜尋 | 備註 |
|------|------|------|------|
| 豆瓣精選 | 🏷️ 主題源（theme） | ❌ | 僅包含精選主題推薦，不提供直接播放 |
| 新歐樂影院 | 🔌 插件源（LumenPlugin） | ✅ | 海外 IP 無廣告 |
| 量子資源 | 🔗 直連 API | ✅ | 無貼片，插入式廣告 |
| 如意资源 | 🔗 直連 API | ✅ | 無貼片，插入式廣告 |
| 暴风资源 | 🔗 直連 API | ✅ | 無貼片，插入式廣告 |
| 电影天堂 | 🔗 直連 API | ✅ | 無貼片，插入式廣告 |
| 360资源 | 🔗 直連 API | ✅ | 貼片廣告，無插入式廣告 |

### `sources-cn.json` — 中國大陸視頻源

| 名稱 | 類型 | 搜尋 | 備註 |
|------|------|------|------|
| 豆瓣精選 | 🏷️ 主題源（theme） | ❌ | 與通用源共用，精選主題推薦 |
| 新廠長 | 🔌 插件源（syncnextPlugin） | ✅ | **要求大陸 IP** |
| 魔都资源 | 🔗 直連 API | ✅ | 1080P 1.5M，文字貼片 |
| 索尼资源网 | 🔗 直連 API | ❌ | 1080P，1M |
| 闪电资源 | 🔗 直連 API | ✅ | 1080P，1.5M |

### `sources-18.json` — 成人內容視頻源（18+）

| 名稱 | 類型 | 備註 |
|------|------|------|
| JAV在线 | 🔌 插件源（LumenPlugin） | 高清 1080P |
| 乐播资源 | 🔗 直連 API | premium |
| CK | 🔗 直連 API | premium |
| jkun | 🔗 直連 API | premium |
| 155 | 🔗 直連 API | premium |
| lsb | 🔗 直連 API | premium |
| 黄色仓库 | 🔗 直連 API | premium |
| 玉兔 | 🔗 直連 API | premium |
| 美少女资源站 | 🔗 直連 API | premium |
| 淫水机资源站 | 🔗 直連 API | premium |
| 香奶儿资源站 | 🔗 直連 API | premium |
| 白嫖资源站 | 🔗 直連 API | premium |
| 黄AV资源站 | 🔗 直連 API | premium |
| 百万资源 | 🔗 直連 API | premium |
| 91麻豆 | 🔗 直連 API | premium |
| 奶香香 | 🔗 直連 API | premium |
| 森林资源 | 🔗 直連 API | premium |
| 番号资源 | 🔗 直連 API | premium |
| 精品资源 | 🔗 直連 API | premium |
| 鲨鱼资源 | 🔗 直連 API | premium |
| 小鸡资源 | 🔗 直連 API | premium |
| 细胞采集 | 🔗 直連 API | premium |

---

## 🔍 視頻源類型說明

Lumen Player 支援三種視頻源類型：

### 🔌 插件源

- API 以 `lumen://` 或 `syncnextPlugin://` 開頭
- 透過 `config.json` + JavaScript 腳本載入內容
- 支援更靈活的網站解析能力

### 🔗 直連 API（MacCMS）

- API 為標準 HTTP/HTTPS URL
- 直接呼叫 MacCMS 格式的 API 介面
- 回傳 XML 或 JSON 格式的影片資料

### 🏷️ 主題源（theme）

- `type` 欄位設為 `"theme"`
- 僅提供精選主題與推薦列表
- 不提供搜尋或直接播放功能，需搭配其他視頻源使用

---

## 🚀 如何在 Lumen Player 中使用

### 匯入訂閱連結（推薦）

1. 將配置檔案託管到可存取的 URL（例如 GitHub Raw 連結）
2. 開啟 Lumen Player → **設定** → **訂閱管理**
3. 貼上訂閱 URL，點擊 **新增**
4. 應用程式會自動解析並載入所有視頻源

---

## ⚙️ 配置欄位說明

每個視頻源條目支援以下欄位：

| 欄位 | 類型 | 必填 | 說明 |
|------|------|------|------|
| `id` | String | ✅ | 唯一識別碼（UUID 或自訂 ID） |
| `name` | String | ✅ | 視頻源顯示名稱 |
| `api` | String | ✅ | API 端點（決定源類型） |
| `type` | String | ❌ | 源類型，預設為 `"vod"`，可設為 `"theme"` |
| `search` | Boolean | ❌ | 是否支援搜尋，預設 `true` |
| `top` | Boolean | ❌ | 是否置頂顯示 |
| `priority` | Number | ❌ | 排序優先級（數值越小越靠前） |
| `note` | String | ❌ | 備註說明（如廣告資訊、畫質等） |
| `cover` | String | ❌ | 封面圖片 URL |
| `enabled` | Boolean | ❌ | 是否啟用，預設 `true` |

---

## ⚠️ 注意事項

- 部分視頻源可能有**地區限制**，需配合相應的網路環境使用
- 視頻源的可用性可能隨時變動，建議定期更新訂閱
- `sources-18.json` 包含成人內容，請確保符合當地法律法規
- 直連 API 源可能包含貼片或插入式廣告，備註欄位中會標明廣告類型
