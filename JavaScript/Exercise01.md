用 JavaScript 來控制網頁內容，不是只用 HTML
- window.onload 可以等網頁全部載入後再執行程式

練習了 getElementById 和 querySelectorAll，知道可以用它們來取得網頁上的元素
- getElementById("container") 來抓 div 容器

使用 createElement 和 appendChild 新增圖片時，一開始不太熟，但多試幾次後就比較懂流程
- createElement("img") 可以在程式中建立圖片
- appendChild() 可以把圖片加到畫面上

透過 for 迴圈一次載入很多寶可夢圖片，讓我更清楚迴圈在實際應用中的用法
- 學到 padStart(3, "0") 可以把數字補成三位數（001、002），這樣圖片網址才會正確

幫圖片加上點擊事件後
- addEventListener("click") 可以讓圖片被點擊後刪除。
- querySelectorAll("img") 可以取得目前有幾張圖片
- innerHTML = "" 可以清空畫面上的內容

- 在做新增和刪除功能時，有發現順序跟數量要算清楚，不然會出錯
- 雖然程式一開始常出現錯誤，但透過不斷測試和修改，最後能正常執行
