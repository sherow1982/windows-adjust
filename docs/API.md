# 🔨 مرجع البنية التقنية (Technical Reference)

## نظرة عامة

Windows Adjust Reference بنية **Static Site** بسيطة عالية الأداء:

- 📄 **HTML5** - بنية سلاسلة
- 🎨 **CSS3** - تنسيق حديث + Gradients + CSS Variables
- 🔍 **Vanilla JS** - بحث حي + Event Handlers

---

## بنية HTML

### Table Rows (Topic Entry)

```html
<tr class="topic-row" data-target="unique-id" data-search="keyword1 keyword2 keyword3">
  <td><span class="category-label category-system">🔧 النظام</span></td>
  <td>الموضوع بالعربية</td>
  <td class="muted">وصف سريع وميسر</td>
  <td><span class="badge">TAG1</span><span class="badge">TAG2</span></td>
</tr>
```

### الفحات المتاحة:

| الفئة | الرمز | اللون |
|-------|--------|------|
| تظبيط النظام | 🔧 | `category-system` |
| الخصوصية والأمان | 🔒 | `category-privacy` |
| تحسين الأداء | ⚡ | `category-performance` |
| تنظيف النظام | 🧹 | `category-cleanup` |
| إصلاح المشاكل | 🔨 | `category-fix` |

---

## بنية CSS

### CSS Variables بالكامل:

```css
:root {
  --bg-color: #0a0e27;                    /* لون الخلفية الرئيسي */
  --card-bg: linear-gradient(...);         /* تدرج البطاقات */
  --accent: #38bdf8;                      /* اللون الرئيسية */
  --text-primary: #f8fafc;                /* النص الأساسي */
  --text-secondary: #94a3b8;              /* النص الثانوي */
  /* ... مزيد */
}
```

### الفئات الرئيسية:

- `.card` - بطاقة رئيسية
- `.topic-row` - صف مم الجدول
- `.badge` - علامة مايكرو
- `.search-input` - مداخلة البحث
- `.btn` - زرار عامة
- `.muted` - نص خاتم

---

## بنية JavaScript

### الدوال الرئيسية:

#### `normalize(s)`
تحويل النص لالبحث:

```javascript
function normalize(s) {
  return (s || '').toString().toLowerCase().trim();
}
```

#### `applySearch(qRaw)`
تطبيق البحث على الجدول:

```javascript
function applySearch(qRaw) {
  const q = normalize(qRaw);
  let visible = 0;
  rows.forEach(r => {
    const hay = normalize(r.getAttribute('data-search') + ' ' + r.innerText);
    const show = !q || hay.includes(q);
    r.classList.toggle('hidden', !show);
    if (show) visible++;
  });
  // تحديث الرسالة
}
```

#### `clearSearch()`
مسح بار البحث:

```javascript
function clearSearch() {
  searchInput.value = '';
  applySearch('');
  searchInput.focus();
}
```

#### `copyToClipboard(element)`
نسخ النص للحافظة:

```javascript
function copyToClipboard(element) {
  if (element && element.textContent) {
    navigator.clipboard.writeText(element.textContent);
    showToast();
  }
}
```

#### `showToast()`
عرض رسالة النجاح:

```javascript
function showToast() {
  var x = document.getElementById("toast");
  x.classList.add("show");
  setTimeout(function(){ x.classList.remove("show"); }, 3000);
}
```

### Event Listeners

```javascript
// البحث الحي
searchInput.addEventListener('input', (e) => applySearch(e.target.value));

// تفعيل البحث عند الحمل
applySearch('');
```

---

## طريقة البحث

### كيفية عمل `data-search`:

```html
<!-- البحث يشمل هذه الكلمات المفتاحية -->
<tr class="topic-row" data-search="powershell admin context menu right click registry">
  <td>إضافة PowerShell Admin</td>
</tr>
```

### أمثلة على البحث الناجح:

| البحث | النتيجة |
|------|--------|
| `powershell` | ✅ نجح |
| `admin` | ✅ نجح |
| `context` | ✅ نجح |
| `menu` | ✅ نجح |
| `right` | ✅ نجح |
| `power` | ❌ فشل (بحث جزئي غير مدعوم) |

---

## الأداء

### تحسينات الأداء:

- 💀 **CSS Gradients** بدلاً من الصور
- 💰 **CSS Variables** لتغييرات الألوان الديناميكية
- ⚡ **Vanilla JS** بدون مكتبات خارجية
- 👻 **Event Delegation** للبحث الفعال
- 💱 **No frameworks** = تحميل أسرع

### حجم الملفات:

- `index.html`: ~44KB (مع كل التوبيكات)
- `README.md`: ~13KB
- **Total**: < 100KB

---

## إضافة توبيك جديد

### خطوات إضافة موضوع جديد:

1. أضف صف جديد في الجدول:

```html
<tr class="topic-row" data-target="my-new-topic" data-search="keyword1 keyword2 اختياري">
  <td><span class="category-label category-CATEGORY">🔧 التصنيف</span></td>
  <td>اسم الموضوع</td>
  <td class="muted">وصف سريع جداً</td>
  <td><span class="badge">TAG</span></td>
</tr>
```

2. استخدم التصنيفات الصحيحة (category-system, category-privacy, إلخ)
3. أضف كلمات مفتاحية في `data-search`
4. اختبر البحث تأكد من أن الموضوع يظهر

---

## الاستجابة (Responsive)

### Breakpoints:

```css
/* جوال */
@media (max-width: 768px) { }

/* تابلت */
@media (768px < width < 1024px) { }

/* سطح مكتب */
@media (min-width: 1024px) { }
```

---

## الترخيص والمساهمة

- 📄 MIT License
- 🤝 المساهمات مرحب بها
- 🐛 البلاغات عن الأخطاء مهمة

---

## الروابط والمراجع

- [GitHub Repository](https://github.com/sherow1982/windows-adjust)
- [Live Site](https://sherow1982.github.io/windows-adjust/)
- [CONTRIBUTING Guide](../CONTRIBUTING.md)
- [INSTALLATION Guide](./INSTALLATION.md)
