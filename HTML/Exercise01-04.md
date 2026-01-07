# 小結 練習01 ~ 04 
===============================
本階段練習只要是為 HTML / CSS 切版的訓練，從基礎結構 → 表格 → Position → CSS Grid，目的是建立 「版面思維」與「排版能力」

## 練習概要
|練習|範圍|技術|學習心得|
|練習01|HTML基礎結構|HTML|語意結構與標籤用途|
|練習02|表格練習|table/colspan/rowspan|格線思維|
|練習03|Position版型|position/flexbox|重疊與交錯|
|練習04|Grid版型|CSS/Grid|版面配置|

### 練習01
- 認識 HTML 文件的基本結構，HTML 負責內容與語意
- 學習標籤使用習慣，標籤不是為了好看，而是為了「結構清楚」
- 區分「結構」與「樣式」，CSS 排版都建立在 HTML 結構之上

### 練習02
- 使用表格方式來訓練版面思維
- 用格子思考版面，練習合併欄位與列，訓練橫向與縱向對齊的概念，
- 運用 ```<table>``` 製作複雜表格，``` rowspan/colspan/<thead>/<tbody>/<caption> ```

### 練習 03
- 使用 position 製作重疊效果，練習左右交錯版型並結合 Flexbox 輔助排版
- Position 疊加元素時，要先想「誰是定位基準」
- 相同 HTML 結構，可只用 CSS 製作多種版型
- ``` position: relative / absolute / z-index / nth-of-type(even) / flex-direction: row-reverse ```
- 開始接觸有版型的設計頁面，但過程中一直偏向手動控制位置，還不夠熟練

### 練習 04
- 使用 Grid 建立複雜版面取代大量 Position 計算
- 學習清楚的版面配置邏輯，HTML 可以保持乾淨一致，複雜視覺效果交給 CSS 處理
- ``` display: grid / grid-template-columns / rows / grid-column / grid-row / nth-child(even) /Grid 疊層與裝飾元素（::after）```
- Grid + Flex 的組合，學習從「硬排版」進化到「思維排版」

## 學到的觀念
- 當單行排列時，用``` Flexbox```
- 小區塊對齊，用``` Flexbox```
- 表格是資料 ，用``` Table```
- 裝飾性重疊，用``` Position```
- 複雜版面，用``` Grid```
