# Tsuduri 官方網站 - 技術規格文件

## 📋 專案概述

**專案名稱**: Tsuduri 品牌官方網站  
**版本**: 1.0  
**更新日期**: 2026-06-23  
**用途**: 展示品牌形象、產品集合、線上購物入口

---

## 📁 專案結構

```
Website/
├── index.html                          # 主要頁面
├── README.md                           # 本規格文件
├── Agent.md                            # AI代理配置
└── bootstrap-5.0.2-dist/              # Bootstrap框架資源
    ├── css/                            # 樣式表資料夾
    │   ├── bootstrap.min.css           # Bootstrap核心樣式（最小化）
    │   ├── bootstrap.css               # Bootstrap核心樣式（完整版）
    │   ├── bootstrap-grid.css          # Grid系統
    │   ├── bootstrap-reboot.css        # CSS重置
    │   ├── bootstrap-utilities.css     # Bootstrap工具類
    │   ├── custom.css                  # 自訂全局樣式
    │   └── header.css                  # 標頭獨立樣式 ⭐ 新增
    ├── js/                             # JavaScript資源
    │   ├── bootstrap.bundle.min.js     # Bootstrap JS（含Popper.js）
    │   ├── bootstrap.bundle.js         # Bootstrap JS完整版
    │   └── bootstrap.min.js            # Bootstrap核心JS
    └── image/                          # 圖片資源
        ├── logo.png                    # 品牌logo
        ├── banner.png                  # 主視覺橫幅
        ├── 品牌標語圖.jpg               # 品牌故事配圖
        ├── product/                    # 產品圖片資料夾
        └── rotate/                     # 輪播圖片資料夾
```

---

## 🎨 CSS 檔案架構與維護

### 檔案說明

| 檔案名 | 用途 | 載入順序 | 維護責任 |
|--------|------|---------|---------|
| `bootstrap.min.css` | Bootstrap框架核心樣式 | 1st | 第三方 |
| `header.css` | 標頭區域樣式（獨立維護） | 2nd | 頁面設計師 |
| `custom.css` | 其他全局自訂樣式 | 3rd | 頁面設計師 |

### CSS 載入順序（在 index.html）

```html
<link href="bootstrap-5.0.2-dist/css/bootstrap.min.css" rel="stylesheet">
<link href="bootstrap-5.0.2-dist/css/header.css" rel="stylesheet">
<link href="bootstrap-5.0.2-dist/css/custom.css" rel="stylesheet">
```

**重點**: header.css 必須在 custom.css 之前載入，避免樣式優先級衝突。

### 各CSS檔案維護範圍

#### **header.css** ⭐ 推薦優先更新
- **包含元素**: 
  - `.site-header` - 標頭容器
  - `.brand-logo` - 品牌logo區域
  - `.signin-btn` - 登入按鈕
- **特點**: 獨立模組化，便於新頁面引用
- **行動響應**: 含767.98px以下斷點

**使用方式** - 在其他頁面引用：
```html
<link href="bootstrap-5.0.2-dist/css/header.css" rel="stylesheet">
```

#### **custom.css**
- **包含內容**:
  - CSS變數定義（:root）
  - body基礎樣式
  - 輪播、導覽、品牌故事、商品卡片、頁尾等樣式
  - 主要的響應式設計
- **變數定義**:
  ```css
  --brand-green: #075234    /* 品牌深綠 */
  --brand-soft: #77c4ad     /* 品牌淺綠 */
  --brand-ink: #2f6b58      /* 品牌墨綠 */
  --brand-paper: #fbfbf8    /* 品牌米白 */
  ```

---

## 🛠️ 技術堆棧

| 技術 | 版本 | 用途 |
|------|------|------|
| HTML | 5 | 標記語言 |
| CSS | 3 | 樣式表 |
| Bootstrap | 5.0.2 | CSS框架 |
| JavaScript | ES6+ | 互動功能（Carousel） |
| 字型 | Georgia, Noto Serif TC | 品牌字體 |

---

## 📱 響應式設計斷點

- **行動版**: ≤ 767.98px
- **平板版**: 768px - 1199.98px
- **桌面版**: ≥ 1200px

主要調整在CSS中使用 `@media (max-width: 767.98px)` 實現。

---

## 🎯 主要頁面元素

### 1. 標頭 (Header)
- 品牌logo居中顯示
- 登入按鈕右上角浮動
- 響應式設計

### 2. 主視覺輪播 (Hero Carousel)
- 5張輪播圖片
- 支援指標按鈕導航
- 手機版高度自動調整

### 3. 導覽選單 (Main Menu)
- 4個主要選單項目（About、Collection、Online Shop、Account）
- 綠色背景品牌色彩
- 懸停互動效果

### 4. 品牌故事區 (Brand Story)
- 左側圖片 + 右側文字
- 行動版改為上下堆疊
- 季節標籤（2026 SS）

### 5. 產品集合 (Collection)
- 6件產品卡片
- 3欄格線佈局（桌面版）
- 回應式自動調整

### 6. 線上購物按鈕 (Shop Area)
- 居中CTA按鈕

### 7. 頁尾 (Footer)
- 品牌資訊、社群連結、公司資訊

---

## 🔧 維護指南

### 修改標頭樣式

1. 編輯 `bootstrap-5.0.2-dist/css/header.css`
2. 更改對象:
   - 標頭背景色/高度 → 修改 `.site-header`
   - Logo尺寸 → 修改 `.brand-logo img`
   - 按鈕位置/樣式 → 修改 `.signin-btn`

### 修改品牌色彩

編輯 `bootstrap-5.0.2-dist/css/custom.css` 的 `:root` 區塊：

```css
:root {
  --brand-green: #075234;    /* 修改這裡 */
  --brand-soft: #77c4ad;
  --brand-ink: #2f6b58;
  --brand-paper: #fbfbf8;
}
```

### 新增新頁面

1. 複製 `index.html` 為新頁面（如 `product-detail.html`）
2. 保留CSS引用:
   ```html
   <link href="bootstrap-5.0.2-dist/css/bootstrap.min.css" rel="stylesheet">
   <link href="bootstrap-5.0.2-dist/css/header.css" rel="stylesheet">
   <link href="bootstrap-5.0.2-dist/css/custom.css" rel="stylesheet">
   ```
3. 修改頁面內容，保持標頭結構一致

### 圖片管理

- **Logo**: `bootstrap-5.0.2-dist/image/logo.png`
- **橫幅**: `bootstrap-5.0.2-dist/image/banner.png`
- **品牌圖**: `bootstrap-5.0.2-dist/image/品牌標語圖.jpg`
- **產品圖**: `bootstrap-5.0.2-dist/image/product/` ← 新產品放這
- **輪播圖**: `bootstrap-5.0.2-dist/image/rotate/` ← 新輪播圖放這

---

## 🚀 未來擴展計劃

### 優先順序

| 優先級 | 項目 | 建議 |
|--------|------|------|
| 高 | 後端服務API | 完成購物、會員系統連結 |
| 高 | 產品詳細頁 | 創建 `product-detail.html` |
| 中 | 購物車功能 | 導入Cart.js或自製模組 |
| 中 | 會員登入 | 串接身份驗證系統 |
| 中 | 搜尋功能 | 全文搜尋產品 |
| 低 | 多語言支援 | 簡體/英文版本 |
| 低 | 黑暗模式 | 新增深色主題CSS |

### 新頁面CSS建議

依照 `header.css` 的模式，為大型功能區域建立獨立CSS：

- `footer.css` - 頁尾樣式
- `carousel.css` - 輪播樣式
- `product-card.css` - 產品卡片樣式
- `navigation.css` - 導覽選單樣式

---

## 📞 交接注意事項

### 關鍵檔案清單

- ✅ HTML結構 - `index.html`
- ✅ 標頭樣式 - `bootstrap-5.0.2-dist/css/header.css`
- ✅ 全局樣式 - `bootstrap-5.0.2-dist/css/custom.css`
- ✅ 品牌資源 - `bootstrap-5.0.2-dist/image/`

### 常見問題解決

**Q: 修改標頭後排版亂掉？**  
A: 檢查是否更改了 `.site-header` 的 `min-height`，可能影響下方內容。

**Q: 顏色不符品牌色?**  
A: 修改 `custom.css` 的 `:root` 變數，而非硬編CSS值。

**Q: 新增產品卡片不對齊？**  
A: 確保使用Bootstrap Grid系統（`col-lg-4` 等class）。

**Q: 行動版排版不適配？**  
A: 檢查所有 `@media (max-width: 767.98px)` 規則是否已更新。

---

## 📝 版本控制

| 版本 | 日期 | 變更說明 |
|------|------|---------|
| 1.0 | 2026-06-23 | 初版上線，標頭CSS獨立模組化 |

---

## 🔗 相關資源

- [Bootstrap 5.0.2 文檔](https://getbootstrap.com/docs/5.0/)
- [Google Fonts - Noto Serif TC](https://fonts.google.com/noto/specimen/Noto+Serif+TC)
- 設計稿位置: _(待確認本地路徑)_

---

**最後更新**: 2026-06-23  
**維護者**: _(待填寫)_
