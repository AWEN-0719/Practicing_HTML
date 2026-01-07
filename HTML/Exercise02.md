# SHOPLINE 官網樣式復刻（練習紀錄）
##################################
## 練習目的 - 拆結構
以 SHOPLINE 網頁為參考範例，目標是練習：
- 如何將一個「真實網站畫面」拆解成 HTML 結構
- 如何使用 CSS 進行整頁排版與樣式設定
- 熟悉常見商業網站的版面配置方式
此練習只做一頁，為了前端切版練習，所以不包含後端或 JavaScript 的功能

- 使用 Flexbox 是練習切版的核心工具
- 練習過程中沒有把CSS拆解出來，直接寫在 <style> 中（之後要拆成外部檔案）
- 沒有處理 RWD
寫得清楚，比較重要

### 練習中學習與使用到的技術
- HTML
- CSS
- Flexbox
- reset.css（清除瀏覽器預設樣式）
- Font Awesome（圖示字型）

### 頁面結構拆解（思考方式）
使用 ```<section>``` 切割頁面區塊
整個頁面依照「功能區」分為多個 section：
- 廣告列（ad）
- 導覽列（header）
- 主視覺（main / hero）
- 功能介紹（features）
- 品牌推薦（brand）
- 底部區塊的語義 (Footer)
```
<! -- html ==!>

<section>
    <div class="main">...</div>
</section>
```
#### 練習心得：
一個 section規劃為一個完整功能區塊，結構需要清楚，有助於之後閱讀程式碼

### class 命名以「用途」為主
命名方式：
- ```.wrap``` / ```.group```：控制內容寬度與置中
- ```.row```：橫向排列的一列內容
- ```.item```：重複出現的小單位
這樣命名是自己一看 class 就知道「這塊在做什麼」
避免用顏色、位置當命名（例如 ```.blueBox```）

## 版面配置重點（使用 CSS）
### 固定導覽列（position: fixed）
```
<! -- css ==!>

.ad,
.headerTop,
.header {
    position: fixed;
    top: 0;
}
```
同時在 body 補空間：
```
<! -- css ==!>

body {
    padding-top: 140px;
}
```
#### 練習心得
過程中 fixed 元素會脫離預想的排版，如果沒有補 padding，內容會被蓋住


### 使用 Flexbox 排版
```
<! -- css ==!>

.wrap {
    display: flex;
    justify-content: space-around;
}
```
```
<! -- css ==!>

.row {
    display: flex;
}
```
#### 練習心得
Flexbox 很適合做「左右排列」，比 float 好控制、好閱讀
- ```display: flex```
- ```justify-content```
- ```flex-wrap```

### 用 CSS 製作交錯圖文版型
```
<! -- css ==!>

.row:nth-child(2n - 1) {
    flex-direction: row-reverse;
}
```
#### 練習心得：
不用改 HTML，用 CSS 就能控制左右順序，這樣可以降低重複結構的撰寫

## 視覺與互動細節
### hover 效果增加互動感
```
a:hover {
    color: blue;
}
```
```
.btnTry a:hover {
    opacity: 70%;
}
```
#### 練習心得：
讓使用者知道「可以點」按鈕、導覽列，都很適合加 hover

### 表單輸入框樣式調整
```
<! -- css ==!>

input {
    border: none;
    border-bottom-style: solid;
}
```
```
<! -- css ==!>

::placeholder {
    color: white;
}
```
#### 練習心得：
透過 CSS 可以做個一致的風格

## 清單與裝飾技巧
### 使用 ::before 自訂清單符號
```
<! -- css ==!>

.list li::before {
    content: "\2714";
    color: blue;
}
```

#### 練習心得：
不一定要用圖片，CSS 也能做裝飾，會比較好維護

## 外部資源使用
### reset.css
```
<! -- html --!>

<link rel="stylesheet" href="../reset.css">
```
為了清除不同瀏覽器的預設樣式差異讓版面結果更一致

### Font Awesome 圖示
```
<! -- html --!>

<script src="https://kit.fontawesome.com/..."></script>
```
```
<! -- html --!>

<i class="fa-brands fa-facebook-f"></i>
```
不用自己畫 icon，可用 CSS 控制大小與顏色
