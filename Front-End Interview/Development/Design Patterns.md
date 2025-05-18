### **سوال ۱: Container-Presenter Pattern چیه و چرا در React مفیده؟**

  

**پاسخ:**

یک pattern برای جداسازی منطق از UI:

- **Container:** شامل state و logic (مثل fetch، mutation)
    
- **Presenter:** فقط مسئول نمایش داده‌هاست (stateless)
    
    مزایا:
    
- تست‌پذیری بالا
    
- قابلیت استفاده مجدد
    
- سادگی در دیباگ و توسعه
    

---

### **سوال ۲: Compound Components چیه و کی استفاده می‌شه؟**

  

**پاسخ:**

Patternیه که یک کامپوننت اصلی چندین زیرکامپوننت وابسته داره که با context به هم متصل هستن. مثل API فرم‌های پیچیده یا تب‌ها.

مثال معروف:
``` tsx
<Tabs>
  <Tabs.List>...</Tabs.List>
  <Tabs.Panel>...</Tabs.Panel>
</Tabs>
```

  

---

### **سوال ۳: Controlled vs Uncontrolled Components چیه؟**

  

**پاسخ:**

- **Controlled:** state از بیرون کنترل می‌شه (با useState یا props)
    
- **Uncontrolled:** رفرنس مستقیم به DOM (با useRef)
    
    در فرم‌ها، controlled ها بهترن برای validation، اما uncontrolled سریع‌تر و ساده‌تر هستن برای فرم‌های ساده
    

---

### **سوال ۴: Singleton Pattern چیه و در کجا می‌تونه مفید باشه؟**

  

**پاسخ:**

- فقط یک instance از کلاس یا object داشته باشیم
    
- مفید برای contextهای global مثل theme، i18n، یا یک event bus
    
    مثلاً:

``` js
let instance;
export const getInstance = () => {
  if (!instance) instance = createSomething();
  return instance;
}
```

  

---

### **سوال ۵: Higher Order Component (HOC) چیه و چه کاربردهایی داره؟**

  

**پاسخ:**

یک تابع که یک کامپوننت ورودی می‌گیره و یک کامپوننت جدید خروجی می‌ده

کاربرد:

- کدهای مشترک مثل auth، data fetching، logging
    
    مثال:

``` js
function withAuth(Component) {
  return function Protected(props) {
    return isLoggedIn ? <Component {...props} /> : <Redirect />
  }
}
```

