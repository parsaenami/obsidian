### **سوال ۱: مهم‌ترین دلایل افت performance در اپ‌های React چیه؟**

  

**پاسخ:**

- رندرهای غیرضروری
    
- عدم استفاده از memoization
    
- حجم زیاد جاوااسکریپت
    
- contextهای بزرگ و shared
    
- استفاده نادرست از state یا props در سطوح بالا
    

---

### **سوال ۲: چطور می‌شه از re-render شدن غیرضروری جلوگیری کرد؟**

  

**پاسخ:**

- استفاده از React.memo
    
- useMemo برای محاسبات سنگین
    
- useCallback برای ارسال فانکشن‌ها به فرزند
    
- شکست کامپوننت‌های بزرگ به بخش‌های کوچکتر
    
- بررسی dependency array در useEffect
    

---

### **سوال ۳: lazy loading چیه و چطور در React پیاده‌سازی می‌شه؟**

  

**پاسخ:**

- بارگذاری فایل یا کامپوننت فقط زمانی که واقعاً لازمه

```
const LazyComponent = React.lazy(() => import('./Component'));
```

با استفاده از Suspense کامپوننت رو wrap می‌کنی.

---

### **سوال ۴: چطور می‌تونیم تصاویر رو بهینه کنیم؟**

  

**پاسخ:**

- استفاده از فرمت‌های مدرن مثل WebP/AVIF
    
- lazy loading تصاویر با loading="lazy"
    
- استفاده از CDN
    
- سرویس‌دهی responsive با srcSet
    

---

### **سوال ۵: چه ابزارهایی برای بررسی performance سمت کلاینت وجود داره؟**

  

**پاسخ:**

- Chrome DevTools (Performance tab)
    
- Lighthouse
    
- Web Vitals
    
- React DevTools (Profiler tab)
    
- SpeedCurve یا Calibre برای مانیتورینگ
    

---

### **سوال ۶: tree-shaking چیه و چطور به ما کمک می‌کنه؟**

  

**پاسخ:**

- فرایند حذف کدهای import شده‌ای که استفاده نشدن
    
- ابزارهایی مثل Webpack این کار رو با ESModules انجام می‌دن
    
- باعث کاهش سایز bundle نهایی می‌شه
    

---

### **سوال ۷: defer و async در تگ script چه تفاوتی دارن؟**

  

**پاسخ:**

- async: بلافاصله پس از دانلود اجرا می‌شه، ممکنه DOM هنوز کامل نشده باشه
    
- defer: بعد از کامل شدن DOM اجرا می‌شه، ترتیب حفظ می‌شه
    
    در React معمولا از defer استفاده می‌شه برای اسکریپت‌های بیرونی
    

---

### **سوال ۸: Code Splitting چیه و چطور با React انجام می‌شه؟**

  

**پاسخ:**

- شکستن کد به بخش‌های کوچکتر برای کاهش زمان لود اولیه
    
- در React با dynamic import و React.lazy
    
- Webpack و Vite پشتیبانی کامل دارن
    

---

### **سوال ۹: Critical Rendering Path چیه؟**

  

**پاسخ:**

مسیر اجرای رندر اولیه شامل:

- Parse HTML → Build DOM
    
- Parse CSS → Build CSSOM
    
- Combine DOM + CSSOM → Render Tree
    
- Layout → Paint
    
    هدف بهینه‌سازی: کاهش این مسیر با کاهش فایل‌ها، استفاده از inline critical CSS، delay جاوااسکریپت و…
    

---

### **سوال ۱۰: چطور می‌شه استفاده از حافظه (Memory) رو بهینه کرد؟**

  

**پاسخ:**

- پاک کردن event listenerها
    
- جلوگیری از reference به objectهای غیرقابل دسترسی
    
- استفاده درست از useEffect cleanup
    
- اجتناب از closureهای غیرضروری
    
- استفاده از ابزار DevTools Memory Snapshot