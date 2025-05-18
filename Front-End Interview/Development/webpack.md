**Webpack** یه **module bundler** برای جاوااسکریپته. یعنی:

  

> همه‌ی فایل‌ها (JS, CSS, images, etc.) رو به‌عنوان **ماژول** در نظر می‌گیره، و اونا رو به یه یا چند فایل **bundle** تبدیل می‌کنه که مرورگر بتونه بهینه لود کنه.

---

## **🧱 چرا Webpack مهمه؟**

- بدون Webpack یا ابزار مشابه، باید به صورت دستی کلی فایل JS و CSS رو مدیریت کنی.
    
- با Webpack:
    
    - همه چیز moduler می‌شه.
        
    - می‌تونی از ES6 modules، TypeScript، SCSS و… استفاده کنی.
        
    - پرفورمنس اپتیمایز می‌شه (minify, code splitting, caching).
        
    - با ابزارهایی مثل React، Vue، و Angular یکپارچه می‌شه.
        
    

---

## **🧩 اجزای اصلی Webpack**
|**جزء**|**توضیح**|
|---|---|
|**Entry**|نقطه ورود اپلیکیشن برای Webpack|
|**Output**|محل خروجی bundle نهایی|
|**Loaders**|برای تبدیل فایل‌های غیر JS (مثل SCSS, images, TypeScript)|
|**Plugins**|برای کارهای پیچیده‌تر مثل minify، تعریف متغیرهای محیطی، extract CSS|
|**Mode**|توسعه (development) یا تولید (production)|
|**DevServer**|سرور توسعه برای هات ری‌لود|
  

---

## **🧪 Loaders چیست؟**

  

Webpack به‌صورت پیش‌فرض فقط فایل‌های JS رو می‌فهمه.

  

**Loaders** میان و فایل‌هایی مثل:

- .scss با sass-loader
    
- .ts با ts-loader
    
- عکس و SVG و فونت‌ها
    
    رو به شکل قابل فهم برای JS در می‌آرن.
    

---

## **🔌 Plugins چیست؟**

  

برای عملیات سنگین‌تر:

- HtmlWebpackPlugin: تولید فایل HTML نهایی
    
- MiniCssExtractPlugin: جدا کردن CSS از JS
    
- DefinePlugin: تعریف متغیر محیطی
    

---

## **💥 Code Splitting**

  

یعنی شکستن باندل بزرگ به تکه‌های کوچکتر برای:

- لود سریع‌تر صفحات
    
- بهتر شدن UX
    
- استفاده فقط از فایل‌های مورد نیاز در لحظه
    

  

مثال:
```js
import('module-name') // dynamic import
```

  

---

## **⚙️ Hot Module Replacement (HMR)**

  

با استفاده از webpack-dev-server می‌تونی:

- موقع توسعه بدون رفرش صفحه، کدها رو آپدیت کنی.
    
- حالت و state حفظ بشه.
    

---

## **⏱️ Tree Shaking**

  

یعنی حذف کدهای **استفاده‌نشده** (dead code) موقع production build

برای اینکه درست کار کنه باید:

- از ES6 Modules استفاده بشه.
    
- در حالت production باشی.
    

---
