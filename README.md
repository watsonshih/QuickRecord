# QuickRecord - 快速簽到退系統

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![GitHub Pages](https://img.shields.io/badge/demo-online-green.svg)](https://watsonshih.github.io/QuickRecord/)

> 透過掃描 QR Code，讓您的活動簽到簽退更快速！
> 
> Streamline your event check-in/out process with QR Code scanning!

## 專案簡介

QuickRecord 是一個簡單易用的活動簽到退系統，專為減輕活動舉辦者負擔而設計。無需安裝任何應用程式，直接使用網頁瀏覽器即可操作，大幅提升簽到退的效率，適合研討會、課程、會議、社團活動等場合使用。

### 主要特色

- **免安裝** - 純網頁應用，開啟即用
- **QR Code 掃描** - 快速識別參與者身份
- **名單管理** - 支援 CSV 匯入/匯出
- **雲端同步** - 多裝置即時共用資料（選用）
- **雙語介面** - 支援繁體中文與英文
- **介面友善** - 深色主題，易於操作
- **隱私保護** - 本地處理資料，可選擇性同步
- **匯出紀錄** - 自動產生完整簽到退 CSV 檔案

## 線上使用

- **主系統**：[https://watsonshih.github.io/QuickRecord/](https://watsonshih.github.io/QuickRecord/)
- **參與者頁面**：[https://watsonshih.github.io/QuickRecord/user.html](https://watsonshih.github.io/QuickRecord/user.html)
- **郵件產生器**：[https://watsonshih.github.io/QuickRecord/generator.html](https://watsonshih.github.io/QuickRecord/generator.html)
- **使用說明**：[https://watsonshih.github.io/QuickRecord/README.html](https://watsonshih.github.io/QuickRecord/README.html)

## 快速上手

### 對於活動主辦方

1. **開啟系統**  
   前往 [QuickRecord 主頁](https://watsonshih.github.io/QuickRecord/)

2. **準備名單**（選用）  
   - 下載 [CSV 模板](https://watsonshih.github.io/QuickRecord/template.csv)
   - 填寫參與者資料（需包含 Name 和 ID 欄位）
   - 上傳 CSV 檔案或選擇直接開始

3. **設定活動資訊**  
   - 輸入活動名稱（必填）
   - 調整顯示設定
   - 選擇是否啟用雲端同步

4. **開始簽到**  
   - 掃描參與者的 QR Code
   - 查看即時簽到狀態
   - 完成後進入簽退階段

5. **下載紀錄**  
   - 簽退完成後下載 CSV 檔案
   - 檔案包含完整簽到退時間記錄

### 對於參與者

1. **產生 QR Code**  
   前往 [參與者頁面](https://watsonshih.github.io/QuickRecord/user.html)

2. **輸入資訊**  
   - 輸入姓名和 ID（需與主辦方名單一致）
   - 系統自動產生個人 QR Code

3. **簽到/簽退**  
   - 向工作人員展示 QR Code
   - 確保螢幕亮度充足且 QR Code 清晰

## 系統需求

- 現代網頁瀏覽器（Chrome、Firefox、Safari、Edge）
- 裝置需配備相機（用於掃描 QR Code）
- 網路連線（僅在使用雲端同步功能時需要）

## 技術架構

### 前端技術

- **HTML5** - 網頁結構
- **Tailwind CSS 3.4.16** - 介面樣式
- **JavaScript** - 互動邏輯
- **jsQR** - QR Code 解碼
- **PapaParse** - CSV 檔案解析
- **qrcode.js** - QR Code 產生

### 專案結構

```
QuickRecord/
├── index.html              # 主系統頁面
├── user.html              # 參與者 QR Code 產生頁面
├── generator.html         # 郵件程式產生器
├── README.html            # 使用說明頁面
├── template.csv           # CSV 模板
├── js/                    # JavaScript 函式庫
│   ├── jsQR.min.js
│   ├── papaparse.min.js
│   ├── qrcode.min.js
│   └── tailwindcss.3.4.16.js
├── i18n/                  # 國際化語言檔
│   ├── langs.js
│   └── langs_readme.js
├── pic/                   # 圖片資源
│   ├── icon.png
│   └── banner.png
├── poster/                # 宣傳海報
│   ├── user_A4.pdf
│   └── user_screen.pdf
└── bgm/                   # 音效檔案
```

## CSV 格式說明

### 參與者名單格式

```csv
Name,ID,Note
王小明,A12345678,第一組
李小華,B87654321,第二組
```

### 必要欄位

- **Name** - 參與者姓名（必填，可重複）
- **ID** - 唯一識別碼（必填，不可重複，區分大小寫）
- **Note** - 備註資訊（選填）

### 匯出紀錄格式

```csv
Name,ID,Note,InCSV,CheckInTime,CheckOutTime
王小明,A12345678,第一組,Yes,2025-05-19 09:30:15,2025-05-19 12:45:30
```

## 輔助工具

### 1. 參與者 QR Code 產生頁面

讓參與者自行產生簽到退用的 QR Code。

**URL 參數預填功能**：
```
https://watsonshih.github.io/QuickRecord/user.html?name=王小明&id=A12345678
```

### 2. 通行碼郵件寄送程式產生器

產生 Google Apps Script 程式碼，透過 Gmail 批次寄送個人化 QR Code 連結。

**使用步驟**：
1. 準備 Google Sheet（需含 Name、ID、Email、Sent 欄位）
2. 在產生器填寫活動資訊
3. 複製產生的程式碼
3. 貼至 Google Apps Script 並執行

## 使用技巧

### 成功秘訣

- 確保網路連線穩定（使用雲端同步時）
- 保持掃描環境光線充足
- 提醒參與者調亮螢幕並保持 QR Code 清晰
- 確保名單資料與 QR Code 資訊一致
- 活動前先進行測試
- 活動結束後立即下載紀錄檔備份

### 常見問題

**Q: 可以離線使用嗎？**  
A: 可以。除非啟用雲端同步功能，否則所有資料都在本地處理。

**Q: 雲端同步的資料會保存多久？**  
A: 雲端資料僅為暫存，可能隨時被清除，請務必下載紀錄檔備份。

**Q: 參與者的 QR Code 需要事先準備嗎？**  
A: 不一定。可以讓參與者現場產生，或事先透過郵件寄送連結。

**Q: ID 欄位可以使用什麼格式？**  
A: 任何文字或數字組合，但必須唯一且區分大小寫。

## 貢獻

歡迎提交 Issue 或 Pull Request！

## 授權條款

本專案採用 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) 授權。

### 免責聲明

QuickRecord 以「現狀」提供，不提供任何明示或暗示的保證。使用者需自行承擔使用風險。服務建立者不對因使用或無法使用本服務而導致的任何損害負責，包括但不限於資料遺失、紀錄錯誤等。

使用者有責任：
- 確保輸入資料的準確性
- 在活動結束後立即下載並備份紀錄檔
- 妥善保管參與者個人資料

## 作者

**Watson Shih**

- Website: [https://watsonshih.github.io/](https://watsonshih.github.io/)
- GitHub: [@watsonshih](https://github.com/watsonshih)

## 致謝

感謝以下開源專案：

- [jsQR](https://github.com/cozmo/jsQR) - QR Code 解碼函式庫
- [PapaParse](https://www.papaparse.com/) - CSV 解析器
- [qrcode.js](https://davidshimjs.github.io/qrcodejs/) - QR Code 產生器
- [Tailwind CSS](https://tailwindcss.com/) - CSS 框架

---

如果這個專案對您有幫助，歡迎給個 Star！

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Boba%20Tea-支持作者-yellow.svg)](https://www.buymeacoffee.com/watsonshih)
