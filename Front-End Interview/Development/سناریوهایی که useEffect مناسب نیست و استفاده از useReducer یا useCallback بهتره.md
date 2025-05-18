

---

### **✅ ۱. زمانی که state وابسته به** **event داخل component**  **باشه، نه side effect خارجی**

  

**بد:**

```
const [count, setCount] = useState(0);

useEffect(() => {
  setCount((c) => c + 1);
}, []);
```

**چرا بده؟**

- این کار یه anti-pattern معروفه.
    
- چون useEffect بعد از render اجرا می‌شه و باعث یه رندر اضافی می‌شه.
    

  

**بهتر:**

- مستقیماً useState یا useReducer استفاده کن و state رو به‌درستی مقداردهی کن.
    

---

### **✅ ۲. وقتی state وابسته به** 

### **یک سری action پیچیده یا مرحله‌ای**

###  **هست**

  

**بد:**

```
const [formState, setFormState] = useState({ name: '', email: '', age: '' });

useEffect(() => {
  if (formState.name === '') {
    setFormState({ ...formState, nameError: 'Required' });
  }
}, [formState.name]);
```

**چرا بده؟**

- رندرهای اضافی و کد پیچیده.
    
- mutation غیرقابل پیش‌بینی.
    

  

**بهتر:**

- استفاده از useReducer برای مدیریت state و validation با action های مشخص.
    

---

### **✅ ۳. زمانی که تابعی به فرزند پاس داده می‌شه و تابع در** 

### **useEffect**

###  **تعریف می‌شه**

  

**بد:**

```
useEffect(() => {
  const handler = () => console.log('Clicked');
  window.addEventListener('click', handler);
  return () => window.removeEventListener('click', handler);
}, []);
```

**چرا بده؟**

- اگر handler تابع سنگینیه یا متغیر خارجی استفاده می‌کنه، کنترلش سخت می‌شه.
    

  

**بهتر:**

- از useCallback برای تعریف تابع استفاده کن و همیشه reference ثابتی بده.
    

```
const handler = useCallback(() => {
  console.log('Clicked');
}, []);
```

  

---

### **✅ ۴. زمانی که منطق درون** 

### **useEffect**

###  **باعث تغییر state بشه که همون تغییر باعث اجرای مجدد** 

### **useEffect**

###  **بشه**

  

**بد (بوی حلقه نامحسوس و re-render بی‌پایان):**

```
useEffect(() => {
  setValue(value + 1);
}, [value]);
```

**درست‌تر:**

- اصلاً همچین کار رو در useEffect نکن.
    
- یا باید از event trigger شده (مثلاً button click) این کار انجام شه.
    
- یا با useReducer منطق تغییر state رو کنترل کن.
    

---

### **✅ ۵. زمانی که یک تابع داخل** 

### **useEffect**

###  **هر بار تغییر می‌کنه**

  

**بد:**

```
useEffect(() => {
  expensiveFunction();
}, [expensiveFunction]);
```

**مشکل:**

- تابع هر بار تعریف بشه → dependency تغییر می‌کنه → اثر دوباره اجرا می‌شه
    

  

**بهتر:**

- wrap با useCallback تا تابع reference ثابتی داشته باشه:
    

```
const expensiveFunction = useCallback(() => { ... }, []);
useEffect(() => {
  expensiveFunction();
}, [expensiveFunction]);
```

  

---

## **🎯 خلاصه نکته کلیدی سینیور پسند:**

|**مشکل**|**ضد‌Pattern**|**راه‌حل مناسب**|
|---|---|---|
|تغییر state داخل useEffect|❌|✅ استفاده از useState یا useReducer مستقیم|
|مدیریت state وابسته به actionهای مرحله‌ای|❌|✅ استفاده از useReducer|
|مدیریت تابع‌های بیرونی که dependency داره|❌|✅ استفاده از useCallback|
|استفاده از effect برای logic داخلی component|❌|✅ استفاده از state و reducer مستقیم|

  
