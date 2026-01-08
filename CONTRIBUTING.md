# 🤝 مرشد المساهمة - Contributing Guide

> **شكراً لرغبتك في المساهمة في مشروع Windows Adjust!** 🌟

---

## 💫 لماذا المساهمة؟

- 🏆 **بناء مجتمع**: كل مساهمة هامة
- 🌟 **مشع رحب بها**: لا تتردد - ساهم مباشرة!
- ✨ **يتم مراجعتها**: عم سريع ومحبترم

---

## ✅ أنواع المساهمات

### 1️⃣ إضافة توبيكات جديدة

**يمكنك المساهمة بيإضافة:**

- 🖛 أوامر PowerShell/CMD جديدة
- 🔧 تحسينات نظام مبتكرة
- 🧹 تقنيات تنظيف متقدمة
- 🔰 حيل لمشاكل معروفة

### 2️⃣ تحسين المواضيع الحالية

- ✍️ تعديل أر أم تي ملبسة
- خطأ إملائي بلغرافية عربية
- تحسين الوصف عن أوامر

### 3️⃣ ترجمة للإنجليزية

- إذا كانت لغتك الإنجليزية جيدة

### 4️⃣ رفع أخطاء ومشاكل

- اعثر على أخطاء في الأوامر
- أخبرنا بيثير له عبارة

---

## 🚀 بدء المساهمة بسرعة

### **الخطوة 1: Fork**

```
adhub.com/sherow1982/windows-adjust
→ اضغط Fork (top right)
```

### **الخطوة 2: Clone**

```bash
git clone https://github.com/YOUR_USERNAME/windows-adjust.git
cd windows-adjust
```

### **الخطوة 3: انشئ Branch**

```bash
git checkout -b feature/your-feature-name
# مثال:
# git checkout -b feature/add-registry-tweak
```

### **الخطوة 4: Edit**

عدل `index.html` وأضف توبيكك

### **الخطوة 5: Commit**

```bash
git add .
git commit -m "فيالثر: إضافة registry tweak لتسريع Boot"
# نمط:
# "Add: [type] - [description]"
# "Fix: [description]"
# "Update: [description]"
```

### **الخطوة 6: Push**

```bash
git push origin feature/your-feature-name
```

### **الخطوة 7: Pull Request**

- اذهب لالريبو الأصلي
- اضغط **New Pull Request**
- اختر branch بتاعك
- اوصف ما فعلت

---

## ✅ معايير القبول

للقبول بمساهمتك بنجاح:

- ✅ **لغة عربية سليمة** - بدون أخطاء ملبسة
- ✅ **أوامر صحيحة** - الأوامر يجب أن تعمل فعلاً
- ✅ **وصف رائع** - وصف واضح للأمر
- ✅ **آمن - موثوق** - لا تفعل الأشياء الخطيرة!
- ✅ **ربط HTML** - صابع بحالها

---

## 📚 مبدأ العمل

### هيكل التوبيك في index.html:

```html
<tr class="topic-row" data-target="my-topic" data-search="مفاتيح keyword1 keyword2">
    <td>
        <span class="category-label category-system">🔧 النظام</span>
    </td>
    <td>
        <strong>اسم التوبيك</strong>
    </td>
    <td class="muted">وصف بسيط</td>
    <td>
        <span class="badge">TAG1</span>
        <span class="badge">TAG2</span>
    </td>
</tr>
```

### الفئات:
- `category-system` = 🔧 النظام
- `category-privacy` = 🔒 الخصوصية
- `category-performance` = ⚡ الأداء
- `category-cleanup` = 🧹 التنظيف
- `category-fix` = 🔨 الإصلاح

---

## 💁 ربط مفيدة

- 📚 [README](README.md) - الرئيسية
- 📋 [TOPICS](TOPICS.md) - قائمة المواضيع
- 📚 [LICENSE](LICENSE) - الترخيص

---

## 🌠 الأوامر السريعة

```bash
# Clone + Setup
git clone https://github.com/YOUR_USERNAME/windows-adjust.git && cd windows-adjust

# Create branch
git checkout -b feature/your-feature

# Make changes
# Then...

git add .
git commit -m "Add: Your awesome feature"
git push origin feature/your-feature

# افتح Pull Request من GitHub UI
```

---

## ❤️ شكراً!

**شكراً لمساهمتك هذه طريقة واحترامنا لوقتك وجهدك!** ❤️

---

**للأسئلة**: [افتح Issue](https://github.com/sherow1982/windows-adjust/issues/new)
