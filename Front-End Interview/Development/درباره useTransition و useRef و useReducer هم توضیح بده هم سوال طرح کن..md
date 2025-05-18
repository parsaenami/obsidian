
## **✅ useTransition**

  

### **توضیح:**

- useTransition از React 18 معرفی شد.
    
- برای مدیریت **آپدیت‌های غیر فوری (non-urgent)** استفاده می‌شه.
    
- کمک می‌کنه UI در هنگام کارهای سنگین، responsive بمونه و user احساس نکنه اپلیکیشن قفل کرده.
    

  

### **کاربرد:**

- فیلتر کردن لیست بزرگ
    
- رندر کردن UI سنگین بعد از تعامل کاربر (مثلاً سرچ)
    

  

### **مثال:**

```
const [isPending, startTransition] = useTransition();

function handleChange(e) {
  startTransition(() => {
    setSearch(e.target.value);
  });
}
```

🔹 نکته:

- آپدیت‌های داخل startTransition دارای priority پایین‌ترن.
    
- React آپدیت‌های urgent (مثل تایپ) رو با اولویت بالا نگه می‌داره.
    

---

### **سوالات useTransition:**

1. کاربرد اصلی useTransition در React 18 چیه و چه مشکلی رو حل می‌کنه؟
    
2. چه تفاوتی بین آپدیت داخل startTransition و آپدیت مستقیم state هست؟
    
3. چه موقع از isPending استفاده می‌کنیم و چه کاربردی داره؟
    
4. آیا useTransition روی سرور هم کار می‌کنه؟
    
5. چه تفاوتی بین useTransition و useDeferredValue هست؟
    

---

## **✅ useRef**

  

### **توضیح:**

- useRef یه hookه که یک **ref object قابل mutable** می‌ده که:
    
    - می‌تونی به DOM element دسترسی داشته باشی.
        
    - یا یک مقدار mutable نگه‌داری کنی که تغییرش باعث re-render نشه.
        
    

  

### **کاربرد:**

- گرفتن reference به DOM (مثل focus روی input)
    
- نگه‌داری مقدارهای قبلی
    
- ساختن متغیرهای «در سایه» بدون trigger رندر
    

  

### **مثال:**

```
const inputRef = useRef(null);

function focusInput() {
  inputRef.current.focus();
}
```

```
const renderCount = useRef(0);
useEffect(() => {
  renderCount.current += 1;
});
```

  

---

### **سوالات useRef:**

1. چه تفاوتی بین useRef و useState هست؟
    
2. آیا تغییر مقدار useRef باعث رندر مجدد کامپوننت می‌شه؟
    
3. چطور با useRef می‌تونیم به DOM element دسترسی پیدا کنیم؟
    
4. چطور می‌تونیم با useRef یک مقدار mutable رو خارج از flow رندر ذخیره کنیم؟
    
5. آیا useRef همیشه به DOM اشاره می‌کنه یا می‌تونه برای داده هم استفاده شه؟
    

---

## **✅ useReducer**

  

### **توضیح:**

- useReducer یه hook پیشرفته‌تر برای مدیریت state پیچیده یا تو در تو هست.
    
- شبیه Redux:
    
    - reducer function: state + action → new state
        
    
- مناسب برای:
    
    - فرم‌های پیچیده
        
    - مدیریت state داینامیک و چند مرحله‌ای
        
    - جاهایی که تغییرات زیادی روی state داریم
        
    

  

### **مثال:**

```
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
```

  

---

### **سوالات useReducer:**

1. چه زمانی استفاده از useReducer به جای useState توصیه می‌شه؟
    
2. تفاوت بین useReducer و Redux چیه؟
    
3. ساختار action در useReducer چیه؟
    
4. آیا می‌تونیم با useReducer چندین state جدا رو مدیریت کنیم؟
    
5. چطور می‌تونی initial state رو بر اساس props داینامیک بسازی (init function در useReducer)؟
    

---
