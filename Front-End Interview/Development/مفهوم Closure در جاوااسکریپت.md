### **سوال ۱: Closure در جاوااسکریپت چیه؟**

  

**پاسخ:**

کلوجر زمانی ایجاد می‌شه که یک تابع به متغیرهای scope بالاتر از خودش (محیط بیرونی) دسترسی داره حتی بعد از اینکه اون scope اصلی تموم شده.

یعنی تابعی که “حافظه” محیط تعریف‌شدنش رو نگه می‌داره.

``` js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}
const counter = outer();
counter(); // 1
counter(); // 2
```

  

---

### **سوال ۲: چه کاربردهایی برای Closure وجود داره؟**

  

**پاسخ:**

- ایجاد متغیر private
    
- ساخت فانکشن‌های memoization
    
- throttle و debounce
    
- نگه‌داری state بدون استفاده از کلاس یا رفرنس خارجی
    
- ساخت فانکشن‌های curried
    

---

### **سوال ۳: چه مشکلاتی ممکنه از استفاده‌ی نادرست از closure پیش بیاد؟**

  

**پاسخ:**

- Memory Leak: اگر فانکشن به context خارجی اشاره کنه ولی هیچ‌وقت پاک نشه
    
- Stale Closure: مخصوصاً در React useEffect اگر به متغیرهای قدیمی درون کلوجر دسترسی داشته باشی
    
	- پیچیدگی در debug کردن به خاطر دسترسی مخفی به scopeهای قبلی