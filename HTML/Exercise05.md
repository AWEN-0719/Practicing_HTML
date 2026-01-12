# Bootstrap 5 官方 Examples 頁的復刻 - 筆記

- 運用 Bootstrap 可解決結構與響應式
- 運用 CSS 可處理視覺
- 採用 Bootstrap 的 Utility，可少寫 CSS
- 練習 RWD 使用 Bootstrap，不足之處再補 Media
- 從 Bootstrap 載入 → Navbar → Utility → Grid → Card → RWD

## Bootstrap 載入與設定
### 必要的meta與CSS
```html=
<meta name="viewport" content="width=device-width, initial-scale=1">
```
- Bootstrap RWD 必備，沒有這行手機尺寸會失效

```html=
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
```
- 使用CDN載入Bootstrap練習，免安裝

### Bootstrap JavaScript 互動功能
```html=
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
```
- 用於 Navbar 摺疊與 Toggle 按鈕
- ```bundle```內含Popper

## Navbar ( 導覽列 )
### Navbar 基本結構
```html=
<nav class="navbar navbar-expand-md navbar-light">
```
- ```navbar```，啟用 Navbar元件
- ```navbar-expand-md```，md 以上展開，以下折疊
- ```navbar-light```，淺色文字配置（實際搭配自訂背景）

### RWD 折疊選單（Collapse）
```html=
<button class="navbar-toggler"
    data-bs-toggle="collapse"
    data-bs-target="#navbarSupportedContent">
```
```html=
<div class="collapse navbar-collapse" id="navbarSupportedContent">
```
- ```data-bs-toggle="collapse"``` 啟動 Bootstrap JS
- ```data-bs-target``` 必須對應 id
- md 以下自動變成「漢堡選單」
- 
### Navbar 排版（Flex + Utility）
```html=
<ul class="navbar-nav me-auto">
```
- ```me-auto```是把後面的元素推到最右邊，用於左選單與右工具列
```html=
<ul class="navbar-nav app flex-row flex-wrap ms-md-auto">
```
- ```flex-row```橫向排列icon
- ```flex-wrap```手機時自動換行
- ```ms-md-auto```md以上推到右邊

## 使用 Utility Classes
### 間距
- ``` m-*```/```p-*``` ; margin / padding
- ```mt-3``` ; 上方外距，margin-top
- ```px-0``` ; 左右 padding = 0
- ```mb-md-0``` ; md 以上取消 margin-bottom = 0

### 文字與字級
- ```fs-1``` ~ ```fs-6``` ; 字級大小
- ```fw-bold ``` / ```fw-light``` ; 粗細
- ```text-white``` ; 白字
- ```text-black-50``` ; 半透明黑
- ```text-center``` ; 置中

### 排版 Flex
```html=
<div class="d-flex flex-wrap justify-content-start">
```
-  ```d-flex``` ; 啟用 flex
-  ```flex-wrap``` ; 允許換行
-  ```justify-content-start``` ; 左對齊

## 欄位系統 Grid
```html=
<div class="card col-sm-12 col-md-4 col-lg-3">
```
使用 Bootstrap 12 欄的 Card RWD
- 螢幕尺寸 sm (手機) ; 12欄，一行一個
- 螢幕尺寸 md (平板) ; 4 欄，三個一排
- 螢幕尺寸 ig (桌機) ; 3 欄，四個一排

## Card 元件
```html=
<div class="card">
  <img class="card-img-top">
  <div class="card-body">
```
- ```card``` ; 卡片容器
- ```card-img-top``` ; 上方圖片
- ```card-body``` ; 內容區
- ```card-title``` ; 標題
- ```card-text``` ; 文字內容
  
```css=
.main .card {
    border: none;
}
```
- 運用 CSS 刻意移除 Bootstrap 預設的邊框
- 維持元件結構，調整視覺


## 按鈕 Buttons
```html=
<button class="btn">
```
- 使用 ```.btn``` 啟動 Bootstrap 樣式
- 顏色與 hover 由自訂的 CSS 控制

## RWD 與 自訂
Bootstrap RWD
```html=
col-sm-12 col-md-4 col-lg-3
mb-md-0
ms-md-auto
```
自訂 Media
```css=
@media screen and (max-width: 768px) { ... }
@media screen and (min-width: 768px) { ... }
```
- 自訂 Media是為了精準控制 width / padding

## Bootstrap 與自訂 CSS 分工原則
- 排版；Bootstrap Grid / Flex
- 間距；Utility Classes
- 元件；Bootstrap Components
- 顏色；自訂 CSS

