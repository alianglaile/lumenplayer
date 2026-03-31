# Lumen Player Video Source Configuration

[📖 中文版](README.md)

This directory contains video source subscription configuration files for Lumen Player. Each JSON file defines a set of video sources that users can import into the app to aggregate content from multiple streaming sites.

---

## 📁 File Overview

| Filename | Description | Use Case | Subscription URL |
|----------|-------------|----------|------------------|
| `sources.json` | General video sources (overseas) | Recommended, no region restrictions | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources.json` |
| `sources-cn.json` | Mainland China video sources | Some sources require China IP | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources-cn.json` |
| `sources-18.json` | Adult content sources (18+) | Adults only | `https://raw.githubusercontent.com/alianglaile/lumenplayer/main/sources-18.json` |

---

## 📋 Video Source Details

### `sources.json` — General Sources

| Name | Type | Search | Notes |
|------|------|--------|-------|
| Douban Picks | 🏷️ Theme | ❌ | Curated recommendations only, no direct playback |
| Olevod | 🔌 Plugin (LumenPlugin) | ✅ | Ad-free for overseas IPs |
| Liangzi Resources | 🔗 Direct API | ✅ | No pre-roll ads, interstitial ads |
| Ruyi Resources | 🔗 Direct API | ✅ | No pre-roll ads, interstitial ads |
| Baofeng Resources | 🔗 Direct API | ✅ | No pre-roll ads, interstitial ads |
| Movie Paradise | 🔗 Direct API | ✅ | No pre-roll ads, interstitial ads |
| 360 Resources | 🔗 Direct API | ✅ | Pre-roll ads, no interstitial ads |

### `sources-cn.json` — Mainland China Sources

| Name | Type | Search | Notes |
|------|------|--------|-------|
| Douban Picks | 🏷️ Theme | ❌ | Shared with general sources, curated recommendations |
| New Director | 🔌 Plugin (syncnextPlugin) | ✅ | **Requires China IP** |
| Modu Resources | 🔗 Direct API | ✅ | 1080P 1.5M, text pre-roll |
| Sony Resources | 🔗 Direct API | ❌ | 1080P, 1M |
| Lightning Resources | 🔗 Direct API | ✅ | 1080P, 1.5M |

### `sources-18.json` — Adult Content Sources (18+)

| Name | Type | Notes |
|------|------|-------|
| JAV Online | 🔌 Plugin (LumenPlugin) | HD 1080P |
| Lebo Resources | 🔗 Direct API | premium |
| CK | 🔗 Direct API | premium |
| jkun | 🔗 Direct API | premium |
| 155 | 🔗 Direct API | premium |
| lsb | 🔗 Direct API | premium |
| Yellow Warehouse | 🔗 Direct API | premium |
| Yutu | 🔗 Direct API | premium |
| Bishoujo Resources | 🔗 Direct API | premium |
| Yinshuiji Resources | 🔗 Direct API | premium |
| Xiangnaier Resources | 🔗 Direct API | premium |
| Baipiao Resources | 🔗 Direct API | premium |
| HuangAV Resources | 🔗 Direct API | premium |
| Million Resources | 🔗 Direct API | premium |
| 91 Madou | 🔗 Direct API | premium |
| Naixiangxiang | 🔗 Direct API | premium |
| Forest Resources | 🔗 Direct API | premium |
| Fanhao Resources | 🔗 Direct API | premium |
| Premium Resources | 🔗 Direct API | premium |
| Shark Resources | 🔗 Direct API | premium |
| Xiaoji Resources | 🔗 Direct API | premium |
| Cell Collector | 🔗 Direct API | premium |

---

## 🔍 Video Source Types

Lumen Player supports three types of video sources:

### 🔌 Plugin Sources

- API starts with `lumen://` or `syncnextPlugin://`
- Loads content via `config.json` + JavaScript scripts
- Supports more flexible website parsing capabilities

### 🔗 Direct API (MacCMS)

- API is a standard HTTP/HTTPS URL
- Directly calls MacCMS-format API endpoints
- Returns video data in XML or JSON format

### 🏷️ Theme Sources

- `type` field set to `"theme"`
- Provides curated themes and recommendation lists only
- No search or direct playback — must be used alongside other video sources

---

## 🚀 How to Use with Lumen Player

### Import Subscription Link (Recommended)

1. Host the configuration file at an accessible URL (e.g., GitHub Raw link)
2. Open Lumen Player → **Settings** → **Subscription Management**
3. Paste the subscription URL, then tap **Add**
4. The app will automatically parse and load all video sources

---

## ⚙️ Configuration Fields

Each video source entry supports the following fields:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `id` | String | ✅ | Unique identifier (UUID or custom ID) |
| `name` | String | ✅ | Display name of the video source |
| `api` | String | ✅ | API endpoint (determines source type) |
| `type` | String | ❌ | Source type, defaults to `"vod"`, can be `"theme"` |
| `search` | Boolean | ❌ | Whether search is supported, defaults to `true` |
| `top` | Boolean | ❌ | Whether to pin to top |
| `priority` | Number | ❌ | Sort priority (lower value = higher position) |
| `note` | String | ❌ | Notes (e.g., ad info, quality) |
| `cover` | String | ❌ | Cover image URL |
| `enabled` | Boolean | ❌ | Whether enabled, defaults to `true` |

---

## ⚠️ Important Notes

- Some video sources may have **regional restrictions** and require an appropriate network environment
- Source availability may change at any time — it's recommended to update subscriptions regularly
- `sources-18.json` contains adult content — please ensure compliance with local laws and regulations
- Direct API sources may include pre-roll or interstitial ads, which are noted in the remarks field
