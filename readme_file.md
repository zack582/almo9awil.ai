# المقاول - محرك البحث الذكي

محرك بحث ذكي مصمم خصيصاً للمقاولين والأعمال التجارية باللغة العربية.

## المميزات

- ✅ واجهة مستخدم عربية متقدمة
- ✅ تصميم متجاوب يعمل على جميع الأجهزة
- ✅ بحث ذكي مدعوم بالذكاء الاصطناعي
- ✅ سجل محلي للاستعلامات السابقة
- ✅ تأثيرات بصرية متقدمة وسلسة
- ✅ دعم الوضع المظلم والفاتح
- ✅ تحسين لمحركات البحث (SEO)

## التقنيات المستخدمة

- **HTML5** - هيكل الصفحة
- **CSS3** - التصميم والتأثيرات البصرية
- **Vanilla JavaScript** - الوظائف التفاعلية
- **Google Fonts** - خط القاهرة العربي
- **Netlify** - الاستضافة والنشر

## التنصيب والتشغيل

### النشر على Netlify

1. انسخ هذا المستودع إلى حسابك على GitHub
2. اربط حسابك على Netlify بـ GitHub
3. اختر هذا المستودع للنشر
4. قم بتحديث متغير `WEBHOOK_URL` في الملف `index.html`

### التشغيل المحلي

```bash
# انسخ المستودع
git clone https://github.com/your-username/arabic-search-engine.git

# انتقل إلى المجلد
cd arabic-search-engine

# افتح الملف في المتصفح
open index.html
```

## إعداد الـ Webhook

قم بتحديث قيمة `WEBHOOK_URL` في الملف `index.html`:

```javascript
const WEBHOOK_URL = "https://your-n8n-instance.com/webhook/your-webhook-id";
```

## البنية

```
arabic-search-engine/
├── index.html          # الملف الرئيسي
├── netlify.toml        # إعدادات Netlify
├── _redirects          # إعادة توجيه الروابط
├── README.md          # هذا الملف
└── .gitignore         # ملفات مستثناة من Git
```

## المساهمة

نرحب بمساهماتكم! يرجى:

1. عمل Fork للمستودع
2. إنشاء فرع جديد (`git checkout -b feature/amazing-feature`)
3. تنفيذ التغييرات (`git commit -m 'Add amazing feature'`)
4. رفع التغييرات (`git push origin feature/amazing-feature`)
5. فتح Pull Request

## الترخيص

هذا المشروع مرخص تحت رخصة MIT - راجع ملف [LICENSE](LICENSE) للتفاصيل.

## الدعم

إذا كان لديك أي أسئلة أو مشاكل، يرجى فتح Issue في المستودع أو التواصل معنا.

## إقرارات

- تصميم مستوحى من أحدث اتجاهات تصميم المواقع
- خط القاهرة من Google Fonts
- الأيقونات والرسوم من تصميمنا الخاص

---

**ملاحظة مهمة:** تأكد من تحديث رابط الـ webhook قبل النشر في بيئة الإنتاج.

## الإعدادات المطلوبة

### متغيرات البيئة في Netlify

1. اذهب إلى Site Settings في لوحة تحكم Netlify
2. انقر على Environment Variables
3. أضف المتغيرات التالية:

```
WEBHOOK_URL = "https://your-production-webhook-url.com/webhook/your-id"
```

### إعداد CORS في N8N

في نود الـ webhook في N8N، أضف الهيدرز التالية:

```json
{
  "Access-Control-Allow-Origin": "https://your-netlify-domain.netlify.app",
  "Access-Control-Allow-Methods": "POST, OPTIONS",
  "Access-Control-Allow-Headers": "Content-Type"
}
```