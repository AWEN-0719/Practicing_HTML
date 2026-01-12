# 練習03  CSS Position（定位）與 Flexbox 的搭配使用
=====================================================
## 練習的目標
- CSS Position（定位）與 Flexbox 的搭配使用，透過重複的內容結構，製作出 左右交錯、圖文重疊的版面效果。
- 理解 ```position: relative``` 與 ```position: absolute``` 的實際用途
- 練習製作「重疊式」版面配置
- 使用 ```nth-of-type``` 控制左右交錯排版
- 在不改 HTML 結構的前提下，僅用 CSS 控制版型變化
- 本作品前端切版練習，不包含 JavaScript 功能。

## 使用技術（Technologies）
HTML
CSS
Flexbox
CSS Position
reset.css（清除瀏覽器預設樣式）
Font Awesome（圖示字型）

## HTML 結構設計說明
每一組內容皆包在一個 ```<section> ```中，拆成三個主要區塊：
### A 區：標題區（```.title```）
- 區塊標題
- 直書數字（01～05）
- 疊在標題上的文字說明區塊

### B 區：圖片區（```.main-video```）
- 主要圖片
- 按鈕圖片
- 使用 Flexbox 做橫向排列

### C 區：文字說明區（```.main-text```）
- 功能說明標語
- 多組小標題與段落
- 使用 margin 與 z-index 製作重疊效果

## CSS 練習筆記
### ```position: relative``` 與 ```position: absolute```
```css=
.title {
    position: relative;
}

.title .title-text {
    position: absolute;
}
```
- ```position: relative``` 是 定位的參考點
- ```position: absolute``` 會以最近的 relative 父層為基準
- 用來做疊在圖片或色塊上的文字
` 不影響其他元素排版的裝飾區塊
練習中，黑色的 ```.title-text``` 就是疊在紅色標題區上

### 使用 ```nth-of-type``` 製作左右交錯版型
```css=
section:nth-of-type(even) .title {
    margin-left: auto;
}
```
```css=
section:nth-of-type(even) .main-video {
    flex-direction: row-reverse;
}
```
- 所有 section 的 HTML 結構完全相同，偶數區塊只透過 CSS 改變排列方向
- 目的是為了避免複製兩套 HTML 結構

### Flexbox 應用於圖片區排列
```css=
.main-video {
    display: flex;
    align-items: center;
}
```

Flexbox 在這裡用來控制圖片與按鈕的左右排列，快速調整對齊方式
搭配 ```row-reverse``` 製作交錯效果

### 使用負 margin 製作視覺重疊
```css=
.main-video .show-video {
    margin-right: -50px;
}

.main-text {
    margin-top: -2em;
    position: relative;
    z-index: 2;
}
```
負 margin 可以讓元素「往外推」，搭配 ```z-index``` 可控制前後層次

### 直書文字（writing-mode）
```css=
.title span {
    writing-mode: vertical-lr;
}
```
製作直向數字標示（01、02、03）來提升視覺辨識度
不需圖片即可完成排版效果

### 使用 ```::before``` 客製清單符號
```css=
.main-text p:before {
    content: '●';
    color: red;
    transform: scale(.7);
}
```
不一定要使用 <ul><li>，CSS 偽元素可製作裝飾符號
視覺與結構可分離設計

### 練習心得
- Position 是「有目的地疊」，複雜版型可以靠規律結構 + CSS 條件控制
- Position 是「輔助版型設計的工具」，不是用來硬撐排版的方式
- 使用這個方式切版邏輯需要清楚
