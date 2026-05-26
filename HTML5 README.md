# 📄 HTML5 เบื้องต้น — สรุปครบจบในที่เดียว

> อ้างอิงจากเอกสาร HTML5 เบื้องต้น ฉบับปรับปรุง 2020

-----

## 📌 สารบัญ

1. [HTML คืออะไร](#1-html-คืออะไร)
1. [การสร้างไฟล์ HTML](#2-การสร้างไฟล์-html)
1. [DOCTYPE](#3-doctype)
1. [Character Encoding](#4-character-encoding)
1. [โครงสร้างภาษา HTML](#5-โครงสร้างภาษา-html)
1. [HTML Element & Attribute](#6-html-element--attribute)
1. [Comment](#7-comment)
1. [Heading (หัวเรื่อง)](#8-heading-หัวเรื่อง)
1. [Paragraph](#9-paragraph)
1. [แท็กจัดรูปแบบข้อความ](#10-แท็กจัดรูปแบบข้อความ)
1. [Line Break & Horizontal Rule](#11-line-break--horizontal-rule)
1. [รูปภาพ (Images)](#12-รูปภาพ-images)
1. [ลิงก์ (Hyperlink)](#13-ลิงก์-hyperlink)
1. [Lists (รายการ)](#14-lists-รายการ)
1. [Table (ตาราง)](#15-table-ตาราง)
1. [div & span](#16-div--span)
1. [HTML Form](#17-html-form)
1. [Block vs Inline](#18-block-vs-inline)
1. [Class & ID](#19-class--id)
1. [Semantic Tag](#20-semantic-tag)
1. [Character Entity](#21-character-entity)
1. [CSS เบื้องต้น *(เพิ่มเติม)*](#22-css-เบื้องต้น-เพิ่มเติม)
1. [JavaScript เบื้องต้น *(เพิ่มเติม)*](#23-javascript-เบื้องต้น-เพิ่มเติม)
1. [Meta Tags ที่ควรรู้ *(เพิ่มเติม)*](#24-meta-tags-ที่ควรรู้-เพิ่มเติม)
1. [Responsive Web (Viewport) *(เพิ่มเติม)*](#25-responsive-web-viewport-เพิ่มเติม)

-----

## 1. HTML คืออะไร

**HTML** (HyperText Markup Language) คือภาษาที่ใช้สร้างเว็บเพจ โดยใช้ **Markup Tag** เพื่อควบคุมการแสดงผลข้อมูล รูปภาพ และวัตถุต่างๆ ผ่าน Web Browser เช่น Chrome, Firefox, Safari, Edge

- แต่ละ Tag มี **Attribute** เพื่อควบคุมการทำงาน
- ไฟล์ HTML มีนามสกุล `.html`

-----

## 2. การสร้างไฟล์ HTML

ต้องใช้ **Text Editor** เช่น VS Code, Notepad++, Sublime Text แล้วบันทึกไฟล์ด้วยนามสกุล `.html`

-----

## 3. DOCTYPE

ประกาศมาตรฐานที่เว็บเพจอ้างอิง ต้องเขียนเป็นบรรทัดแรกของไฟล์เสมอ

```html
<!-- HTML5 (แนะนำ) -->
<!DOCTYPE html>

<!-- HTML 4.01 -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">

<!-- XHTML 1.1 -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "">
```

-----

## 4. Character Encoding

กำหนดรูปแบบการเข้ารหัสอักขระด้วยแท็ก `<meta>` เพื่อให้แสดงภาษาไทยได้ถูกต้อง

```html
<meta charset="utf-8">
<!-- หรือ -->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
```

-----

## 5. โครงสร้างภาษา HTML

HTML แบ่งออกเป็น 2 ส่วนหลัก คือ **head** และ **body**

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="utf-8">
    <title>ชื่อเว็บเพจ</title>
  </head>
  <body>
    <!-- เนื้อหาหลักของเว็บ -->
    <h1>สวัสดีโลก</h1>
    <p>นี่คือเนื้อหาของเว็บ</p>
  </body>
</html>
```

|ส่วน |แท็ก               |หน้าที่                                    |
|----|------------------|----------------------------------------|
|Head|`<head>...</head>`|อธิบายข้อมูลเว็บ เช่น title, keywords, author|
|Body|`<body>...</body>`|เนื้อหาหลัก ข้อความ รูปภาพ ฟอร์ม วิดีโอ         |

-----

## 6. HTML Element & Attribute

โครงสร้างของ Element คือ `<แท็กเปิด>เนื้อหา</แท็กปิด>`

```html
<!-- Element ปกติ -->
<h1>หัวข้อเรื่อง</h1>

<!-- Element พร้อม Attribute -->
<a href="https://www.google.com">เข้าสู่เว็บไซต์</a>

<!-- Element แบบไม่มีแท็กปิด (Self-closing) -->
<br />
<img src="image.jpg" alt="รูปภาพ" />
```

-----

## 7. Comment

ข้อความอธิบายโค้ดที่จะไม่ถูกแสดงผลในเบราว์เซอร์

```html
<!-- นี่คือ Comment ใช้อธิบายโค้ด -->

<!-- 
  Comment หลายบรรทัด
  บรรทัดที่สอง
-->
```

-----

## 8. Heading (หัวเรื่อง)

มี 6 ระดับ `<h1>` ใหญ่สุด → `<h6>` เล็กสุด

```html
<h1>หัวข้อระดับ 1 (ใหญ่สุด)</h1>
<h2>หัวข้อระดับ 2</h2>
<h3>หัวข้อระดับ 3</h3>
<h4>หัวข้อระดับ 4</h4>
<h5>หัวข้อระดับ 5</h5>
<h6>หัวข้อระดับ 6 (เล็กสุด)</h6>
```

-----

## 9. Paragraph

แสดงข้อมูลเป็นย่อหน้า โดยจะขึ้นบรรทัดใหม่โดยอัตโนมัติ

```html
<p>นี่คือย่อหน้าแรก</p>
<p>นี่คือย่อหน้าที่สอง จะแยกออกจากย่อหน้าแรกโดยอัตโนมัติ</p>
```

-----

## 10. แท็กจัดรูปแบบข้อความ

```html
<p>ข้อความ<strong>ตัวหนา (มีความสำคัญ)</strong></p>
<p>ข้อความ<b>ตัวหนา</b></p>
<p>ข้อความ<i>ตัวเอียง</i></p>
<p>ข้อความ<em>ตัวเอียง (เน้นย้ำ)</em></p>
<p>ข้อความ<small>ตัวเล็ก</small></p>
<p>ข้อความ<u>ขีดเส้นใต้</u></p>
<p>ข้อความ<del>ขีดฆ่า</del></p>
<p>ข้อความ<mark>ไฮไลต์</mark></p>
<p>H<sub>2</sub>O  (subscript)</p>
<p>x<sup>2</sup>   (superscript)</p>
```

-----

## 11. Line Break & Horizontal Rule

```html
<!-- ขึ้นบรรทัดใหม่ -->
<p>บรรทัดแรก<br />บรรทัดที่สอง</p>

<!-- เส้นคั่นแนวนอน -->
<hr>
```

-----

## 12. รูปภาพ (Images)

```html
<!-- รูปภาพในโฟลเดอร์เดียวกัน (Internal) -->
<img src="photo.jpg" alt="คำอธิบายรูป" width="300" height="200">

<!-- รูปภาพจาก URL (External) -->
<img src="https://example.com/image.png" alt="รูปภาพจากอินเทอร์เน็ต" width="300">

<!-- ใส่ลิงก์ให้รูปภาพ -->
<a href="https://www.google.com">
  <img src="photo.jpg" alt="คลิกที่รูป">
</a>
```

|Attribute|ความหมาย               |
|---------|-----------------------|
|`src`    |ที่อยู่ของไฟล์รูปภาพ         |
|`alt`    |ข้อความแสดงเมื่อโหลดรูปไม่ได้|
|`width`  |ความกว้าง (px หรือ %)    |
|`height` |ความสูง (px หรือ %)      |

-----

## 13. ลิงก์ (Hyperlink)

```html
<!-- ลิงก์ปกติ -->
<a href="https://www.google.com">ไปที่ Google</a>

<!-- เปิดในแท็บใหม่ -->
<a href="https://www.google.com" target="_blank">เปิดแท็บใหม่</a>

<!-- ลิงก์ไปยังหน้าในเว็บเดียวกัน -->
<a href="about.html">เกี่ยวกับเรา</a>

<!-- ลิงก์ไปยัง ID ในหน้าเดียวกัน (Anchor) -->
<a href="#section1">ไปที่ Section 1</a>

<!-- ลิงก์อีเมล -->
<a href="mailto:example@email.com">ส่งอีเมล</a>

<!-- ลิงก์โทรศัพท์ -->
<a href="tel:0812345678">โทร 081-234-5678</a>
```

-----

## 14. Lists (รายการ)

### Ordered List (รายการตัวเลข)

```html
<ol type="1">   <!-- 1, 2, 3 -->
  <li>รายการที่ 1</li>
  <li>รายการที่ 2</li>
  <li>รายการที่ 3</li>
</ol>

<!-- type="A" → A, B, C -->
<!-- type="a" → a, b, c -->
<!-- type="I" → I, II, III -->
```

### Unordered List (รายการสัญลักษณ์)

```html
<ul type="disc">   <!-- จุดสีดำ (ค่าเริ่มต้น) -->
  <li>รายการที่ 1</li>
  <li>รายการที่ 2</li>
</ul>

<!-- type="circle"  → วงกลมโปร่ง -->
<!-- type="square"  → สี่เหลี่ยม -->
```

### Nested List (รายการซ้อน)

```html
<ul>
  <li>ผลไม้
    <ul>
      <li>แอปเปิ้ล</li>
      <li>กล้วย</li>
    </ul>
  </li>
  <li>ผัก</li>
</ul>
```

-----

## 15. Table (ตาราง)

```html
<table border="1" width="100%" cellpadding="5" cellspacing="0">
  <thead>
    <tr>
      <th>ชื่อ</th>
      <th>อายุ</th>
      <th>เมือง</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>สมชาย</td>
      <td>25</td>
      <td>กรุงเทพ</td>
    </tr>
    <tr>
      <td>สมหญิง</td>
      <td>30</td>
      <td>เชียงใหม่</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">ข้อมูล ณ วันที่ 2024</td>
    </tr>
  </tfoot>
</table>
```

### Attribute สำคัญของ Table

|Attribute    |ความหมาย                   |
|-------------|---------------------------|
|`border`     |ความหนาเส้นขอบ              |
|`width`      |ความกว้าง (%)               |
|`bgcolor`    |สีพื้นหลัง                     |
|`colspan`    |รวมคอลัมน์                   |
|`rowspan`    |รวมแถว                     |
|`align`      |จัดตำแหน่ง (left/center/right)|
|`cellpadding`|ช่องว่างภายในเซลล์            |
|`cellspacing`|ช่องว่างระหว่างเซลล์           |

-----

## 16. div & span

```html
<!-- div: Block element — ขึ้นบรรทัดใหม่ -->
<div style="background-color: lightblue; padding: 10px;">
  <h2>หัวข้อ</h2>
  <p>เนื้อหาในกล่อง div</p>
</div>

<!-- span: Inline element — ไม่ขึ้นบรรทัดใหม่ -->
<p>ข้อความปกติ <span style="color: red;">ข้อความสีแดง</span> ข้อความต่อ</p>
```

-----

## 17. HTML Form

```html
<form action="submit.php" method="POST">

  <!-- Text Input -->
  <label for="name">ชื่อ:</label>
  <input type="text" id="name" name="name" placeholder="กรอกชื่อ">
  <br>

  <!-- Email -->
  <label for="email">อีเมล:</label>
  <input type="email" id="email" name="email">
  <br>

  <!-- Password -->
  <label for="pass">รหัสผ่าน:</label>
  <input type="password" id="pass" name="password">
  <br>

  <!-- Radio Button -->
  <label>เพศ:</label>
  <input type="radio" name="gender" value="male"> ชาย
  <input type="radio" name="gender" value="female"> หญิง
  <br>

  <!-- Checkbox -->
  <input type="checkbox" name="agree" value="yes"> ยอมรับเงื่อนไข
  <br>

  <!-- Dropdown -->
  <label for="city">จังหวัด:</label>
  <select id="city" name="city">
    <option value="bkk">กรุงเทพ</option>
    <option value="cnx">เชียงใหม่</option>
    <option value="hkt">ภูเก็ต</option>
  </select>
  <br>

  <!-- Textarea -->
  <label for="msg">ข้อความ:</label>
  <textarea id="msg" name="message" rows="4" cols="40"></textarea>
  <br>

  <!-- Submit Button -->
  <button type="submit">ส่งข้อมูล</button>
  <button type="reset">ล้างข้อมูล</button>

</form>
```

### Input Types ใน HTML5

```html
<input type="text">
<input type="email">
<input type="password">
<input type="number" min="1" max="100">
<input type="date">
<input type="time">
<input type="color">
<input type="range" min="0" max="100">
<input type="search">
<input type="url">
<input type="tel">
<input type="file">
```

-----

## 18. Block vs Inline

|ประเภท    |ลักษณะ                          |ตัวอย่าง                                           |
|----------|-------------------------------|-------------------------------------------------|
|**Block** |ความกว้างเต็มบรรทัด ขึ้นบรรทัดใหม่เสมอ|`<div>`, `<p>`, `<h1>`-`<h6>`, `<ul>`, `<table>` |
|**Inline**|ความกว้างตามเนื้อหา ไม่ขึ้นบรรทัดใหม่  |`<span>`, `<a>`, `<img>`, `<b>`, `<i>`, `<input>`|

-----

## 19. Class & ID

```html
<!-- Class: ใช้ซ้ำได้หลายครั้ง เรียกด้วย . ใน CSS -->
<p class="highlight">ย่อหน้าที่ 1</p>
<p class="highlight">ย่อหน้าที่ 2</p>

<!-- ID: ใช้ได้ครั้งเดียวในหน้า เรียกด้วย # ใน CSS -->
<div id="main-content">เนื้อหาหลัก</div>

<!-- ใช้ร่วมกันได้ -->
<div id="header" class="container dark-bg">ส่วนหัว</div>
```

-----

## 20. Semantic Tag

แท็กที่มีความหมายชัดเจน ช่วยให้โครงสร้าง HTML อ่านเข้าใจง่ายและดีต่อ SEO

```html
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8">
  <title>My Website</title>
</head>
<body>

  <header>
    <h1>โลโก้ / ชื่อเว็บ</h1>
  </header>

  <nav>
    <a href="index.html">หน้าแรก</a>
    <a href="about.html">เกี่ยวกับ</a>
    <a href="contact.html">ติดต่อ</a>
  </nav>

  <main>
    <article>
      <h2>บทความที่ 1</h2>
      <section>
        <h3>หัวข้อย่อย</h3>
        <p>เนื้อหา...</p>
      </section>
    </article>

    <aside>
      <p>เมนูด้านข้าง / โฆษณา</p>
    </aside>
  </main>

  <footer>
    <p>© 2024 My Website. All rights reserved.</p>
  </footer>

</body>
</html>
```

|Tag        |ความหมาย        |
|-----------|----------------|
|`<header>` |ส่วนหัวของเว็บ     |
|`<nav>`    |เมนูนำทาง         |
|`<main>`   |เนื้อหาหลัก        |
|`<article>`|บทความ/เนื้อหาอิสระ|
|`<section>`|กลุ่มหัวข้อย่อย      |
|`<aside>`  |เนื้อหาข้างเคียง    |
|`<footer>` |ส่วนท้ายของเว็บ    |

-----

## 21. Character Entity

อักขระพิเศษที่ใช้แสดงในหน้าเว็บ

```html
<p>&lt;div&gt;  → แสดงเป็น <div> บนหน้าจอ</p>
<p>&amp;       → &</p>
<p>&quot;      → "</p>
<p>&nbsp;      → ช่องว่าง (Non-breaking space)</p>
<p>&copy;      → ©</p>
<p>&reg;       → ®</p>
<p>&trade;     → ™</p>
<p>&hearts;    → ♥</p>
<p>&larr;      → ←</p>
<p>&rarr;      → →</p>
```

-----

## 22. CSS เบื้องต้น *(เพิ่มเติม)*

CSS (Cascading Style Sheets) ใช้กำหนดสไตล์การแสดงผลของ HTML

### 3 วิธีการใช้ CSS

```html
<!-- 1. Inline CSS -->
<p style="color: red; font-size: 18px;">ข้อความสีแดง</p>

<!-- 2. Internal CSS (ใน <head>) -->
<head>
  <style>
    p {
      color: blue;
      font-family: Arial, sans-serif;
    }
    .highlight { background-color: yellow; }
    #main { width: 80%; margin: auto; }
  </style>
</head>

<!-- 3. External CSS (ไฟล์แยก) -->
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

### CSS Properties พื้นฐาน

```css
/* สี */
color: red;
background-color: #f0f0f0;

/* ฟอนต์ */
font-size: 16px;
font-weight: bold;
font-family: 'Sarabun', sans-serif;
text-align: center;

/* Box Model */
width: 300px;
height: 200px;
padding: 10px;
margin: 20px auto;
border: 1px solid black;
border-radius: 8px;

/* Display */
display: block;
display: inline;
display: flex;
display: none;
```

-----

## 23. JavaScript เบื้องต้น *(เพิ่มเติม)*

JavaScript ใช้เพิ่มการโต้ตอบให้เว็บเพจ

```html
<!-- Internal JS (ใน <body> ก่อนปิด) -->
<button onclick="sayHello()">คลิกฉัน</button>

<script>
  function sayHello() {
    alert("สวัสดี HTML5!");
  }

  // เปลี่ยนเนื้อหา Element
  document.getElementById("demo").innerHTML = "ข้อความใหม่";

  // เปลี่ยน Style
  document.getElementById("box").style.color = "red";
</script>

<!-- External JS (ไฟล์แยก) -->
<script src="script.js"></script>
```

-----

## 24. Meta Tags ที่ควรรู้ *(เพิ่มเติม)*

```html
<head>
  <!-- Charset -->
  <meta charset="UTF-8">

  <!-- คำอธิบายเว็บ (SEO) -->
  <meta name="description" content="เว็บไซต์ HTML5 เบื้องต้น">

  <!-- คีย์เวิร์ด (SEO) -->
  <meta name="keywords" content="HTML, HTML5, เว็บ, เบื้องต้น">

  <!-- ชื่อผู้เขียน -->
  <meta name="author" content="ชื่อผู้พัฒนา">

  <!-- รีเฟรชหน้าอัตโนมัติทุก 30 วินาที -->
  <meta http-equiv="refresh" content="30">

  <!-- ป้องกัน cache -->
  <meta http-equiv="Cache-Control" content="no-cache">

  <!-- ชื่อแท็บเบราว์เซอร์ -->
  <title>ชื่อหน้าเว็บ</title>

  <!-- Favicon -->
  <link rel="icon" type="image/png" href="favicon.png">
</head>
```

-----

## 25. Responsive Web (Viewport) *(เพิ่มเติม)*

ทำให้เว็บแสดงผลได้ดีบนทุกอุปกรณ์

```html
<!-- ต้องใส่ใน <head> เสมอ -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Media Query (CSS)

```css
/* สำหรับหน้าจอมือถือ */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
  .container {
    width: 100%;
    padding: 10px;
  }
}

/* สำหรับแท็บเล็ต */
@media (min-width: 769px) and (max-width: 1024px) {
  .container {
    width: 90%;
  }
}

/* สำหรับ Desktop */
@media (min-width: 1025px) {
  .container {
    width: 80%;
    margin: auto;
  }
}
```

-----

## 🗂️ ตัวอย่างโครงสร้างเว็บเพจสมบูรณ์

```html
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="เว็บตัวอย่าง HTML5">
  <title>เว็บเพจตัวอย่าง</title>
  <style>
    body { font-family: 'Sarabun', sans-serif; margin: 0; }
    header { background-color: #333; color: white; padding: 20px; }
    nav a { color: white; margin: 0 10px; text-decoration: none; }
    main { padding: 20px; max-width: 1200px; margin: auto; }
    footer { background-color: #333; color: white; text-align: center; padding: 10px; }
  </style>
</head>
<body>

  <header>
    <h1>ชื่อเว็บไซต์</h1>
    <nav>
      <a href="#">หน้าแรก</a>
      <a href="#">บทความ</a>
      <a href="#">ติดต่อ</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>บทความตัวอย่าง</h2>
      <p>เนื้อหาของบทความ...</p>
      <img src="image.jpg" alt="รูปประกอบ" width="100%">
    </article>
  </main>

  <footer>
    <p>&copy; 2024 My Website. All rights reserved.</p>
  </footer>

</body>
</html>
```

-----

> 📚 **แหล่งเรียนรู้เพิ่มเติม**
> 
> - [W3Schools HTML](https://www.w3schools.com/html/)
> - [MDN Web Docs](https://developer.mozilla.org/th/docs/Web/HTML)
> - [HTML Living Standard](https://html.spec.whatwg.org/)