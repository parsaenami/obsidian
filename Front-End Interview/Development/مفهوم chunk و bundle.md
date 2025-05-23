### **سوال ۱: تفاوت بین Chunk و Bundle چیه؟**

  

**پاسخ:**

- **Bundle:** خروجی نهایی Webpack یا ابزارهای مشابه که شامل تمام کدهای مورد نیاز اپ هست (JS، CSS، …)
    
- **Chunk:** تکه‌ای از bundle که جداگانه تولید می‌شه و می‌تونه lazy load بشه.
    

  

مثلاً:

- main.js (bundle اصلی)
    
- vendors~product.chunk.js (برای lazy load یک بخش خاص)
    

---

### **سوال ۲: چطوری می‌تونیم با Webpack یا ابزارهای مشابه chunkهای جدا بسازیم؟**

  

**پاسخ:**

با استفاده از dynamic import:

```
const Product = React.lazy(() => import('./Product'));
```

و Webpack به‌صورت خودکار یک chunk جدا برای این فایل می‌سازه.

همچنین می‌تونی با SplitChunksPlugin یا optimization.splitChunks رفتار دقیق‌تر رو مشخص کنی.

---

### **سوال ۳: چه مزیتی داره که پروژه رو به chunkهای جدا تقسیم کنیم؟**

  

**پاسخ:**

- کاهش زمان لود اولیه (Initial Load Time)
    
- استفاده بهینه از cache مرورگر
    
- بارگذاری فقط چیزهایی که نیاز داریم
    
- بهبود تجربه کاربری در پروژه‌های بزرگ
    

---

### **سوال ۴: چه چالش‌هایی ممکنه در مدیریت chunkها وجود داشته باشه؟**

  

**پاسخ:**

- افزایش تعداد requestها به سرور
    
- پیچیدگی در prefetch/preload
    
- احتمال افت تجربه کاربر اگه lazy load به‌موقع انجام نشه
    
- مدیریت درست خطاها در dynamic import
    
- نیاز به fallback UI مناسب برای React.lazy