# 🤝 دليل المساهمين

الشكر لرغبتك لالمساهمة في **Windows Adjust Reference**! 🌟

---

## 📝 القواعد الأساسية

### ⭐ ها الفمرة للمساهمة:

1. **Fork** الريبو
2. **Clone** للجهاز الخاص بك
3. **Branch** للتتبع عملك
4. **Commit** التغييرات
5. **Push** للفرع الخاص بك
6. **Pull Request** للمجبول

---

## 💵 نوعا المساهمات

### 🎨 1. أوامر جديدة (Topics)

**هل تريد إضافة أوامر Windows جديدة؟**

**المطلوب:**
- لا يكون موجود بالفعل في الريبو
- الأمر الواحد ورافق له بوصف مفصل
- مختبر على **Windows 10/11 LTSC** على الأقل

**مع اللينكم والمراجع:**
```html
<tr class="topic-row" 
    data-target="my-topic-id" 
    data-search="keyword1 keyword2 search-terms">
    <td>التصنيف الرئيسي</td>
    <td>اسم الخدمة بالعربية</td>
    <td class="muted">وصف ثلاثي السطر</td>
    <td>
        <span class="badge">KEYWORD</span>
        <span class="badge">TAG</span>
    </td>
    <td>
        <button class="btn" onclick="jumpTo('my-topic-id')">فتح</button>
    </td>
</tr>
```

ثم أضف الكارت:
```html
<div class="card topic-card" id="my-topic-id">
    <span class="card-category cat-system">تظبيط النظام</span>
    <h2>🔧 اسم الخدمة</h2>
    <p class="muted">وصف طويل للخدمة.</p>
    
    <div class="warning-box">
        <span class="warning-icon">⚠️</span>
        <div>تحذير عند الحاجة</div>
    </div>
    
    <div class="code-container">
        <div class="code-header">
            PowerShell المسئول
            <span class="code-tool">ADMIN REQUIRED</span>
        </div>
        <pre onclick="copyToClipboard(this)">
<code>Your-Command-Here</code>
        </pre>
    </div>
</div>
```

### 📝 2. تحسينات على واجهة الموقع

**المطلوب:**
- CSS/UI التحسينات
- Performance وتسريع الموقع
- الأذاعات الجديدة

**ما لا نقبل:**
- تغييرات مهمة بدون PR
- إزالة أوامر بدون متابعة

### 📋 3. تحسينات على الوثائق

**المطلوب:**
- README.md التحسينات
- Documentation زيادة
- شرح أعمق للأوامر

---

## 📄 مواصلات اللغة والأسلوب

### لغة التراجمة:
- لا نستخدم المترجمين الآليين (خم عام لا يفهم التراميب)
- ترجمة يدوية متقنة بما يناسب السياق

### الأسلوب:
- الارتباط التقني العالي
- وضوح كاملة
- لا تسخيف في الشرح

---

## ⚠️ أمور مهمة

### تأكد من:
- [ ] الأمر مدارؤ بالفعل (باختبار)
- [ ] الوصف واضح ودقيق
- [ ] تم شتر التغيير والوشيبة

### ما لا تنساه:
- ❌ لا توار بحرام Windows
- ❌ لا تعلم بعض الأشياء بدون الاختبار
- ❌ لا عيب يا خارظ

---

## 🚀 بعد التقديم

1. **مراجعة البيانات** - تؤكد من سلامة الأمر
2. **الإجابة** - برم راجعو أي استفسارات
3. **الموافقة** - ما عر الثقه 

---

## 😉 والموافقه في النهاية

الملفت للآباء العظيم على مساهماتهم! 🌟

**براه عريباث**
