# HTML + CSS Grid 學習筆記

## 練習的目標
熟悉 CSS Grid 的實際應用方式，利用 Grid 製作 高度自由、可重疊、可左右交錯的版面配置
- 建立 Grid 容器與 Grid item 的概念
- 使用「大量欄位 + 精細單位」進行精準排版
- 理解 ```grid-column```、```grid-row``` 的實際作用
- 使用 ```nth-child(even)``` 製作左右對稱交錯版型
- 體會 Grid 與 Flexbox 的差異與適用情境

## 整體結構說明（HTML 與 CSS 分工）
前幾次練習都沒把CSS與HTML拆開，本次 HTML 的角色只負責結構與語意
- 每一組 ```.merit``` 結構完全一致
- 不寫任何「位置相關」資訊

CSS Grid 的角色，負責所有版面位置與視覺設計與控制
- 元素擺放位置
- 重疊層級
- 左右交錯

學習 Grid 的使用場景

## Grid 容器設定
### ```.merit``` 作為 Grid Container
```css=
.merit{
    display: grid;
    grid-template-columns: repeat(192, 5px);
    grid-template-rows: repeat(570, 1px) 1fr;
}
```
- 使用大量欄位（192 欄) ，目的是把版面切成細小刻度，方便精準對齊
- 每一欄 5px，整體寬度為 960px
目的是預設需要精細控制切版時的練習

## 主要 Grid Item 位置說明
### 資訊區 ```.info```
```css=
.info{
    grid-column: 1 / 72;
    grid-row: 1 / span 345;
    z-index: 2;
}
```
- 位於左側疊在圖片與背景之上
- 使用 z-index 控制層級
Grid 允許元素自由重疊，不影響其他項目

### 圖片區 ```.show```
```css=
.show{
    grid-column: 37 / span 139;
    grid-row: 141 / span 430;
}
```
圖片橫跨多欄與 .info 有交疊，形成「圖文交錯」視覺效果

### 圖示按鈕 ```.show-icon```
```css=
.show-icon{
    grid-column: 166 / span 11;
    grid-row: 350 / span 48;
}
```
練習小尺寸元件精準定位在圖片角落，適合使用 Grid 放這類裝飾元素

### 說明清單 ```.modify```
```css=
.modify{
    grid-row: span 20 / -1;
    background-color: #eeeeee;
    z-index: 2;
}
```
固定在版面下方，依不同 ```.merit ```類型微調 ```column``` 起始位置
結果顯示 Grid 可以單獨客製單一元素位置

## 使用 ```::after``` 製作背景色塊（運用Grid 疊層）
```css=
.merit::after{
    content: '';
    background-color: #f3f3f3;
    grid-column: span 87 / -1;
    grid-row: 55 / span 285;
}
```
- Grid 不只放內容，也能放「裝飾用區塊」
- ```::after``` 也是 Grid item，可用來製作背景色塊、視覺分區

## 左右交錯版型的關鍵技巧
### 偶數區塊反轉位置
```css=
.merit:nth-child(even) .info{
    grid-column: -72 / -1;
}
```
```css=
.merit:nth-child(even) .show{
    grid-column: 2 / -53;
}
```
HTML 結構完全相同，只透過 CSS 改變 Grid 擺放位置，大幅提升可維護性

## Grid 與 Flexbox 的搭配使用
練習的構想是
- 使用 Grid	做整體版面配置、重疊、定位
- 使用 Flexbox 做標題區內部排列（```.titleArea```）
```css=
.info>.titleArea{
    display: flex;
    justify-content: space-between;
}
```
Grid 管「大方向」，Flex 管「小排列」

## 練習心得
- 當版型開始變複雜時，Grid 會比 Flex 更清楚、更好維護。
- 複雜視覺設計其實可以 HTML 很乾淨，把位置、層級、對齊都應交給 CSS 處理
