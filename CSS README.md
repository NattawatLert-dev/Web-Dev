# 📘 CSS เบื้องต้น — สรุปครบทุกหัวข้อ พร้อมคำอธิบายการใช้งาน

> Cascading Style Sheets (CSS3) — เอกสารสรุปพร้อมตัวอย่างโค้ดและคำอธิบายแต่ละหัวข้อ

-----

## สารบัญ

1. [CSS คืออะไร](#1-css-คืออะไร)
1. [โครงสร้างของ CSS](#2-โครงสร้างของ-css)
1. [ประเภทของ Selector](#3-ประเภทของ-selector)
1. [การประกาศใช้ CSS](#4-การประกาศใช้-css)
1. [Comment](#5-comment)
1. [หน่วยวัด (Units)](#6-หน่วยวัด-units)
1. [ฟอนต์ (Font)](#7-ฟอนต์-font)
1. [สี (Color)](#8-สี-color)
1. [ข้อความ (Text)](#9-ข้อความ-text)
1. [ความกว้าง & ความสูง](#10-ความกว้าง--ความสูง)
1. [Box Model](#11-box-model)
1. [Background](#12-background)
1. [Display & Visibility](#13-display--visibility)
1. [Position](#14-position)
1. [Float & Clear](#15-float--clear)
1. [Overflow](#16-overflow)
1. [Link Pseudo-class](#17-link-pseudo-class)
1. [Opacity, Box-shadow & Text-shadow](#18-opacity-box-shadow--text-shadow)
1. [Cursor](#19-cursor)
1. [Responsive Web Design & Media Query](#20-responsive-web-design--media-query)
1. [Viewport Units](#21-viewport-units)
1. [Flexbox](#22-flexbox)
1. [CSS Grid Layout](#23-css-grid-layout)
1. [Advanced Selectors](#24-advanced-selectors)
1. [CSS Variable](#25-css-variable)
1. [Transform](#26-transform)
1. [Transition](#27-transition)
1. [CSS Animation & @keyframes](#28-css-animation--keyframes)
1. [🔥 หัวข้อเพิ่มเติมที่ต้องรู้](#29-หัวข้อเพิ่มเติมที่ต้องรู้)

-----

## 1. CSS คืออะไร

**ใช้เมื่อ:** ต้องการตกแต่งหน้าเว็บให้สวยงาม โดยแยกส่วน “รูปแบบ” ออกจาก “เนื้อหา” HTML

CSS (Cascading Style Sheets) คือภาษาที่ใช้ควบคุมหน้าตาของ HTML เช่น กำหนดสี ขนาด ฟอนต์ ระยะห่าง และตำแหน่งของ element ต่างๆ บนหน้าเว็บ โดยไม่ต้องยุ่งกับโครงสร้าง HTML เลย

> **ตัวอย่างความสัมพันธ์:** HTML คือโครงสร้างบ้าน, CSS คือสีทาบ้านและการตกแต่ง

-----

## 2. โครงสร้างของ CSS

**ใช้เมื่อ:** เขียน CSS ทุกครั้ง — นี่คือรูปแบบพื้นฐานที่ต้องเข้าใจก่อน

CSS ทุกบรรทัดมีโครงสร้างเดียวกันคือ “บอกว่าจะจัดการ element ไหน แล้วตั้งค่าอะไร”

```css
selector {
  property: value;
  property: value;
}
```

|ส่วนประกอบ   |ความหมาย                 |ตัวอย่าง                        |
|------------|-------------------------|------------------------------|
|**Selector**|ระบุว่าจะ style element ไหน|`p`, `.card`, `#header`       |
|**Property**|คุณสมบัติที่ต้องการตั้งค่า        |`color`, `font-size`, `margin`|
|**Value**   |ค่าที่กำหนดให้กับ property     |`red`, `16px`, `auto`         |

```css
/* อ่านว่า: "ทุก <p> ให้ตัวอักษรสีแดง จัดกึ่งกลาง และมี padding 10px" */
p {
  color: red;
  text-align: center;
  padding: 10px;
}
```

- property กับ value คั่นด้วย **colon** (`:`)
- แต่ละ property คั่นด้วย **semi-colon** (`;`)
- ถ้าลืมใส่ `;` CSS บรรทัดนั้นและบรรทัดถัดไปอาจไม่ทำงาน

-----

## 3. ประเภทของ Selector

**ใช้เมื่อ:** ต้องการเลือก element ที่จะ style — เป็นหัวใจสำคัญของ CSS

### Element Selector

ใช้เมื่อต้องการกำหนด style ให้ **ทุก element ที่เป็น tag เดียวกัน** ทั้งหน้า

```css
/* ทุก <p> ในหน้าเว็บจะมีตัวอักษรสีน้ำเงิน */
p {
  color: blue;
}

/* ทุก <h1> จะมีขนาดฟอนต์ 32px */
h1 {
  font-size: 32px;
}
```

### Class Selector (`.`)

ใช้เมื่อต้องการ style **หลาย element พร้อมกัน** โดยไม่จำกัดชนิด tag
สามารถใช้ class เดียวกันกับ element หลายตัวได้

```css
/* ทุก element ที่มี class="card" จะมีพื้นหลังขาวและ border */
.card {
  background-color: white;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
}
```

```html
<!-- ใช้ได้กับหลาย tag -->
<div class="card">การ์ดที่ 1</div>
<article class="card">การ์ดที่ 2</article>
<section class="card">การ์ดที่ 3</section>
```

### ID Selector (`#`)

ใช้เมื่อต้องการ style **element เฉพาะตัวเดียว** ในหน้า — ID ห้ามซ้ำกันในหน้าเดียว

```css
/* เฉพาะ element ที่มี id="navbar" เท่านั้น */
#navbar {
  background-color: #333;
  color: white;
  position: fixed;
  top: 0;
  width: 100%;
}
```

```html
<nav id="navbar">เมนู</nav>
```

### Universal Selector (`*`)

ใช้เมื่อต้องการกำหนด style ให้ **ทุก element ในหน้า** — มักใช้สำหรับ CSS Reset

```css
/* รีเซ็ต margin/padding ทุก element ก่อนเริ่มเขียน CSS */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

### Union Selector (`,`)

ใช้เมื่อต้องการกำหนด **style เดียวกัน** ให้กับหลาย selector พร้อมกัน ลดการเขียนโค้ดซ้ำ

```css
/* แทนที่จะเขียน 3 block แยก รวมเป็น block เดียว */
h1, h2, h3 {
  font-family: 'Sarabun', sans-serif;
  color: #333;
}
```

### Tag.Class Selector

ใช้เมื่อต้องการ style **เฉพาะ tag ชนิดนั้นที่มี class นั้น** เท่านั้น
เหมาะเมื่อ class เดียวกันใช้กับหลาย tag แต่อยากให้แต่ละ tag มีหน้าตาต่างกัน

```css
/* <p> ที่มี class="highlight" เท่านั้น ไม่รวม <div class="highlight"> */
p.highlight {
  background-color: yellow;
}

/* ใช้กับ form validation */
p.error   { color: red; }
p.success { color: green; }
p.warning { color: orange; }
```

-----

## 4. การประกาศใช้ CSS

**ใช้เมื่อ:** ต้องเลือกว่าจะใส่ CSS ไว้ที่ไหนของโปรเจกต์

### Inline — ใช้เมื่อต้องการแก้เฉพาะ element นั้น element เดียว เช่น แก้เร็วๆ ชั่วคราว

> ⚠️ ไม่แนะนำในโปรเจกต์จริง เพราะดูแลยากและ override ได้ยาก

```html
<p style="color: green; font-size: 18px; font-weight: bold;">ข้อความสีเขียว</p>
```

### Internal / Embedded — ใช้เมื่อทำหน้าเว็บหน้าเดียว หรือ style ใช้เฉพาะหน้านั้น

```html
<head>
  <style>
    /* CSS อยู่ใน HTML ไฟล์เดียวกัน */
    body { font-family: 'Sarabun', sans-serif; }
    h1   { color: #333; }
    p    { line-height: 1.6; }
  </style>
</head>
```

### External — แนะนำสำหรับโปรเจกต์จริง เพราะแยกไฟล์ชัดเจน และใช้ CSS ไฟล์เดียวกับหลายหน้าได้

```html
<!-- ไฟล์ index.html -->
<head>
  <link rel="stylesheet" href="style.css">
  <!-- โหลดฟอนต์จาก Google Fonts ก็ทำแบบเดียวกัน -->
  <link href="https://fonts.googleapis.com/css2?family=Sarabun&display=swap" rel="stylesheet">
</head>
```

```css
/* ไฟล์ style.css — ใช้ร่วมกันได้ทุกหน้าที่ link ไฟล์นี้ */
body { font-family: 'Sarabun', sans-serif; }
```

### ลำดับความสำคัญ (Specificity)

เมื่อ CSS หลายบรรทัดกำหนด property เดียวกัน จะใช้ค่าจาก selector ที่มีความสำคัญสูงกว่า

```
!important  >  Inline  >  ID  >  Class  >  Element
```

```css
/* ตัวอย่าง: ทั้งสามบรรทัดกำหนดสีให้ <p id="msg" class="txt"> */
p         { color: blue; }    /* ถูก override */
.txt      { color: green; }   /* ถูก override */
#msg      { color: red; }     /* ชนะ — ID มี specificity สูงกว่า */

/* !important บังคับให้ชนะทุกอย่าง — ใช้เมื่อจำเป็นจริงๆ */
p { color: purple !important; }
```

-----

## 5. Comment

**ใช้เมื่อ:** ต้องการอธิบายโค้ด แบ่งส่วน หรือปิดการใช้งาน CSS ชั่วคราว

Comment จะไม่ถูก render ในหน้าเว็บ browser จะข้ามส่วนนี้ไป

```css
/* ===== Global Styles ===== */

/* กำหนดสีหลักของเว็บ */
:root {
  --primary: #3498db;
}

p {
  color: red;             /* สีตัวอักษร */
  /* font-size: 20px; */  /* ปิดชั่วคราว เผื่อเปิดทีหลัง */
}

/*
  TODO: ปรับ responsive ส่วนนี้
  - mobile: 1 column
  - tablet: 2 columns
*/
```

-----

## 6. หน่วยวัด (Units)

**ใช้เมื่อ:** กำหนดขนาด ระยะห่าง หรือความสูงของ element

### Absolute — ค่าตายตัว ไม่เปลี่ยนตามขนาดหน้าจอ เหมาะกับสิ่งพิมพ์หรือขนาดที่แน่นอน

|หน่วย      |เหมาะใช้กับ                        |
|----------|---------------------------------|
|`px`      |ขนาด border, icon, spacing ส่วนใหญ่|
|`pt`      |งานสิ่งพิมพ์ (print stylesheet)      |
|`cm`, `mm`|งานพิมพ์ที่ต้องการขนาดจริง             |

```css
.icon { width: 24px; height: 24px; }   /* ไอคอนขนาดแน่นอน */
.border { border: 1px solid #ccc; }    /* เส้นบาง 1 pixel */
```

### Relative — ค่าสัมพัทธ์ ปรับตามบริบท เหมาะกับ Responsive Design

|หน่วย |อ้างอิงจาก                         |ตัวอย่างการใช้              |
|-----|---------------------------------|-------------------------|
|`%`  |ขนาด parent element              |ความกว้าง column          |
|`em` |font-size ของ element ตัวเอง      |padding, margin รอบข้อความ|
|`rem`|font-size ของ `<html>` (ปกติ 16px)|ขนาดฟอนต์ทั้งเว็บ            |
|`vw` |ความกว้างของ browser window       |layout เต็มหน้าจอ          |
|`vh` |ความสูงของ browser window         |hero section, full-screen|

```css
/* ตัวอย่างการใช้งานจริง */
.container {
  width: 90%;           /* ความกว้าง 90% ของ parent */
  max-width: 1200px;    /* แต่ไม่เกิน 1200px */
}

body {
  font-size: 16px;      /* base font = 16px */
}

h1 { font-size: 2rem; }    /* 32px (2 × 16px) */
p  { font-size: 1rem; }    /* 16px */
small { font-size: 0.875rem; } /* 14px */

.hero {
  height: 100vh;        /* เต็มความสูงจอ */
  padding: 2em;         /* padding = 2 × font-size ของ .hero */
}
```

-----

## 7. ฟอนต์ (Font)

**ใช้เมื่อ:** ต้องการเปลี่ยนรูปแบบ ขนาด หรือน้ำหนักของตัวอักษร

```css
body {
  /* กำหนดฟอนต์ — browser จะลองจากซ้ายไปขวา ถ้าไม่มีจะใช้ตัวถัดไป */
  font-family: 'Sarabun', 'Kanit', Arial, sans-serif;
}

h1 {
  font-size: 2rem;        /* ขนาด: ตัวเลข (px, rem, em) หรือ keyword */
  font-size: large;       /* keyword: xx-small → xx-large */

  font-weight: bold;      /* หนา */
  font-weight: 700;       /* ตัวเลข 100 (บาง) → 900 (หนามาก) */
  font-weight: lighter;   /* บางกว่า parent */

  font-style: italic;     /* เอียง */
  font-style: normal;     /* ปกติ */
}

/* shorthand รวมทุกอย่างในบรรทัดเดียว: style weight size/line-height family */
p {
  font: italic 400 16px/1.6 'Sarabun', sans-serif;
}
```

### นำเข้าฟอนต์จาก Google Fonts

```html
<!-- 1. ใส่ใน <head> ก่อน CSS ไฟล์ -->
<link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;700&family=Kanit&display=swap" rel="stylesheet">
```

```css
/* 2. เรียกใช้ใน CSS */
body { font-family: 'Sarabun', sans-serif; }
h1   { font-family: 'Kanit', sans-serif; }
```

-----

## 8. สี (Color)

**ใช้เมื่อ:** กำหนดสีตัวอักษร พื้นหลัง เส้นขอบ หรืออื่นๆ

```css
.box {
  /* 1. ชื่อสี (140 ชื่อมาตรฐาน) */
  color: red;
  color: tomato;
  color: cornflowerblue;

  /* 2. HEX — นิยมใช้มากที่สุด */
  color: #ff0000;         /* แดง */
  color: #f00;            /* แดง (ย่อ 3 ตัว) */
  color: #3498db;         /* น้ำเงิน */

  /* 3. RGB */
  color: rgb(255, 0, 0);          /* แดงเต็ม */
  color: rgba(255, 0, 0, 0.5);   /* แดง โปร่งใส 50% */

  /* 4. HSL — ปรับสีง่ายกว่า เพราะอ่านรู้ว่าสีอะไร */
  color: hsl(0, 100%, 50%);             /* แดง */
  color: hsl(200, 80%, 50%);            /* ฟ้า */
  color: hsla(200, 80%, 50%, 0.7);      /* ฟ้า โปร่งใส 70% */
}
```

> **เทคนิค:** ใช้ HEX สำหรับสีตายตัว ใช้ rgba() เมื่อต้องการปรับความโปร่งใส ใช้ HSL เมื่อต้องการ generate สีเป็น palette

-----

## 9. ข้อความ (Text)

**ใช้เมื่อ:** ต้องการจัดรูปแบบข้อความ เช่น จัดกึ่งกลาง ขีดเส้นใต้ ระยะห่างบรรทัด

```css
p {
  /* จัดแนวข้อความ */
  text-align: left;           /* ชิดซ้าย (default) */
  text-align: center;         /* กึ่งกลาง */
  text-align: right;          /* ชิดขวา */
  text-align: justify;        /* เต็มความกว้างทุกบรรทัด */

  /* ตกแต่งเส้น */
  text-decoration: none;          /* ลบเส้นใต้ link */
  text-decoration: underline;     /* ขีดเส้นใต้ */
  text-decoration: line-through;  /* ขีดทับ (ราคาลด) */
  text-decoration: overline;      /* เส้นบน */

  /* ระยะห่าง */
  letter-spacing: 0.1em;    /* ระยะห่างระหว่างตัวอักษร */
  word-spacing: 4px;        /* ระยะห่างระหว่างคำ */
  line-height: 1.6;         /* ระยะห่างระหว่างบรรทัด (แนะนำ 1.4–1.8) */

  /* ตัวพิมพ์ใหญ่-เล็ก */
  text-transform: uppercase;    /* ตัวใหญ่ทั้งหมด */
  text-transform: lowercase;    /* ตัวเล็กทั้งหมด */
  text-transform: capitalize;   /* ขึ้นต้นทุกคำด้วยตัวใหญ่ */
}

/* ตัดข้อความยาวด้วย ... (ใช้บ่อยใน card/list) */
.title {
  white-space: nowrap;      /* ไม่ตัดบรรทัด */
  overflow: hidden;         /* ซ่อนส่วนเกิน */
  text-overflow: ellipsis;  /* แสดง ... แทน */
  max-width: 200px;         /* ต้องกำหนด max-width ด้วย */
}
```

-----

## 10. ความกว้าง & ความสูง

**ใช้เมื่อ:** ต้องการกำหนดขนาดของ box/container/image

```css
.box {
  width: 300px;         /* ความกว้างแน่นอน */
  width: 50%;           /* 50% ของ parent */
  width: auto;          /* browser คำนวณให้ (default) */

  height: 200px;
  height: auto;         /* สูงตามเนื้อหา (default) */

  /* กำหนดขอบเขตสำหรับ responsive */
  min-width: 200px;     /* กว้างขั้นต่ำ 200px ไม่ว่า % จะเหลือเท่าไหร่ */
  max-width: 800px;     /* กว้างไม่เกิน 800px — ใช้บ่อยมากกับ container */
  min-height: 100px;
  max-height: 500px;    /* ใช้บ่อยกับ modal หรือ dropdown */
}

/* ตัวอย่างใช้จริง: container กว้างตาม % แต่ไม่เกิน 1200px */
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;       /* จัดกึ่งกลาง */
}
```

-----

## 11. Box Model

**ใช้เมื่อ:** ต้องการเข้าใจว่าทำไม element ถึงมีขนาดไม่ตรงกับที่กำหนด

ทุก element ใน HTML มีพื้นที่ 4 ชั้นซ้อนกัน:

```
┌─────────────────────────────┐  ← Margin (ระยะห่างจาก element อื่น)
│  ┌───────────────────────┐  │
│  │  Border (เส้นขอบ)    │  │
│  │  ┌─────────────────┐  │  │
│  │  │ Padding (พื้นที่  │  │  │
│  │  │ ว่างด้านใน)      │  │  │
│  │  │  ┌───────────┐  │  │  │
│  │  │  │  Content  │  │  │  │
│  │  │  └───────────┘  │  │  │
│  │  └─────────────────┘  │  │
│  └───────────────────────┘  │
└─────────────────────────────┘
```

### Margin — ระยะห่างระหว่าง element กับ element อื่นรอบๆ (ด้านนอก border)

```css
.box {
  /* ใส่ค่าเดียว = ทุกด้าน */
  margin: 20px;

  /* 2 ค่า = บน-ล่าง | ซ้าย-ขวา */
  margin: 10px 20px;

  /* 3 ค่า = บน | ซ้าย-ขวา | ล่าง */
  margin: 10px 20px 30px;

  /* 4 ค่า = บน | ขวา | ล่าง | ซ้าย (ตามเข็มนาฬิกา) */
  margin: 10px 20px 30px 5px;

  /* auto = browser แบ่งพื้นที่ให้เท่ากันทั้งซ้ายขวา → จัดกึ่งกลาง */
  margin: 0 auto;

  /* กำหนดทีละด้าน */
  margin-top: 10px;
  margin-bottom: 10px;
}
```

### Padding — ระยะห่างระหว่างเนื้อหากับ border (ด้านใน)

```css
.button {
  /* padding ทำให้ปุ่มมีพื้นที่รอบข้อความ */
  padding: 12px 24px;    /* บน-ล่าง 12px | ซ้าย-ขวา 24px */
  padding-top: 8px;
  padding-left: 16px;
}
```

### Border — เส้นขอบ

```css
.card {
  /* shorthand: width style color */
  border: 1px solid #ddd;

  /* กำหนดแยก property */
  border-width: 2px;
  border-style: solid;     /* dotted | dashed | double | groove */
  border-color: #333;

  /* เฉพาะด้านใดด้านหนึ่ง */
  border-bottom: 3px solid #3498db;   /*밑줄 เหมือน underline */
  border-left: 4px solid red;         /* accent bar ซ้าย */

  /* มุมโค้ง */
  border-radius: 8px;     /* โค้งทุกมุม */
  border-radius: 50%;     /* วงกลม (ต้องให้ width = height) */
  border-top-left-radius: 16px;
}
```

### box-sizing — สิ่งสำคัญที่มักลืม

```css
/*
  ปกติ (content-box):
  width: 200px + padding: 20px + border: 2px = จริงๆ กว้าง 244px

  border-box:
  width: 200px = รวม padding และ border แล้ว → กว้างจริง 200px
*/
* {
  box-sizing: border-box;  /* แนะนำให้ใส่ทุกโปรเจกต์ */
}
```

-----

## 12. Background

**ใช้เมื่อ:** ต้องการกำหนดพื้นหลังของ element ไม่ว่าจะเป็นสี รูปภาพ หรือ gradient

```css
.hero {
  /* สีพื้นหลัง */
  background-color: #f0f4f8;
  background-color: transparent;       /* โปร่งใส */

  /* รูปภาพพื้นหลัง */
  background-image: url('bg.jpg');
  background-image: url('https://example.com/photo.jpg');

  /* การซ้ำของรูป */
  background-repeat: no-repeat;        /* ไม่ซ้ำ (ใช้บ่อยที่สุด) */
  background-repeat: repeat-x;         /* ซ้ำเฉพาะแนวนอน (pattern) */
  background-repeat: repeat;           /* ซ้ำทั้ง x และ y (default) */

  /* ตำแหน่งรูป */
  background-position: center center;  /* กึ่งกลาง */
  background-position: top left;
  background-position: 50% 30%;        /* x% y% */

  /* ขนาดรูป */
  background-size: cover;    /* ขยายให้เต็ม element รักษาสัดส่วน (ใช้บ่อย) */
  background-size: contain;  /* ย่อให้เห็นรูปทั้งหมด */
  background-size: 100% 100%; /* ยืดเต็ม element */

  /* การเลื่อนตาม scroll */
  background-attachment: fixed;  /* รูปอยู่กับที่ (parallax effect) */
  background-attachment: scroll; /* เลื่อนตามหน้า (default) */
}

/* Gradient — ไล่สี */
.gradient-box {
  background: linear-gradient(to right, #667eea, #764ba2);
  background: linear-gradient(135deg, #f093fb, #f5576c);
  background: radial-gradient(circle, #ffecd2, #fcb69f);
}

/* รวมทุกอย่างใน shorthand เดียว */
.hero {
  background: #fff url('hero.jpg') no-repeat center center / cover;
}
```

-----

## 13. Display & Visibility

**ใช้เมื่อ:** ต้องการควบคุมว่า element จะแสดง/ซ่อน หรือเรียงตัวอย่างไร

### display

```css
/* block — ครอบเต็มความกว้าง ขึ้นบรรทัดใหม่เสมอ
   (default ของ: div, p, h1–h6, section, article) */
.box { display: block; }

/* inline — กว้างแค่เนื้อหา ไม่ขึ้นบรรทัดใหม่ กำหนด width/height ไม่ได้
   (default ของ: span, a, strong, em) */
.badge { display: inline; }

/* inline-block — เหมือน inline แต่กำหนด width/height ได้
   ใช้เมื่อต้องการ element เรียงแนวนอน แต่ต้องการกำหนดขนาด */
.nav-item { display: inline-block; width: 100px; }

/* none — ซ่อน element และไม่ใช้พื้นที่เลย (เหมือนไม่มีอยู่)
   ใช้ซ่อน dropdown menu หรือ modal */
.dropdown { display: none; }
.dropdown.active { display: block; }

/* flex และ grid — ดูหัวข้อ 22 และ 23 */
```

### visibility vs display:none

```css
/* visibility: hidden — ซ่อน แต่ยังใช้พื้นที่อยู่ (เหมือนล่องหน) */
.ghost { visibility: hidden; }

/* display: none — ซ่อนและไม่ใช้พื้นที่ (หายไปเลย) */
.gone { display: none; }
```

-----

## 14. Position

**ใช้เมื่อ:** ต้องการควบคุมตำแหน่งของ element อย่างละเอียด

```css
/* static — ค่า default จัดวางตาม flow ปกติ top/left ไม่มีผล */
.normal { position: static; }

/* relative — ขยับจากตำแหน่งเดิมของตัวเอง ไม่กระทบ element อื่น */
.shifted {
  position: relative;
  top: 10px;   /* ขยับลงจากตำแหน่งเดิม 10px */
  left: 20px;  /* ขยับขวาจากตำแหน่งเดิม 20px */
}

/* absolute — วางอ้างอิงจาก parent ที่ไม่ใช่ static
   ถ้าไม่มี parent ที่ position ≠ static จะอ้างอิงจาก body
   ใช้กับ tooltip, dropdown, badge, icon บน card */
.parent {
  position: relative;  /* ← สำคัญ: ต้องมีบน parent */
}
.badge {
  position: absolute;
  top: -8px;
  right: -8px;
}

/* fixed — ติดหน้าจอ ไม่เลื่อนตาม scroll
   ใช้กับ navbar, back-to-top button, cookie banner */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
}

/* sticky — เลื่อนตามปกติจนถึงตำแหน่งที่กำหนด แล้วติดอยู่กับที่
   ใช้กับ table header, sidebar ที่ scroll ตามแต่ไม่หายไป */
.sticky-header {
  position: sticky;
  top: 0;
}

/* z-index — ควบคุมลำดับการซ้อน ยิ่งมากยิ่งอยู่บน */
.modal    { z-index: 1000; }
.overlay  { z-index: 999; }
.dropdown { z-index: 100; }
```

```css
/* เทคนิคยอดนิยม: จัดกึ่งกลางแนวตั้ง-นอน ด้วย absolute + transform */
.parent { position: relative; }
.center-child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

-----

## 15. Float & Clear

**ใช้เมื่อ:** ต้องการให้รูปภาพลอยข้างข้อความ (วิธีเก่า — ปัจจุบันนิยมใช้ Flexbox/Grid แทน)

```css
/* float — ทำให้ element "ลอย" ไปทางซ้ายหรือขวา
   element อื่นจะล้อมรอบ float element */
img.float-left {
  float: left;
  margin-right: 16px;   /* เว้นระยะห่างจากข้อความ */
}

img.float-right {
  float: right;
  margin-left: 16px;
}

/* clear — บอกว่า element นี้ไม่ยอมขึ้นข้างๆ float element
   ใช้เพื่อยุติ float ที่กำลังทำงาน */
.after-float {
  clear: both;     /* left | right | both */
}

/* clearfix — วิธีจัดการ float ที่ทำให้ parent หดตัว */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

-----

## 16. Overflow

**ใช้เมื่อ:** เนื้อหาในกล่องมีมากกว่าพื้นที่ที่กำหนด ต้องการควบคุมว่าจะแสดงอย่างไร

```css
.box {
  width: 200px;
  height: 100px;

  overflow: visible;  /* แสดงเนื้อหาที่เกินออกนอก box (default) */
  overflow: hidden;   /* ซ่อนเนื้อหาที่เกิน — ใช้บ่อยกับ border-radius */
  overflow: scroll;   /* มี scrollbar เสมอ แม้เนื้อหาจะไม่เกิน */
  overflow: auto;     /* มี scrollbar เฉพาะเมื่อเนื้อหาเกิน (แนะนำ) */

  /* กำหนดแยกแนวนอน-แนวตั้ง */
  overflow-x: auto;   /* scroll แนวนอน */
  overflow-y: hidden; /* ซ่อนแนวตั้ง */
}

/* ตัวอย่างใช้จริง: กล่องข้อความที่ scroll ได้ */
.chat-box {
  height: 400px;
  overflow-y: auto;
}

/* ตัดมุมโค้งต้องใช้ overflow: hidden บน parent */
.rounded-card {
  border-radius: 12px;
  overflow: hidden;  /* ถ้าไม่มีนี้ รูปภาพข้างในจะทะลุมุมโค้ง */
}
```

-----

## 17. Link Pseudo-class

**ใช้เมื่อ:** ต้องการกำหนดหน้าตา link ในแต่ละสถานะ (ยังไม่คลิก, วางเมาส์, คลิกแล้ว)

```css
/* ต้องเรียงตามลำดับนี้เสมอ: L-V-H-A (LoVe HAte) */
a:link    { color: #3498db; text-decoration: none; }   /* ยังไม่เคยคลิก */
a:visited { color: #9b59b6; }                          /* คลิกแล้ว */
a:hover   { color: #2980b9; text-decoration: underline; }  /* เมาส์วางอยู่ */
a:active  { color: #e74c3c; }                          /* ขณะกดค้างอยู่ */

/* ตัวอย่างปุ่มแบบ link */
.nav-link {
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 4px;
  transition: background-color 0.2s;
}
.nav-link:hover {
  background-color: rgba(255,255,255,0.2);
}

/* hover ใช้กับ element อื่นได้ด้วย ไม่ใช่แค่ link */
.button:hover { background-color: darkblue; }
.card:hover   { box-shadow: 0 8px 24px rgba(0,0,0,0.15); }
```

-----

## 18. Opacity, Box-shadow & Text-shadow

**ใช้เมื่อ:** ต้องการเพิ่มความลึก ความโปร่งใส หรือเงาให้ element

### Opacity — ความโปร่งใสของทั้ง element รวมถึงเนื้อหาข้างใน

```css
.overlay {
  opacity: 1.0;   /* ทึบสุด (default) */
  opacity: 0.5;   /* โปร่งใส 50% — เนื้อหาข้างในก็โปร่งใสด้วย */
  opacity: 0.0;   /* มองไม่เห็น แต่ยังใช้พื้นที่อยู่ */
}

/* ถ้าต้องการพื้นหลังโปร่งใสแต่ข้อความยังชัด ให้ใช้ rgba() แทน */
.translucent-bg {
  background-color: rgba(0, 0, 0, 0.5);  /* พื้นหลังดำโปร่งใส 50% */
  color: white;                           /* ข้อความยังชัดอยู่ */
}
```

### Box-shadow — เงารอบกล่อง ใช้สร้าง depth และ elevation

```css
/* box-shadow: x y blur spread color */
.card {
  /* x บวก = ขวา, ลบ = ซ้าย */
  /* y บวก = ล่าง, ลบ = บน */
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);          /* เงาเบาๆ */
  box-shadow: 0 8px 24px rgba(0,0,0,0.15);         /* เงาลึก */
  box-shadow: 4px 4px 0px 0px #000;               /* เงา flat design */
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.2);    /* เงาด้านใน */

  /* หลายเงาพร้อมกัน */
  box-shadow:
    0 1px 3px rgba(0,0,0,0.12),
    0 4px 12px rgba(0,0,0,0.08);
}

/* hover ทำให้การ์ด "ยก" ขึ้น */
.card:hover {
  box-shadow: 0 12px 32px rgba(0,0,0,0.2);
  transform: translateY(-4px);
}
```

### Text-shadow — เงาของตัวอักษร

```css
/* text-shadow: x y blur color */
h1 {
  text-shadow: 2px 2px 4px rgba(0,0,0,0.3);   /* เงาปกติ */
  text-shadow: 0 0 10px rgba(255,255,0,0.8);  /* glow effect */
  text-shadow: -1px -1px 0 #000,
                1px -1px 0 #000,
               -1px  1px 0 #000,
                1px  1px 0 #000;             /* outline text */
}
```

-----

## 19. Cursor

**ใช้เมื่อ:** ต้องการเปลี่ยนรูปร่างเมาส์เมื่อวางบน element เพื่อบอก user ว่าทำอะไรได้

```css
.button  { cursor: pointer; }      /* มือชี้ — บอกว่าคลิกได้ */
.text    { cursor: text; }         /* I-beam — บอกว่าพิมพ์ได้ */
.loading { cursor: wait; }         /* นาฬิกา — กำลังโหลด */
.move    { cursor: move; }         /* ลูกศร 4 ทิศ — ลากได้ */
.resize  { cursor: nwse-resize; }  /* ลูกศรเฉียง — ปรับขนาดได้ */
.no      { cursor: not-allowed; }  /* วงกลมมีขีด — ทำไม่ได้ */
.zoom    { cursor: zoom-in; }      /* แว่นขยาย */
.grab    { cursor: grab; }         /* มือเปิด */
.grabbing{ cursor: grabbing; }     /* มือกำ */
.help    { cursor: help; }         /* เครื่องหมาย ? */
.hidden  { cursor: none; }         /* ซ่อน cursor */
```

-----

## 20. Responsive Web Design & Media Query

**ใช้เมื่อ:** ต้องการให้หน้าเว็บแสดงผลได้ดีทั้งบน PC, Tablet และมือถือ

Media Query คือการเขียน CSS ที่จะ “ทำงานเฉพาะเมื่อหน้าจอมีขนาดตรงตามเงื่อนไข”

```css
/* === Breakpoints มาตรฐาน === */
/* Mobile:   320px – 480px  */
/* Tablet:   481px – 768px  */
/* Laptop:   769px – 1024px */
/* Desktop: 1025px – 1200px */
/* TV/Wide: 1201px+         */

/* Mobile First (แนะนำ) — เขียน CSS สำหรับมือถือก่อน แล้วค่อย override สำหรับจอใหญ่ */
.container {
  width: 100%;    /* มือถือ: เต็มหน้าจอ */
  padding: 16px;
}

@media (min-width: 768px) {
  /* จอ tablet ขึ้นไป */
  .container { width: 720px; }
  .grid { grid-template-columns: repeat(2, 1fr); }
}

@media (min-width: 1024px) {
  /* จอ laptop ขึ้นไป */
  .container { width: 960px; }
  .grid { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1200px) {
  /* จอใหญ่ */
  .container { width: 1140px; }
}

/* Desktop First — เขียนสำหรับจอใหญ่ก่อน แล้ว override สำหรับจอเล็ก */
.sidebar { display: block; }

@media (max-width: 768px) {
  /* จอเล็กกว่า 768px: ซ่อน sidebar */
  .sidebar { display: none; }
  .text    { font-size: 14px; }
}

/* เงื่อนไขหลายอย่าง */
@media screen and (min-width: 481px) and (max-width: 768px) {
  /* เฉพาะ tablet */
}

/* สำหรับหน้าพิมพ์ */
@media print {
  nav, .ads, footer { display: none; }
  body { font-size: 12pt; color: black; }
}
```

-----

## 21. Viewport Units

**ใช้เมื่อ:** ต้องการกำหนดขนาดที่อ้างอิงจากขนาดหน้าต่าง browser โดยตรง

ต้องใส่ meta viewport ใน HTML ก่อนเสมอ:

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

```css
/* vw = viewport width, vh = viewport height */

/* Hero section เต็มหน้าจอ */
.hero {
  width: 100vw;     /* กว้างเท่าหน้าต่าง browser */
  height: 100vh;    /* สูงเท่าหน้าต่าง browser */
}

/* ฟอนต์ที่ scale ตามขนาดจอ */
h1 { font-size: 5vw; }    /* บน 1000px wide = 50px, บน 500px = 25px */

/* Sidebar ที่มีความสูงเท่าหน้าจอ */
.sidebar {
  height: 100vh;
  overflow-y: auto;
}

/* vmin/vmax — ใช้เมื่อต้องการให้ scale ตามทั้งความกว้างและสูง */
.logo {
  width: 20vmin;    /* 20% ของด้านที่สั้นกว่า — ได้ขนาดที่สมดุลทุกจอ */
}
```

-----

## 22. Flexbox

**ใช้เมื่อ:** ต้องการจัด layout แบบ 1 มิติ (แถวเดียวหรือคอลัมน์เดียว) เช่น navbar, card row, centering

Flexbox มี 2 ส่วน: **Container** (กล่องที่ครอบ) และ **Items** (สมาชิกข้างใน)

```css
/* ===== Container ===== */
.container {
  display: flex;

  /* ทิศทาง */
  flex-direction: row;           /* → แนวนอน (default) */
  flex-direction: column;        /* ↓ แนวตั้ง */
  flex-direction: row-reverse;   /* ← แนวนอน ย้อนกลับ */
  flex-direction: column-reverse;/* ↑ แนวตั้ง ย้อนกลับ */

  /* การขึ้นบรรทัดใหม่เมื่อ item เกินพื้นที่ */
  flex-wrap: nowrap;       /* ไม่ขึ้นบรรทัดใหม่ (default) — item จะหด */
  flex-wrap: wrap;         /* ขึ้นบรรทัดใหม่เมื่อเต็ม */
  flex-wrap: wrap-reverse; /* ขึ้นบรรทัดใหม่แบบย้อนกลับ */

  /* จัดแนวตามแกนหลัก (แนวนอนถ้า flex-direction: row) */
  justify-content: flex-start;    /* ชิดซ้าย */
  justify-content: flex-end;      /* ชิดขวา */
  justify-content: center;        /* กึ่งกลาง */
  justify-content: space-between; /* แจกพื้นที่ว่างระหว่าง item */
  justify-content: space-around;  /* แจกพื้นที่ว่างรอบ item */
  justify-content: space-evenly;  /* แจกพื้นที่ว่างเท่ากันทุกช่อง */

  /* จัดแนวตามแกนรอง (แนวตั้งถ้า flex-direction: row) */
  align-items: stretch;     /* ยืดเต็มความสูง container (default) */
  align-items: flex-start;  /* ชิดบน */
  align-items: flex-end;    /* ชิดล่าง */
  align-items: center;      /* กึ่งกลางแนวตั้ง */
  align-items: baseline;    /* align ตาม baseline ของข้อความ */

  /* ระยะห่างระหว่าง item */
  gap: 16px;
  gap: 8px 16px;    /* row-gap column-gap */
}

/* ===== Items ===== */
.item {
  /* flex: grow shrink basis */
  flex: 1;           /* ขยายเต็มพื้นที่ที่เหลือ — ทุก item เท่ากัน */
  flex: 0 0 200px;   /* ไม่ขยาย ไม่หด กว้าง 200px */
  flex: 2;           /* ขยาย 2 เท่าของ item ที่ flex: 1 */

  flex-grow: 1;      /* ขยายเมื่อมีพื้นที่เหลือ */
  flex-shrink: 0;    /* ไม่หดเมื่อพื้นที่ไม่พอ */
  flex-basis: 200px; /* ขนาดเริ่มต้น */

  align-self: center;    /* override align-items เฉพาะ item นี้ */
  order: -1;             /* เปลี่ยนลำดับการแสดง (ต่ำ = อยู่หน้า) */
}
```

```css
/* ===== Use Cases ===== */

/* 1. จัดกึ่งกลางทั้งแนวตั้ง-นอน */
.centered {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 2. Navbar: logo ซ้าย, เมนูขวา */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px;
}

/* 3. Card grid ที่ item กว้างเท่ากัน */
.card-row {
  display: flex;
  gap: 16px;
}
.card-row .card {
  flex: 1;
}
```

-----

## 23. CSS Grid Layout

**ใช้เมื่อ:** ต้องการจัด layout แบบ 2 มิติ (มีทั้งแถวและคอลัมน์) เช่น layout หน้าเว็บ, gallery, dashboard

```css
/* ===== Container ===== */
.grid {
  display: grid;

  /* กำหนดคอลัมน์ */
  grid-template-columns: 200px 1fr 1fr;         /* คอลัมน์ 1: 200px, 2 และ 3: แบ่งที่เหลือเท่ากัน */
  grid-template-columns: repeat(3, 1fr);        /* 3 คอลัมน์กว้างเท่ากัน */
  grid-template-columns: repeat(4, minmax(200px, 1fr)); /* อย่างน้อย 200px */
  grid-template-columns: 250px auto;            /* sidebar + main */

  /* กำหนดแถว */
  grid-template-rows: 60px 1fr 80px;   /* header, content, footer */
  grid-auto-rows: 200px;               /* แถวที่สร้างอัตโนมัติจะสูง 200px */

  /* ช่องว่าง */
  gap: 16px;
  column-gap: 20px;
  row-gap: 10px;
}

/* ===== Items ===== */
.item {
  /* กำหนดว่า item จะครอบกี่คอลัมน์/แถว */
  grid-column: 1 / 3;      /* จาก column line 1 ถึง 3 (ครอบ 2 คอลัมน์) */
  grid-column: span 2;     /* ครอบ 2 คอลัมน์ (นับจากตำแหน่งปัจจุบัน) */
  grid-column: 1 / -1;     /* ครอบทุกคอลัมน์ */

  grid-row: 1 / 3;         /* ครอบ 2 แถว */
  grid-row: span 2;
}
```

```css
/* ===== Template Area — อ่านง่ายที่สุด ===== */
.layout {
  display: grid;
  grid-template-areas:
    "header  header  header"
    "sidebar main    main"
    "footer  footer  footer";
  grid-template-columns: 250px 1fr 1fr;
  grid-template-rows: 60px 1fr 80px;
  min-height: 100vh;
  gap: 0;
}

/* กำหนดชื่อพื้นที่ให้แต่ละ element */
header  { grid-area: header; }
.sidebar{ grid-area: sidebar; }
main    { grid-area: main; }
footer  { grid-area: footer; }
```

```css
/* ===== Use Cases ===== */

/* 1. Photo gallery responsive */
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 8px;
}

/* 2. Card grid 3 คอลัมน์บน desktop, 1 คอลัมน์บน mobile */
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}
@media (max-width: 768px) {
  .cards { grid-template-columns: 1fr; }
}
```

-----

## 24. Advanced Selectors

**ใช้เมื่อ:** ต้องการเลือก element อย่างละเอียดโดยไม่ต้องเพิ่ม class ใน HTML

### Descendant Selector (เว้นวรรค) — เลือก element ลูกหลาน ไม่จำกัดความลึก

```css
/* ทุก <a> ที่อยู่ใน .nav ไม่ว่าจะซ้อนกี่ชั้น */
.nav a { color: white; }

/* ทุก <li> ที่อยู่ใน .sidebar */
.sidebar li { list-style: none; }
```

### Child Selector (`>`) — เลือกเฉพาะลูกตรงๆ ชั้นเดียว

```css
/* เฉพาะ <li> ที่เป็นลูกตรงของ .menu เท่านั้น ไม่รวม sub-menu */
.menu > li { border-bottom: 1px solid #eee; }
```

### Adjacent Sibling (`+`) — เลือก element ที่อยู่ถัดไปทันที

```css
/* <p> ที่อยู่ถัดจาก <h2> ทันที — ลบ margin บนออก */
h2 + p { margin-top: 0; }

/* label ที่อยู่หลัง input ที่ focus */
input:focus + label { color: blue; }
```

### General Sibling (`~`) — เลือก element พี่น้องทุกตัวที่อยู่ถัดไป

```css
/* ทุก <p> ที่อยู่หลัง <h2> ในกลุ่มเดียวกัน */
h2 ~ p { color: #555; }
```

### Attribute Selector — เลือกตาม attribute ของ HTML tag

```css
/* ตรงกันพอดี */
input[type="text"]     { border: 1px solid #ccc; }
input[type="checkbox"] { margin-right: 8px; }

/* เริ่มต้นด้วย */
a[href^="https"]  { color: green; }   /* link ปลอดภัย */
a[href^="mailto"] { color: orange; }  /* email link */

/* ลงท้ายด้วย */
a[href$=".pdf"]   { color: red; }     /* ไฟล์ PDF */
a[href$=".zip"]   { color: blue; }    /* ไฟล์ ZIP */

/* มีคำนี้อยู่ไหนก็ได้ */
a[href*="youtube"] { color: red; }
div[class*="col-"] { float: left; }
```

### Pseudo-class Selectors — เลือกตามสถานะหรือตำแหน่งใน DOM

```css
/* ตำแหน่งใน parent */
li:first-child  { font-weight: bold; }      /* ลูกตัวแรก */
li:last-child   { border-bottom: none; }    /* ลูกตัวสุดท้าย */
li:nth-child(2) { color: red; }             /* ลูกตัวที่ 2 */
li:nth-child(odd)  { background: #f5f5f5; } /* ลูกตัวคี่ */
li:nth-child(even) { background: white; }   /* ลูกตัวคู่ */
li:nth-child(3n+1) { color: blue; }         /* ตัวที่ 1, 4, 7, 10... */

/* สถานะ form */
input:focus    { outline: 2px solid #3498db; }
input:disabled { opacity: 0.5; cursor: not-allowed; }
input:checked  { accent-color: green; }
input:valid    { border-color: green; }
input:invalid  { border-color: red; }

/* :not() — ยกเว้น */
li:not(:last-child) { border-bottom: 1px solid #eee; }
p:not(.special) { color: #555; }
```

### Pseudo-elements — เพิ่ม/แก้เนื้อหาบางส่วนของ element

```css
/* ::before / ::after — เพิ่ม content ก่อน/หลัง element โดยไม่แก้ HTML */
.required::after {
  content: " *";
  color: red;
}

/* สร้างไอคอนหรือ decoration */
.external-link::after {
  content: " ↗";
  font-size: 0.8em;
}

/* เส้นใต้หัวข้อด้วย ::after */
h2 {
  position: relative;
  padding-bottom: 12px;
}
h2::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 50px;
  height: 3px;
  background-color: #3498db;
}

/* ::first-line / ::first-letter */
p::first-line   { font-weight: bold; }
p::first-letter { font-size: 3em; float: left; }

/* ::selection — สีเมื่อ highlight ข้อความ */
::selection {
  background-color: #3498db;
  color: white;
}
```

-----

## 25. CSS Variable

**ใช้เมื่อ:** มีค่าที่ใช้ซ้ำหลายที่ เช่น สีหลัก, ขนาด border-radius, font-size — ช่วยให้แก้ที่เดียวทั้งเว็บ

```css
/* กำหนดตัวแปรใน :root เพื่อให้ใช้ได้ทุกที่ */
:root {
  /* สี */
  --color-primary:   #3498db;
  --color-secondary: #2ecc71;
  --color-danger:    #e74c3c;
  --color-text:      #333333;
  --color-bg:        #f8f9fa;

  /* ขนาด */
  --font-size-sm: 0.875rem;  /* 14px */
  --font-size-md: 1rem;      /* 16px */
  --font-size-lg: 1.25rem;   /* 20px */
  --font-size-xl: 1.5rem;    /* 24px */

  /* spacing */
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;

  /* อื่นๆ */
  --border-radius: 8px;
  --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  --transition: all 0.3s ease;
}

/* เรียกใช้ด้วย var() */
.button {
  background-color: var(--color-primary);
  font-size: var(--font-size-md);
  padding: var(--spacing-sm) var(--spacing-md);
  border-radius: var(--border-radius);
  box-shadow: var(--shadow);
  transition: var(--transition);
}

.button-danger {
  background-color: var(--color-danger);  /* แค่เปลี่ยนสีเดียว */
}

/* fallback — ถ้าตัวแปรไม่มี จะใช้ค่า black แทน */
p { color: var(--color-text, black); }

/* Dark mode — แค่ override ตัวแปรใน :root */
@media (prefers-color-scheme: dark) {
  :root {
    --color-text: #f0f0f0;
    --color-bg:   #1a1a2e;
    --color-primary: #60a5fa;
  }
}
```

-----

## 26. Transform

**ใช้เมื่อ:** ต้องการขยับ หมุน ขยาย หรือเอียง element โดยไม่กระทบ layout รอบข้าง

```css
.box {
  /* translate — ขยับตำแหน่ง */
  transform: translateX(50px);           /* ขยับขวา 50px */
  transform: translateY(-20px);          /* ขยับขึ้น 20px */
  transform: translate(50px, -20px);     /* ขยับขวา 50px, ขึ้น 20px */
  transform: translate(-50%, -50%);      /* ขยับซ้าย-บน 50% ของตัวเอง (ใช้ centering) */

  /* scale — ขยาย/ย่อ */
  transform: scale(1.5);          /* ขยาย 1.5 เท่า */
  transform: scale(1);            /* ขนาดปกติ */
  transform: scale(0.8);          /* ย่อ 80% */
  transform: scale(2, 0.5);       /* กว้าง 2 เท่า, สูง 0.5 เท่า */

  /* rotate — หมุน */
  transform: rotate(45deg);       /* หมุนตามเข็ม 45 องศา */
  transform: rotate(-90deg);      /* หมุนทวนเข็ม 90 องศา */
  transform: rotate(0.5turn);     /* หมุนครึ่งรอบ */

  /* skew — เอียง */
  transform: skewX(20deg);        /* เอียงแนวนอน */
  transform: skewY(10deg);        /* เอียงแนวตั้ง */

  /* รวมหลาย transform — ลำดับสำคัญ! */
  transform: translateX(100px) rotate(45deg) scale(1.2);

  /* จุดหมุน/ขยาย */
  transform-origin: center;       /* default */
  transform-origin: top left;     /* หมุนรอบมุมซ้ายบน */
  transform-origin: 50% 100%;     /* หมุนรอบกึ่งกลางด้านล่าง */
}
```

```css
/* ===== Use Cases ===== */

/* hover effect — card ยกขึ้น */
.card {
  transition: transform 0.3s ease;
}
.card:hover {
  transform: translateY(-8px);
}

/* icon หมุน 90 องศาเมื่อ dropdown เปิด */
.arrow { transition: transform 0.3s; }
.open .arrow { transform: rotate(90deg); }

/* centering แนวตั้ง-นอน ด้วย position + transform */
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

-----

## 27. Transition

**ใช้เมื่อ:** ต้องการให้การเปลี่ยน style ค่อยๆ เปลี่ยน แทนที่จะเปลี่ยนพรวดเดียว

Transition บอกว่า “เมื่อ property นี้เปลี่ยน ให้ใช้เวลา X วินาที”

```css
.button {
  background-color: #3498db;
  color: white;
  padding: 12px 24px;
  border-radius: 6px;

  /* transition: property | duration | timing-function | delay */
  transition: background-color 0.3s ease;

  /* หลาย property */
  transition:
    background-color 0.3s ease,
    transform 0.2s ease-out,
    box-shadow 0.3s ease;

  /* all = ทุก property ที่เปลี่ยน */
  transition: all 0.3s ease;
}

.button:hover {
  background-color: #2980b9;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}
```

### Timing Functions — ความเร็วในแต่ละช่วง

|ค่า                         |พฤติกรรม             |เหมาะกับ              |
|---------------------------|--------------------|---------------------|
|`linear`                   |ความเร็วคงที่ตลอด      |spinner, loading bar |
|`ease`                     |เร็วตรงกลาง ช้าต้น-ปลาย|ทั่วไป (default)       |
|`ease-in`                  |ช้าตอนต้น → เร็วขึ้น     |element ที่ออกจากหน้า   |
|`ease-out`                 |เร็วตอนต้น → ช้าลง     |element ที่เข้ามาในหน้า  |
|`ease-in-out`              |ช้า → เร็ว → ช้า       |dialog, modal        |
|`cubic-bezier(x1,y1,x2,y2)`|กำหนดเอง             |spring effect, bounce|

```css
/* cubic-bezier — ใช้ https://cubic-bezier.com ช่วยสร้าง */
.spring {
  transition: transform 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

-----

## 28. CSS Animation & @keyframes

**ใช้เมื่อ:** ต้องการ animation ที่ซับซ้อนกว่า transition เช่น เล่นอัตโนมัติ วนซ้ำ หรือมีหลาย step

Transition เปลี่ยนค่าจาก A → B เมื่อมีเหตุ  
Animation กำหนด step เองได้ และเล่นอัตโนมัติ

```css
/* 1. กำหนด keyframes (ลำดับของ animation) */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-20px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.05); }
  100% { transform: scale(1); }
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

@keyframes slideIn {
  0%   { transform: translateX(-100%); opacity: 0; }
  100% { transform: translateX(0);     opacity: 1; }
}

/* 2. ใช้งาน animation */
.box {
  animation-name: fadeIn;                /* ชื่อ keyframes */
  animation-duration: 0.5s;             /* ระยะเวลา */
  animation-timing-function: ease-out;  /* timing function */
  animation-delay: 0.2s;               /* รอ 0.2s ก่อนเริ่ม */
  animation-iteration-count: 1;         /* จำนวนรอบ (infinite = ไม่สิ้นสุด) */
  animation-direction: normal;          /* normal | reverse | alternate */
  animation-fill-mode: forwards;        /* หลังจบ animation จะค้างค่าสุดท้ายไว้ */

  /* shorthand: name duration timing delay count direction fill */
  animation: fadeIn 0.5s ease-out 0.2s 1 normal forwards;
}
```

```css
/* ===== Use Cases ===== */

/* 1. Loading spinner */
.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid #f3f3f3;
  border-top-color: #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

/* 2. Notification badge กระพริบ */
.badge {
  animation: pulse 2s ease-in-out infinite;
}

/* 3. หน้าเว็บ fade in เมื่อโหลด */
.page-content {
  animation: fadeIn 0.6s ease-out;
}

/* 4. Stagger — หลาย element ทยอยปรากฏ */
.item:nth-child(1) { animation: fadeIn 0.5s ease-out 0.0s both; }
.item:nth-child(2) { animation: fadeIn 0.5s ease-out 0.1s both; }
.item:nth-child(3) { animation: fadeIn 0.5s ease-out 0.2s both; }
```

-----

## 29. หัวข้อเพิ่มเติมที่ต้องรู้

### calc() — คำนวณค่า CSS แบบ dynamic

**ใช้เมื่อ:** ต้องการผสมหน่วยต่างกันในการคำนวณ เช่น `100% - 250px`

```css
/* ตัวอย่างที่ทำไม่ได้ด้วยค่าปกติ */
.main-content {
  width: calc(100% - 250px);      /* ลบความกว้าง sidebar ออก */
  height: calc(100vh - 60px);     /* ลบความสูง navbar ออก */
}

.grid-item {
  width: calc(33.33% - 16px);     /* 1/3 ลบ gap ออก */
}

h1 {
  font-size: calc(16px + 2vw);    /* ฟอนต์ที่ scale ตาม viewport */
}

/* รองรับ + - * / */
.box {
  padding: calc(var(--spacing) * 2);
  margin: calc(50% - 150px);
}
```

-----

### object-fit — ควบคุมการแสดงรูปใน container ที่กำหนดขนาดไว้

**ใช้เมื่อ:** ใส่รูปลง card/thumbnail แต่ไม่อยากให้รูปบิดเบี้ยว

```css
/* ปัญหา: รูปขนาดต่างๆ ใน card ขนาดเดียวกัน */
.card-img {
  width: 100%;
  height: 200px;               /* กำหนดความสูงตายตัว */
  object-fit: cover;           /* ตัดรูปให้พอดี รักษาสัดส่วน (ใช้บ่อยที่สุด) */
  object-fit: contain;         /* ย่อรูปให้เห็นทั้งหมด อาจมีพื้นที่ว่าง */
  object-fit: fill;            /* ยืดรูปให้เต็ม อาจบิดเบี้ยว */
  object-fit: none;            /* แสดงรูปขนาดจริง */
  object-fit: scale-down;      /* เล็กกว่าระหว่าง contain กับ none */

  /* กำหนดจุดโฟกัสของรูป */
  object-position: center;     /* default */
  object-position: top;        /* แสดงส่วนบน (ใช้กับรูปคน — เห็นหน้า) */
  object-position: 20% 30%;
}
```

-----

### filter — เอฟเฟกต์กรองรูปภาพแบบ CSS

**ใช้เมื่อ:** ต้องการเพิ่ม effect ให้รูปโดยไม่ต้องแก้ไฟล์รูป หรือทำ hover effect

```css
img {
  filter: blur(4px);              /* เบลอ */
  filter: brightness(0.7);        /* มืดลง (< 1 มืด, > 1 สว่าง) */
  filter: contrast(150%);         /* เพิ่ม contrast */
  filter: grayscale(100%);        /* ขาว-ดำ */
  filter: sepia(80%);             /* โทนน้ำตาล ย้อนยุค */
  filter: saturate(200%);         /* เพิ่มความเข้มสี */
  filter: hue-rotate(90deg);      /* หมุนโทนสี */
  filter: invert(100%);           /* สีกลับ */
  filter: drop-shadow(4px 4px 8px rgba(0,0,0,0.3)); /* เงาตาม shape */

  /* รวมหลาย filter */
  filter: brightness(1.1) contrast(110%) saturate(120%);
}

/* hover effect ยอดนิยม */
.card img {
  filter: grayscale(100%);
  transition: filter 0.3s;
}
.card:hover img {
  filter: grayscale(0%);     /* คืนสีเมื่อ hover */
}
```

-----

### pointer-events — ควบคุมการรับ event ของเมาส์

**ใช้เมื่อ:** ต้องการให้คลิกทะลุผ่าน element ที่ซ้อนอยู่ด้านบน

```css
/* overlay ที่ไม่บล็อกการคลิก element ข้างใน */
.decorative-overlay {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  pointer-events: none;   /* เมาส์ทะลุผ่านได้ */
}

/* ปิดการคลิกชั่วคราว เช่น ระหว่าง loading */
.button.loading {
  pointer-events: none;
  opacity: 0.7;
}

/* กลับมาปกติ */
.button { pointer-events: auto; }
```

-----

### Gradient — ไล่สีขั้นสูง

**ใช้เมื่อ:** ต้องการพื้นหลังที่สวยงามโดยไม่ใช้รูปภาพ

```css
.box {
  /* Linear Gradient — ไล่สีเป็นเส้นตรง */
  background: linear-gradient(to right, #f093fb, #f5576c);        /* ซ้ายไปขวา */
  background: linear-gradient(to bottom, #4facfe, #00f2fe);       /* บนลงล่าง */
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);  /* เฉียง + จุดหยุดสี */
  background: linear-gradient(to right, red, yellow, green);      /* หลายสี */

  /* Radial Gradient — ไล่สีจากจุดศูนย์กลาง */
  background: radial-gradient(circle, #f7971e, #ffd200);
  background: radial-gradient(ellipse at top left, #a18cd1, #fbc2eb);

  /* Conic Gradient — ไล่สีแบบกรวย (CSS ใหม่) */
  background: conic-gradient(red, yellow, green, blue, red);  /* วงสี */
  background: conic-gradient(from 0deg at 50% 50%, #f093fb, #f5576c);

  /* Gradient บน background-image */
  background:
    linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
    url('hero.jpg') center/cover;  /* overlay สีดำทับรูป */
}
```

-----

### Scrollbar Styling — ปรับแต่งหน้าตา scrollbar

**ใช้เมื่อ:** ต้องการให้ scrollbar เข้ากับ design ของเว็บ

```css
/* Chrome, Safari, Edge (Chromium) */
::-webkit-scrollbar {
  width: 8px;          /* ความกว้าง scrollbar แนวตั้ง */
  height: 8px;         /* ความสูง scrollbar แนวนอน */
}
::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 4px;
}
::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
  background: #555;
}

/* Firefox */
* {
  scrollbar-width: thin;           /* auto | thin | none */
  scrollbar-color: #888 #f1f1f1;  /* thumb track */
}

/* ซ่อน scrollbar แต่ยัง scroll ได้ */
.hide-scrollbar {
  -ms-overflow-style: none;   /* IE */
  scrollbar-width: none;      /* Firefox */
}
.hide-scrollbar::-webkit-scrollbar {
  display: none;              /* Chrome, Safari */
}
```

-----

### scroll-behavior — Smooth Scroll

**ใช้เมื่อ:** ต้องการให้การ scroll ไปยัง anchor (`#section`) ค่อยๆ เลื่อนแทนที่จะกระโดด

```css
/* ใส่ใน html เพื่อให้ทุก scroll ในหน้าเป็นแบบ smooth */
html {
  scroll-behavior: smooth;
}

/* กำหนดเฉพาะ element */
.chat-container {
  overflow-y: auto;
  scroll-behavior: smooth;
}
```

```html
<!-- คลิก link แล้ว scroll ลงไปยัง #about แบบ smooth -->
<a href="#about">เกี่ยวกับเรา</a>
<section id="about">...</section>
```

-----

### aspect-ratio — รักษาสัดส่วนอัตโนมัติ

**ใช้เมื่อ:** ต้องการให้กล่อง/รูปรักษา aspect ratio เมื่อขนาดเปลี่ยน

```css
/* วิดีโอ responsive — เมื่อ width เปลี่ยน height จะปรับตาม 16:9 อัตโนมัติ */
.video-wrapper {
  width: 100%;
  aspect-ratio: 16 / 9;
}

/* thumbnail สี่เหลี่ยมจัตุรัสเสมอ */
.thumbnail {
  width: 100%;
  aspect-ratio: 1 / 1;     /* หรือเขียนว่า aspect-ratio: 1 */
  object-fit: cover;
}

/* Card profile ที่รูปต้องเป็น 4:3 */
.profile-img {
  width: 200px;
  aspect-ratio: 4 / 3;
}
```

-----

### clamp() — ขนาดที่ responsive โดยไม่ต้องใช้ Media Query

**ใช้เมื่อ:** ต้องการให้ค่าอยู่ระหว่างขั้นต่ำและสูงสุด และ scale ตาม viewport อัตโนมัติ

```css
/* clamp(min, preferred, max) */
h1 {
  /* ไม่ต่ำกว่า 1.5rem, ไม่เกิน 3rem, ปรับตาม 4vw */
  font-size: clamp(1.5rem, 4vw, 3rem);
  /* บนจอ 375px:  4vw = 15px → ใช้ min 1.5rem (24px)  */
  /* บนจอ 768px:  4vw = 30.7px → ใช้ 30.7px            */
  /* บนจอ 1440px: 4vw = 57.6px → ใช้ max 3rem (48px)   */
}

.container {
  /* กว้างอย่างน้อย 320px, ไม่เกิน 1200px */
  width: clamp(320px, 90%, 1200px);
}

.card {
  padding: clamp(12px, 3%, 32px);
}
```

-----

### Sass / SCSS — CSS Preprocessor

**ใช้เมื่อ:** โปรเจกต์ใหญ่ที่ต้องการจัดการ CSS ได้ดีขึ้น — ต้อง compile เป็น CSS ก่อนใช้

> ต้องติดตั้ง `npm install -g sass` ก่อน

```scss
// 1. ตัวแปร (เหมือน CSS Variable แต่เขียนง่ายกว่า)
$primary: #3498db;
$font-base: 16px;
$radius: 8px;

// 2. Nesting — เขียน CSS ซ้อนกันตาม HTML structure
.card {
  padding: 20px;
  border-radius: $radius;

  // เทียบเท่า .card:hover
  &:hover {
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }

  // เทียบเท่า .card .title
  .title {
    font-size: 1.25rem;
    color: $primary;
  }

  // เทียบเท่า .card--featured
  &--featured {
    border-left: 4px solid $primary;
  }
}

// 3. Mixin — โค้ดที่ใช้ซ้ำได้
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

@mixin respond-to($breakpoint) {
  @if $breakpoint == mobile {
    @media (max-width: 768px) { @content; }
  } @else if $breakpoint == desktop {
    @media (min-width: 1024px) { @content; }
  }
}

// 4. เรียกใช้ mixin
.hero {
  @include flex-center;
  height: 100vh;

  @include respond-to(mobile) {
    height: auto;
    padding: 40px;
  }
}

// 5. Function
@function rem($px) {
  @return $px / 16px * 1rem;
}
h1 { font-size: rem(32px); }  // → 2rem
```

-----

### CSS Reset & Normalize — เริ่มต้นด้วยฐานที่สม่ำเสมอ

**ใช้เมื่อ:** ต้องการลบ style เริ่มต้นของ browser ที่แตกต่างกันในแต่ละ browser

```css
/* Modern CSS Reset — ใส่ไว้ต้นไฟล์ CSS เสมอ */
*, *::before, *::after {
  box-sizing: border-box;     /* ขนาดรวม padding และ border */
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
  font-size: 16px;
}

body {
  font-family: system-ui, -apple-system, sans-serif;
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;  /* font เรียบบน Mac */
  color: #333;
}

/* รูปและ media ไม่เกิน container */
img, video, svg, canvas {
  max-width: 100%;
  display: block;
}

/* form element ใช้ฟอนต์เดียวกับ body */
input, button, textarea, select {
  font: inherit;
}

/* ลบ list style */
ul, ol { list-style: none; }

/* ลบ underline link */
a { text-decoration: none; color: inherit; }

/* p ที่ไม่มี class มี line-height มากขึ้น */
p:not([class]) {
  line-height: 1.7;
}
```

-----

## 🔗 แหล่งเรียนรู้เพิ่มเติม

|แหล่ง                                                            |เนื้อหา                             |
|----------------------------------------------------------------|----------------------------------|
|[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS)|อ้างอิง CSS ที่ครบที่สุด                 |
|[CSS-Tricks](https://css-tricks.com)                            |บทความและ guide เชิงปฏิบัติ           |
|[Flexbox Froggy](https://flexboxfroggy.com)                     |เกมฝึก Flexbox                     |
|[Grid Garden](https://cssgridgarden.com)                        |เกมฝึก CSS Grid                    |
|[Can I Use](https://caniuse.com)                                |เช็คว่า browser รองรับ property นั้นไหม|
|[cubic-bezier.com](https://cubic-bezier.com)                    |สร้าง timing function แบบ custom   |
|[CSS Gradient](https://cssgradient.io)                          |สร้าง gradient ด้วย visual editor   |

-----

*สรุปจากเอกสาร CSS เบื้องต้น (2020) — เพิ่มเติมหัวข้อสำคัญและคำอธิบายการใช้งานจริง*