سوال ۱: تفاوت بین getServerSideProps، getStaticProps و getInitialProps چیه؟

پاسخ:
	•	getStaticProps: در زمان build اجرا می‌شه (Static Generation)
	•	getServerSideProps: در هر request اجرا می‌شه (SSR)
	•	getInitialProps: در both client و server اجرا می‌شه (پیشنهاد نمی‌شه چون باعث جلوگیری از static optimization می‌شه)

⸻

سوال ۲: چه زمانی getStaticProps بهتر از getServerSideProps هست؟

پاسخ:
وقتی داده‌ها در زمان build در دسترس هستن و به‌ندرت تغییر می‌کنن → getStaticProps باعث سرعت بالا و SEO خوب می‌شه.

⸻

سوال ۳: مفهوم ISR (Incremental Static Regeneration) چیه؟

پاسخ:
ویژگی Next.js که اجازه می‌ده صفحات statically ساخته بشن و بعداً به‌صورت background به‌روزرسانی بشن:
``` js
export async function getStaticProps() {
  return {
    props: { ... },
    revalidate: 60, // ثانیه
  }
}
```


⸻

سوال ۴: تفاوت بین App Router و Pages Router چیه؟

پاسخ:
	•	Pages Router: ساختار قدیمی بر پایه فایل
	•	App Router: از /app شروع می‌شه، بر پایه React Server Components
	•	App Router امکانات پیشرفته‌تری داره مثل layout.tsx, loading.tsx, و nested routing

⸻

سوال ۵: چه زمانی از dynamic import استفاده می‌کنی؟

پاسخ:
برای split کردن کد و lazy load کردن کامپوننت‌ها:
```ts
const HeavyComponent = dynamic(() => import('./Heavy'), { ssr: false })
```


⸻

سوال ۶: چطور API route در Next.js ایجاد می‌کنی؟

پاسخ:
در مسیر /pages/api/hello.ts مثلاً:
```ts
export default function handler(req, res) {
  res.status(200).json({ message: 'Hello' });
}
```
فقط در Pages Router موجوده. در App Router از route handler ها استفاده می‌شه.

⸻

سوال ۷: Middleware در Next.js چطوری کار می‌کنه؟

پاسخ:
در پوشه middleware.ts در root قرار می‌گیره و قبل از رسیدن request به route اجرا می‌شه. می‌تونه برای auth، logging یا locale redirect استفاده شه.
مثال:
```ts
export function middleware(req) {
  const token = req.cookies.get("token")
  if (!token) return NextResponse.redirect('/login')
}
```


⸻

سوال ۸: چطور از React Server Components در Next.js استفاده می‌کنی؟

پاسخ:
در App Router، کامپوننت‌هایی که درون فایل‌های .tsx قرار دارن و از hookهای client استفاده نمی‌کنن، به‌صورت پیش‌فرض server component هستن.
برای تعریف client component:
```ts
'use client'
```


⸻

سوال ۹: فرق Link در Next.js با تگ a چیه؟

پاسخ:
	•	Link از next/navigation استفاده می‌کنه و SPA navigation انجام می‌ده
	•	باعث جلوگیری از full-page reload می‌شه
	•	a برای external لینک‌ها یا در کنار Link برای تنظیم target, rel استفاده می‌شه

⸻

سوال ۱۰: چطور internationalization (i18n) رو در Next.js پیاده می‌کنی؟

پاسخ:
	•	از ویژگی داخلی i18n در next.config.js می‌تونی استفاده کنی
	•	یا از پکیج‌هایی مثل next-i18next برای ترجمه مبتنی بر فایل‌های JSON
پیکربندی پایه:
```js
i18n: {
  locales: ['en', 'fa'],
  defaultLocale: 'fa',
}
```
