### **سوال ۱: Service Worker چیه و کجا استفاده می‌شه؟**

  

**پاسخ:**

Service Worker یک اسکریپت جدا از main thread مرورگره که بین اپلیکیشن و شبکه قرار می‌گیره و می‌تونه requestها رو intercept کنه.

کاربردها:

- کش کردن assets
    
- offline support
    
- push notification
    
- background sync
    

---

### **سوال ۲: چرخه‌ی زندگی (lifecycle) یک Service Worker چطوره؟**

  

**پاسخ:**

۱. **Register:** ثبت فایل service worker

۲. **Install:** دانلود و کش فایل‌های مورد نیاز

۳. **Activate:** پاک‌سازی کش قدیمی و آماده‌سازی برای اجرا

۴. **Fetch:** هندل کردن requestهای شبکه

  

نکته: SW فقط بعد از close و reopen شدن تب فعال می‌شه (برای امنیت).

---

### **سوال ۳: تفاوت بین Cache API و IndexedDB در Service Worker چیه؟**

  

**پاسخ:**

- **Cache API:** برای ذخیره و مدیریت request/responseها استفاده می‌شه (مثلاً HTML, JS, CSS)
    
- **IndexedDB:** برای ذخیره داده‌های ساختاریافته (مثل JSON، داده‌های فرم و…)
    
    در SW معمولاً Cache برای فایل‌ها و IndexedDB برای دیتاهای dynamic استفاده می‌شن.
    

---

### **سوال ۴: چه چالش‌هایی در استفاده از Service Worker وجود داره؟**

  

**پاسخ:**

- مدیریت نسخه‌بندی و بروزرسانی فایل‌ها
    
- پیچیدگی در invalidate کردن کش
    
- Debug کردن سخت‌تر از اپلیکیشن‌های معمولی
    
- خطر stale content اگه مدیریت درست نشه
    
- نیاز به https (به جز localhost)