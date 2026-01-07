## 練習03  CSS Position（定位）與 Flexbox 的搭配使用
=====================================================
練習的重點在於 CSS Position（定位）與 Flexbox 的搭配使用，透過重複的內容結構，製作出 左右交錯、圖文重疊的版面效果。

本次練習主要學習目標：
- 理解 position: relative 與 position: absolute 的實際用途
- 練習製作「重疊式」版面配置
- 使用 nth-of-type 控制左右交錯排版
- 在不改 HTML 結構的前提下，僅用 CSS 控制版型變化
- 本作品前端切版練習，不包含 JavaScript 功能。

二、使用技術（Technologies）

HTML5

CSS3

Flexbox

CSS Position

reset.css（清除瀏覽器預設樣式）

Font Awesome（圖示字型）

三、HTML 結構設計說明

每一組內容皆包在一個 <section> 中，
並統一拆成三個主要區塊：

A 區：標題區（.title）

區塊標題

直書數字（01～05）

疊在標題上的文字說明區塊

B 區：圖片區（.main-video）

主要圖片

按鈕圖片

使用 Flexbox 做橫向排列

C 區：文字說明區（.main-text）

功能說明標語

多組小標題與段落

使用 margin 與 z-index 製作重疊效果

四、CSS 重點學習筆記
4.1 position: relative 與 position: absolute
.title {
    position: relative;
}

.title .title-text {
    position: absolute;
}

學到的重點：

position: relative 是 定位的參考點

position: absolute 會以最近的 relative 父層為基準

適合用來做：

疊在圖片或色塊上的文字

不影響其他元素排版的裝飾區塊

在本練習中，黑色的 .title-text 就是疊在紅色標題區上。

4.2 使用 nth-of-type 製作左右交錯版型
section:nth-of-type(even) .title {
    margin-left: auto;
}

section:nth-of-type(even) .main-video {
    flex-direction: row-reverse;
}

為什麼這樣寫？

所有 section HTML 結構完全相同

偶數區塊只透過 CSS 改變排列方向

避免複製兩套 HTML 結構

📌 這是實務上非常重要的觀念

4.3 Flexbox 應用於圖片區排列
.main-video {
    display: flex;
    align-items: center;
}


Flexbox 在這裡用來：

控制圖片與按鈕的左右排列

快速調整對齊方式

搭配 row-reverse 製作交錯效果

4.4 使用負 margin 製作視覺重疊
.main-video .show-video {
    margin-right: -50px;
}

.main-text {
    margin-top: -2em;
    position: relative;
    z-index: 2;
}

學習心得：

負 margin 可以讓元素「往外推」

搭配 z-index 可控制前後層次

常用於設計感較強的商業網站版型

4.5 直書文字（writing-mode）
.title span {
    writing-mode: vertical-lr;
}

用途：

製作直向數字標示（01、02、03）

提升視覺辨識度

不需圖片即可完成排版效果

4.6 使用 ::before 客製清單符號
.main-text p:before {
    content: '●';
    color: red;
    transform: scale(.7);
}

學到的觀念：

不一定要使用 <ul><li>

CSS 偽元素可製作裝飾符號

視覺與結構可分離設計

五、為什麼這個練習重要？

這個練習幫助我理解：

Position 並不是亂用，而是「有目的地疊」

複雜版型可以靠 規律結構 + CSS 條件控制

好的切版不是元素少，而是邏輯清楚

六、目前不足與可改進方向

CSS 直接寫在 <style> 中（可改為外部檔案）

尚未加入 RWD（media query）

class 命名尚未系統化（可練習 BEM）

七、學習總結（給未來的自己）

這次練習讓我真正理解
Position 是「輔助版型設計的工具」，
而不是用來硬撐排版的方式。
