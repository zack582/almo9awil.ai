# دليل النشر على Netlify

## الخطوات السريعة

### 1. إنشاء مستودع GitHub

```bash
# إنشاء مستودع جديد على GitHub باسم: almiqaoul-search-engine
# نسخ كل الملفات التالية إلى المستودع:
```

**الملفات المطلوبة:**
- `index.html` - الملف الرئيسي
- `netlify.toml` - إعدادات Netlify  
- `_redirects` - إعادة توجيه الروابط
- `README.md` - وثائق المشروع
- `.gitignore` - ملفات مستثناة
- `package.json` - معلومات المشروع
- `LICENSE` - رخصة المشروع

### 2. رفع الملفات إلى GitHub

```bash
git init
git add .
git commit -m "Initial commit: Arabic search engine"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/almiqaoul-search-engine.git
git push -u origin main
```

### 3. ربط Netlify بـ GitHub

1. اذهب إلى [Netlify.com](https://netlify.com)
2. سجل دخول أو أنشئ حساب جديد
3. انقر على **"New site from Git"**
4. اختر **GitHub** وامنح الصلاحيات
5. اختر مستودع `almiqaoul-search-engine`
6. إعدادات البناء:
   - **Build command:** اتركه فارغاً
   - **Publish directory:** `.` (نقطة)
   - **Branch:** `main`
7. انقر **"Deploy site"**

### 4. تحديث رابط الـ Webhook

⚠️ **مهم جداً:** قم بتحديث الرابط في `index.html`:

```javascript
// استبدل هذا السطر:
const WEBHOOK_URL = window.location.hostname === 'localhost' 
  ? "http://localhost:5678/webhook-test/247924dc-d09c-44bb-b062-033b71738f7f"
  : "https://your-production-webhook-url.com/webhook/your-id";

// بالرابط الفعلي لـ webhook الخاص بك:
const WEBHOOK_URL = window.location.hostname === 'localhost' 
  ? "http://localhost:5678/webhook-test/247924dc-d09c-44bb-b062-033b71738f7f"
  : "https://YOUR-N8N-DOMAIN.com/webhook/YOUR-ACTUAL-WEBHOOK-ID";
```

### 5. إعداد متغيرات البيئة (اختياري)

في لوحة تحكم Netlify:
1. اذهب إلى **Site settings**
2. انقر على **Environment variables**
3. أضف:
   - `WEBHOOK_URL`: رابط الـ webhook الإنتاجي

### 6. إعداد Domain مخصص (اختياري)

1. في **Site settings** → **Domain management**
2. انقر **Add custom domain**
3. أدخل النطاق الخاص بك
4. اتبع التعليمات لتحديث DNS

## إعداد CORS في N8N

في نود الـ webhook في N8N، أضف Response Headers:

```json
{
  "Access-Control-Allow-Origin": "*",
  "Access-Control-Allow-Methods": "POST, GET, OPTIONS",
  "Access-Control-Allow-Headers": "Content-Type, Authorization",
  "Content-Type": "application/json"
}
```

أو للأمان أكثر، استخدم نطاق محدد:

```json
{
  "Access-Control-Allow-Origin": "https://your-site-name.netlify.app",
  "Access-Control-Allow-Methods": "POST, OPTIONS", 
  "Access-Control-Allow-Headers": "Content-Type"
}
```

## التحقق من النشر

1. انتظر حتى يكتمل النشر (عادة 1-2 دقيقة)
2. انقر على رابط الموقع المؤقت (مثل: `https://amazing-name-123456.netlify.app`)
3. اختبر وظيفة البحث
4. تحقق من وحدة التحكم للأخطاء

## استكشاف الأخطاء

### خطأ CORS
```
Access to fetch at 'your-webhook' from origin 'your-netlify-site' has been blocked by CORS policy
```
**الحل:** إعداد CORS في N8N webhook كما موضح أعلاه

### خطأ 404 عند تحديث الصفحة
**الحل:** ملف `_redirects` موجود ويحتوي على:
```
/*    /index.html   200
```

### الموقع لا يعمل على الهاتف
**الحل:** تأكد من وجود meta viewport في `index.html`:
```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

## التطوير المحلي

```bash
# تشغيل خادم محلي
npx serve .
# أو
npx live-server .
```

## النشر التلقائي

✅ كل push إلى branch `main` = نشر تلقائي  
✅ Preview deployments للـ pull requests  
✅ Rollback سهل للإصدارات السابقة  

## الأمان

- ✅ HTTPS تلقائي مع Let's Encrypt
- ✅ Security headers في `netlify.toml`
- ✅ Content Security Policy
- ✅ XSS protection

## الأداء

- ✅ CDN عالمي
- ✅ Gzip compression تلقائي
- ✅ Cache headers للملفات الثابتة
- ✅ تحسين للهواتف المحمولة

## إضافات مفيدة

### Netlify Analytics
1. اذهب إلى Site overview
2. انقر Enable Analytics
3. $9/شهر للإحصائيات المتقدمة

### Form Handling
إذا كنت تريد إضافة نماذج:
```html
<form name="contact" method="POST" data-netlify="true">
  <!-- form fields -->
</form>
```

### Functions (Serverless)
إنشاء مجلد `netlify/functions/` للوظائف الخادمية.

## الدعم

- [Netlify Docs](https://docs.netlify.com)
- [Netlify Community](https://community.netlify.com)
- [Discord Server](https://discord.com/invite/netlify)

---

**نصيحة:** احفظ رابط webhook في مكان آمن ولا تشاركه علناً!