# 📘 JavaScript เบื้องต้น — สรุปครบทุกหัวข้อ

> อ้างอิงจากเอกสาร *JavaScript เบื้องต้น รวมกับ HTML5 CSS3 [ฉบับปรับปรุง 2020]*  
> ⭐ หัวข้อที่มีเครื่องหมาย `[เพิ่มเติม]` คือหัวข้อที่จำเป็นต้องรู้แต่ไม่มีในไฟล์ต้นฉบับ

-----

## สารบัญ

1. [JavaScript คืออะไร](#1-javascript-คืออะไร)
1. [รูปแบบการเขียน JavaScript](#2-รูปแบบการเขียน-javascript)
1. [การแสดงข้อมูล](#3-การแสดงข้อมูล)
1. [การเขียน Comment](#4-การเขียน-comment)
1. [ตัวแปรและชนิดข้อมูล](#5-ตัวแปรและชนิดข้อมูล)
1. [Data Type](#6-data-type)
1. [การแปลงชนิดข้อมูล (Type Conversion)](#7-การแปลงชนิดข้อมูล-type-conversion)
1. [Array](#8-array)
1. [ตัวดำเนินการ (Operator)](#9-ตัวดำเนินการ-operator)
1. [โครงสร้างควบคุม (Control Structure)](#10-โครงสร้างควบคุม-control-structure)
1. [ค่า null, undefined และ NaN](#11-ค่า-null-undefined-และ-nan)
1. [ฟังก์ชัน (Function)](#12-ฟังก์ชัน-function)
1. [JavaScript Object](#13-javascript-object)
1. [HTML DOM](#14-html-dom)
1. [DOM Event และ EventListener](#15-dom-event-และ-eventlistener)
1. [JavaScript ES6+](#16-javascript-es6)
1. [Object-Oriented Programming (OOP)](#17-object-oriented-programming-oop)
1. [Promise และ Async/Await `[เพิ่มเติม]`](#18-promise-และ-asyncawait-เพิ่มเติม)
1. [การจัดการ Error `[เพิ่มเติม]`](#19-การจัดการ-error-เพิ่มเติม)
1. [Modules (import/export) `[เพิ่มเติม]`](#20-modules-importexport-เพิ่มเติม)
1. [Local Storage และ Session Storage `[เพิ่มเติม]`](#21-local-storage-และ-session-storage-เพิ่มเติม)
1. [Fetch API `[เพิ่มเติม]`](#22-fetch-api-เพิ่มเติม)

-----

## 1. JavaScript คืออะไร

JavaScript เป็นภาษาคอมพิวเตอร์ที่ใช้พัฒนาเว็บร่วมกับ HTML/CSS เพื่อให้เว็บมีลักษณะ **Dynamic** คือสามารถตอบสนองกับผู้ใช้ได้

- ทำงานฝั่งผู้ใช้ (Client-Side Script)
- Web Browser ทำหน้าที่ประมวลผลคำสั่ง
- สามารถเปลี่ยนแปลง HTML, CSS ได้
- ตรวจสอบข้อมูล (Validation) ได้
- เก็บข้อมูลผู้ใช้ได้ เช่น Cookie, Local Storage

-----

## 2. รูปแบบการเขียน JavaScript

### แบบ Internal

เขียนไว้ใน `<head>` หรือ `<body>` ของ HTML

```html
<script type="text/javascript">
  document.write("Hello World");
</script>
```

### แบบ External

แยกไว้เป็นไฟล์ `.js` และเรียกเข้ามา

```html
<script src="myscript.js"></script>
```

```js
// myscript.js
document.write("Hello from external file");
```

-----

## 3. การแสดงข้อมูล

```js
// แสดงในหน้าเว็บ
document.write("ข้อความ");

// แสดง popup แจ้งเตือน
alert("แจ้งเตือน!");

// แสดงใน Console (ใช้ debug)
console.log("ค่าที่ต้องการตรวจสอบ");
```

-----

## 4. การเขียน Comment

```js
// Comment บรรทัดเดียว

/*
  Comment
  หลายบรรทัด
*/
```

-----

## 5. ตัวแปรและชนิดข้อมูล

JavaScript ใช้ **Dynamic Typing** — ไม่ต้องประกาศชนิดข้อมูล ระบบจะกำหนดให้อัตโนมัติตามค่าที่เก็บ

### กฎการตั้งชื่อตัวแปร

- ขึ้นต้นด้วยตัวอักษร, `$`, หรือ `_`
- ห้ามขึ้นต้นด้วยตัวเลข
- Case Sensitive (`name` ≠ `Name`)
- ห้ามใช้ Reserved Keywords

### การประกาศตัวแปร

```js
// var — ขอบเขต function scope (เก่า)
var name = "สมชาย";

// let — ขอบเขต block scope (แนะนำ)
let age = 25;
let x, y, z;
let a = 1, b = 2, c = 3;

// const — ค่าคงที่ เปลี่ยนไม่ได้
const PI = 3.14159;
```

### typeof — ตรวจสอบชนิดข้อมูล

```js
let x = 42;
console.log(typeof x);       // "number"
console.log(typeof "hello"); // "string"
console.log(typeof true);    // "boolean"
```

-----

## 6. Data Type

|ชนิดข้อมูล    |คำอธิบาย                  |ตัวอย่าง                 |
|-----------|------------------------|-----------------------|
|`boolean`  |ค่าจริง/เท็จ               |`true`, `false`        |
|`number`   |ตัวเลขทั้งจำนวนเต็มและทศนิยม  |`20`, `30.15`          |
|`string`   |ข้อความ                  |`"kongruksiam"`        |
|`object`   |ข้อมูลเชิงวัตถุ              |`{name:"kong", age:20}`|
|`array`    |ชุดข้อมูล                  |`["มะม่วง", "ส้ม"]`      |
|`undefined`|ตัวแปรที่ประกาศแต่ยังไม่กำหนดค่า|`let x;`               |
|`null`     |ไม่มีค่า (กำหนดโดยผู้เขียน)    |`let x = null;`        |

```js
let num = 10;          // number
let price = 99.99;     // number (float)
let str = "hello";     // string
let flag = true;       // boolean
let obj = { name: "kong" }; // object
let arr = [1, 2, 3];  // array
```

-----

## 7. การแปลงชนิดข้อมูล (Type Conversion)

```js
// String → Number
let a = parseInt("42");       // 42 (จำนวนเต็ม)
let b = parseFloat("3.14");   // 3.14 (ทศนิยม)
let c = +"100";               // 100 (ใช้เครื่องหมาย +)

// Number → String
let n = 100;
let s1 = "" + n;              // "100"
let s2 = n.toString();        // "100"
```

-----

## 8. Array

### การสร้าง Array

```js
// วิธีที่ 1: ใช้ Array()
let days = Array("จันทร์", "อังคาร", "พุธ");

// วิธีที่ 2: ใช้ [] (แนะนำ)
let colors = ["แดง", "น้ำเงิน", "เหลือง"];
```

### การเข้าถึงสมาชิก

```js
let colors = ["แดง", "น้ำเงิน", "เหลือง"];
console.log(colors[0]);  // แดง
console.log(colors[1]);  // น้ำเงิน

let first = colors[0];
let last = colors[colors.length - 1];
```

### Array Methods ที่ใช้บ่อย

```js
let fruits = ["ส้ม", "องุ่น", "มะม่วง"];

fruits.length;          // 3 — จำนวนสมาชิก
fruits.push("แอปเปิ้ล"); // เพิ่มท้าย
fruits.pop();           // เอาตัวท้ายออก
fruits.sort();          // เรียงตัวอักษร
fruits.reverse();       // กลับลำดับ
fruits.toString();      // แปลงเป็น string
fruits.join(" | ");     // รวมเป็น string ด้วยตัวคั่น

// รวม Array
let vegs = ["คะน้า", "ผักชี"];
let all = fruits.concat(vegs);

// วนลูปด้วย forEach
fruits.forEach(function(item) {
  console.log(item);
});

// เรียงตัวเลขจากน้อยไปมาก
let nums = [20, 100, -5, 10];
nums.sort((a, b) => a - b);

// เรียงตัวเลขจากมากไปน้อย
nums.sort((a, b) => b - a);
```

-----

## 9. ตัวดำเนินการ (Operator)

### คณิตศาสตร์

```js
let a = 10, b = 3;
console.log(a + b);  // 13
console.log(a - b);  // 7
console.log(a * b);  // 30
console.log(a / b);  // 3.333...
console.log(a % b);  // 1 (เศษจากการหาร)
```

### เปรียบเทียบ (คืนค่า boolean)

```js
5 == "5"   // true  (เปรียบค่าอย่างเดียว)
5 === "5"  // false (เปรียบทั้งค่าและชนิด — แนะนำ)
5 != 3     // true
5 > 3      // true
5 < 3      // false
5 >= 5     // true
5 <= 4     // false
```

### ตรรกศาสตร์

```js
true && false  // false (AND)
true || false  // true  (OR)
!true          // false (NOT)
```

### เพิ่มค่า / ลดค่า

```js
let x = 5;
x++;  // x = 6 (postfix — ใช้ค่าก่อน แล้วค่อยเพิ่ม)
++x;  // x = 7 (prefix  — เพิ่มก่อน แล้วค่อยใช้)
x--;  // x = 6
--x;  // x = 5
```

### Compound Assignment

```js
let x = 10;
x += 5;  // x = 15
x -= 3;  // x = 12
x *= 2;  // x = 24
x /= 4;  // x = 6
x %= 4;  // x = 2
```

-----

## 10. โครงสร้างควบคุม (Control Structure)

### if / else if / else

```js
let score = 75;

if (score >= 80) {
  console.log("A");
} else if (score >= 70) {
  console.log("B");
} else if (score >= 60) {
  console.log("C");
} else {
  console.log("ไม่ผ่าน");
}
```

### Ternary Operator (if-else แบบลดรูป)

```js
let age = 20;
let status = (age >= 18) ? "ผู้ใหญ่" : "เด็ก";
console.log(status); // ผู้ใหญ่
```

### switch…case

```js
let day = 1;
switch (day) {
  case 1: console.log("จันทร์"); break;
  case 2: console.log("อังคาร"); break;
  case 3: console.log("พุธ"); break;
  default: console.log("ไม่พบวัน");
}
```

### while Loop

```js
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

### for Loop

```js
for (let i = 1; i <= 5; i++) {
  console.log(i);
}

// วนใน Array
let colors = ["แดง", "น้ำเงิน", "เหลือง"];
for (let i = 0; i < colors.length; i++) {
  console.log(colors[i]);
}
```

### do…while Loop

```js
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
// ทำงานอย่างน้อย 1 รอบก่อนตรวจเงื่อนไข
```

### break และ continue

```js
for (let i = 1; i <= 10; i++) {
  if (i === 5) break;      // หยุดลูปทันที
  if (i % 2 === 0) continue; // ข้ามรอบนี้
  console.log(i);
}
```

-----

## 11. ค่า null, undefined และ NaN

```js
// null — ไม่มีค่า (กำหนดเอง)
let a = null;
console.log(a);        // null
console.log(!a);       // true (ถือว่า false)

// undefined — ประกาศแต่ไม่กำหนดค่า
let b;
console.log(b);        // undefined

// NaN — ผลลัพธ์จากการคำนวณที่ไม่ใช่ตัวเลข
let c = 10 - "x";
console.log(c);        // NaN
console.log(isNaN(c)); // true
```

-----

## 12. ฟังก์ชัน (Function)

### รูปแบบต่างๆ

```js
// 1. ไม่รับ ไม่ส่งค่า
function sayHello() {
  console.log("Hello!");
}
sayHello();

// 2. รับค่าเข้ามา (parameter)
function greet(name) {
  console.log("สวัสดี " + name);
}
greet("สมชาย");

// 3. ส่งค่าออกมา (return)
function add(a, b) {
  return a + b;
}
let result = add(3, 5); // 8

// 4. กำหนดค่าเริ่มต้น (Default Parameter)
function greet(name = "แขก") {
  console.log("สวัสดี " + name);
}
greet();          // สวัสดี แขก
greet("สมชาย");  // สวัสดี สมชาย
```

### ขอบเขตตัวแปร (Scope)

```js
let globalVar = "ตัวแปร Global"; // เข้าถึงได้ทุกที่

function myFunc() {
  let localVar = "ตัวแปร Local"; // เข้าถึงได้เฉพาะในฟังก์ชัน
  console.log(globalVar); // ✅ เข้าถึงได้
}

console.log(localVar); // ❌ Error
```

-----

## 13. JavaScript Object

```js
// การสร้าง Object
let user = {
  name: "kong",
  age: 20,
  email: "kong@gmail.com"
};

// การเข้าถึง Property
console.log(user.name);        // kong
console.log(user["email"]);    // kong@gmail.com

// Object ที่มี Method
let product = {
  name: "มะม่วง",
  price: 150,
  getInfo: function() {
    return this.name + " ราคา " + this.price + " บาท";
  }
};

console.log(product.getInfo()); // มะม่วง ราคา 150 บาท
```

### confirm()

```js
let answer = confirm("คุณต้องการลบข้อมูลหรือไม่?");
if (answer) {
  console.log("ลบแล้ว");
} else {
  console.log("ยกเลิก");
}
```

-----

## 14. HTML DOM

DOM (Document Object Model) คือโครงสร้างต้นไม้ที่ Browser สร้างจาก HTML เพื่อให้ JavaScript จัดการได้

### เข้าถึง Element

```js
// ด้วย ID
let el = document.getElementById("myId");

// ด้วย Tag Name
let tags = document.getElementsByTagName("p");

// ด้วย Class Name
let cls = document.getElementsByClassName("myClass");

// ด้วย CSS Selector (แนะนำ)
let el2 = document.querySelector("#myId");
let els = document.querySelectorAll(".myClass");
```

### แก้ไข Element

```js
let el = document.getElementById("demo");

el.innerHTML = "<b>ข้อความใหม่</b>";  // เปลี่ยน HTML ภายใน
el.innerText = "ข้อความธรรมดา";        // เปลี่ยนข้อความ
el.style.color = "red";                // เปลี่ยน CSS
el.setAttribute("class", "active");   // เปลี่ยน Attribute
```

### สร้าง/ลบ Element

```js
// สร้าง element ใหม่
let newEl = document.createElement("p");
newEl.innerText = "พารากราฟใหม่";
document.body.appendChild(newEl);

// ลบ element
let parent = document.getElementById("container");
let child = document.getElementById("item");
parent.removeChild(child);

// แทนที่ element
parent.replaceChild(newEl, child);
```

### จัดการ Class

```js
let el = document.getElementById("box");
el.classList.add("active");       // เพิ่ม class
el.classList.remove("active");    // ลบ class
el.classList.toggle("active");    // เพิ่ม/ลบ สลับกัน
el.classList.contains("active");  // ตรวจสอบว่ามี class ไหม
```

-----

## 15. DOM Event และ EventListener

### ชนิด Event ที่พบบ่อย

|Event        |ความหมาย        |
|-------------|----------------|
|`onclick`    |คลิก element     |
|`onmouseover`|เลื่อน mouse เข้า  |
|`onmouseout` |เลื่อน mouse ออก  |
|`onchange`   |เปลี่ยนค่าใน input |
|`onfocus`    |input ได้รับ focus|
|`onblur`     |input เสีย focus |
|`onsubmit`   |กด submit form  |
|`onload`     |โหลดหน้าเว็บเสร็จ  |

```html
<!-- แบบ Inline -->
<button onclick="sayHello()">คลิก</button>
```

### addEventListener (แนะนำ)

```js
let btn = document.getElementById("myBtn");

btn.addEventListener("click", function() {
  alert("คลิกแล้ว!");
});

// ใช้ Arrow Function
btn.addEventListener("mouseover", () => {
  btn.style.background = "yellow";
});
```

-----

## 16. JavaScript ES6+

### let และ const (Block Scope)

```js
// var ทะลุขอบเขต block — อย่าใช้แล้ว
if (true) {
  var x = 10; // เข้าถึงได้นอก if
}

// let และ const อยู่แค่ใน block
if (true) {
  let y = 20;
  const z = 30;
}
// console.log(y); // ❌ Error
```

### Arrow Function

```js
// แบบเดิม
function add(a, b) {
  return a + b;
}

// Arrow Function
const add = (a, b) => a + b;
const square = x => x * x;   // พารามิเตอร์ตัวเดียว ไม่ต้องมีวงเล็บ
const greet = () => "Hello"; // ไม่มีพารามิเตอร์
```

### Template Literal

```js
let name = "สมชาย";
let age = 25;

// แบบเดิม
console.log("ชื่อ: " + name + " อายุ: " + age);

// Template Literal
console.log(`ชื่อ: ${name} อายุ: ${age}`);

// หลายบรรทัด
let text = `
  บรรทัดที่ 1
  บรรทัดที่ 2
`;
```

### Destructuring

```js
// Array Destructuring
const colors = ["ขาว", "แดง", "น้ำเงิน"];
const [a, b, c] = colors;
console.log(a); // ขาว

// Object Destructuring
const user = { name: "kong", age: 20 };
const { name, age } = user;
console.log(name); // kong
```

### Spread Operator

```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// คัดลอก Array
const copy = [...arr1];

// ส่งหลายค่าเข้าฟังก์ชัน
console.log(Math.max(...arr1)); // 3
```

### Rest Parameter

```js
function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}
console.log(sum(1, 2, 3, 4, 5)); // 15
```

### Shorthand Object Property

```js
let name = "kong";
let email = "kong@gmail.com";

// แบบเดิม
const user1 = { name: name, email: email };

// ES6 Shorthand
const user2 = { name, email };
```

-----

## 17. Object-Oriented Programming (OOP)

### Class และ Object

```js
class User {
  name;
  password;

  constructor(name, password) {
    this.name = name;
    this.password = password;
  }

  login() {
    console.log(`${this.name} เข้าสู่ระบบแล้ว`);
  }
}

// สร้าง Object
let user1 = new User("สมชาย", "1234");
user1.login(); // สมชาย เข้าสู่ระบบแล้ว
```

### Encapsulation (การห่อหุ้ม)

```js
class BankAccount {
  #balance = 0;      // Private (เข้าถึงได้เฉพาะใน class)
  _owner = "";       // Protected (แนะนำใช้ใน subclass)

  constructor(owner) {
    this._owner = owner;
  }

  deposit(amount) {
    this.#balance += amount;
  }

  get balance() {
    return this.#balance; // Getter
  }
}

let acc = new BankAccount("สมชาย");
acc.deposit(1000);
console.log(acc.balance); // 1000
// acc.#balance = 9999;   // ❌ Error — เข้าถึงไม่ได้
```

### Inheritance (การสืบทอด)

```js
class User {
  constructor(name, password) {
    this.name = name;
    this.password = password;
  }
  login() {
    console.log(`${this.name} login`);
  }
}

class Teacher extends User {
  constructor(name, password, subject) {
    super(name, password); // เรียก constructor ของ User
    this.subject = subject;
  }
  teach() {
    console.log(`${this.name} สอนวิชา ${this.subject}`);
  }
}

let t = new Teacher("อาจารย์ก้อง", "pass123", "JavaScript");
t.login();  // อาจารย์ก้อง login
t.teach();  // อาจารย์ก้อง สอนวิชา JavaScript
```

### Polymorphism (การพ้องรูป)

```js
class Animal {
  speak() {
    console.log("...");
  }
}

class Dog extends Animal {
  speak() {
    console.log("โฮ่ง!"); // Override method
  }
}

class Cat extends Animal {
  speak() {
    console.log("เมี้ยว!"); // Override method
  }
}

let animals = [new Dog(), new Cat()];
animals.forEach(a => a.speak());
// โฮ่ง!
// เมี้ยว!
```

### Static Property และ Method

```js
class MathHelper {
  static PI = 3.14159;

  static circleArea(r) {
    return MathHelper.PI * r * r;
  }
}

console.log(MathHelper.PI);            // 3.14159
console.log(MathHelper.circleArea(5)); // 78.539...
// ไม่ต้อง new — เรียกผ่านชื่อ class ได้เลย
```

-----

## 18. Promise และ Async/Await `[เพิ่มเติม]`

จำเป็นสำหรับการทำงานแบบ **Asynchronous** เช่น การเรียก API หรือโหลดข้อมูล

### Promise

```js
const fetchData = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("โหลดข้อมูลสำเร็จ");
  } else {
    reject("เกิดข้อผิดพลาด");
  }
});

fetchData
  .then(data => console.log(data))   // สำเร็จ
  .catch(err => console.log(err));   // ล้มเหลว
```

### Async/Await (แนะนำ — อ่านง่ายกว่า)

```js
async function getData() {
  try {
    const response = await fetch("https://api.example.com/users");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}

getData();
```

-----

## 19. การจัดการ Error `[เพิ่มเติม]`

```js
// try...catch...finally
try {
  let result = 10 / 0;
  JSON.parse("ข้อมูลไม่ถูกต้อง"); // จะเกิด Error
} catch (error) {
  console.log("เกิดข้อผิดพลาด:", error.message);
} finally {
  console.log("ทำงานเสมอ ไม่ว่าจะ error หรือไม่");
}

// throw Error เอง
function divide(a, b) {
  if (b === 0) throw new Error("หารด้วยศูนย์ไม่ได้!");
  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (e) {
  console.log(e.message); // หารด้วยศูนย์ไม่ได้!
}
```

-----

## 20. Modules (import/export) `[เพิ่มเติม]`

แบ่งโค้ดเป็นไฟล์ย่อยๆ เพื่อจัดการได้ง่ายขึ้น

```js
// math.js — export ฟังก์ชัน
export function add(a, b) {
  return a + b;
}

export const PI = 3.14159;

export default function multiply(a, b) {
  return a * b;
}
```

```js
// main.js — import มาใช้
import multiply, { add, PI } from "./math.js";

console.log(add(2, 3));       // 5
console.log(PI);              // 3.14159
console.log(multiply(4, 5));  // 20
```

```html
<!-- ใน HTML ต้องระบุ type="module" -->
<script type="module" src="main.js"></script>
```

-----

## 21. Local Storage และ Session Storage `[เพิ่มเติม]`

เก็บข้อมูลไว้ใน Browser โดยไม่หมดอายุ (localStorage) หรือหมดเมื่อปิด tab (sessionStorage)

```js
// localStorage — ข้อมูลคงอยู่แม้ปิด browser
localStorage.setItem("username", "สมชาย");
let name = localStorage.getItem("username"); // สมชาย
localStorage.removeItem("username");
localStorage.clear(); // ล้างทั้งหมด

// เก็บ Object ต้องแปลงเป็น JSON ก่อน
let user = { name: "kong", age: 20 };
localStorage.setItem("user", JSON.stringify(user));

let savedUser = JSON.parse(localStorage.getItem("user"));
console.log(savedUser.name); // kong

// sessionStorage — ข้อมูลหายเมื่อปิด tab
sessionStorage.setItem("token", "abc123");
```

-----

## 22. Fetch API `[เพิ่มเติม]`

ใช้สำหรับเรียกข้อมูลจาก API ภายนอก (แทน XMLHttpRequest แบบเก่า)

```js
// GET ข้อมูล
async function getUsers() {
  const res = await fetch("https://jsonplaceholder.typicode.com/users");
  const users = await res.json();
  console.log(users);
}

// POST ส่งข้อมูล
async function createUser(userData) {
  const res = await fetch("https://api.example.com/users", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(userData)
  });
  const result = await res.json();
  console.log(result);
}

createUser({ name: "สมชาย", age: 25 });
```

-----

## สรุปหัวข้อที่เพิ่มเติมจากไฟล์ต้นฉบับ

|หัวข้อ                         |เหตุผลที่ต้องรู้                                       |
|-----------------------------|-------------------------------------------------|
|Promise / Async/Await        |ใช้ในการทำงานกับ API และข้อมูลแบบ async ในทุกโปรเจกต์จริง|
|try…catch (Error Handling)   |ป้องกัน app พังเมื่อเกิดข้อผิดพลาด                       |
|Modules (import/export)      |จัดการโค้ดหลายไฟล์ ใช้กับ framework ทุกตัว              |
|localStorage / sessionStorage|เก็บข้อมูลใน browser — มีอยู่ในเอกสารแต่ไม่มีตัวอย่าง       |
|Fetch API                    |ดึงข้อมูลจาก REST API ซึ่งจำเป็นมากในการพัฒนาเว็บสมัยใหม่   |

-----

> 📌 **แหล่งเรียนรู้เพิ่มเติม**
> 
> - [MDN Web Docs — JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
> - [JavaScript.info](https://javascript.info)