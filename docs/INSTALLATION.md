# 🚀 دليل البداية

## سريع وبسيط

Windows Adjust Reference هو موقع رابط بسيط - لا يحتاج لأي تثبيت!

### طريقة الوصول المباشرة:

```
https://sherow1982.github.io/windows-adjust/
```

بس امل الرابط مباشرة في متصفحك - وهذا كل ما تحتاجه!

---

## على جهازك (Local Development)

### المتطلبات:

- 💻 متصفح حديث (Chrome, Firefox, Edge, Safari)
- 📱 خادم ويب (Python, Node.js, أو أي خادم آخر)

### خطوات التثبيت:

#### الخيار الأول: باستخدام Python

```bash
# انسخ الريبو
git clone https://github.com/sherow1982/windows-adjust.git
cd windows-adjust

# شغل خادم ويب
python -m http.server 8000

# افتح http://localhost:8000
```

#### الخيار الثاني: باستخدام Node.js

```bash
# انسخ الريبو
git clone https://github.com/sherow1982/windows-adjust.git
cd windows-adjust

# شغل المشروع
npm install
npm run dev

# سيفتح متصفحك للرابط http://localhost:8000
```

#### الخيار الثالث: بفتح مباشر

```bash
# على Windows
start index.html

# على macOS
open index.html

# على Linux
xdg-open index.html
```

---

## للمبالغة من Fork

### 1. Fork المشروع

```bash
git clone https://github.com/YOUR_USERNAME/windows-adjust.git
cd windows-adjust
```

### 2. أنشئ Pull Request

```bash
git checkout -b feature/your-feature-name
git add .
git commit -m "(يصف قصير) - التغيير الذي لنا فعلته"
git push origin feature/your-feature-name
```

### 3. فتح Pull Request للريبو الرئيسي

---

## الهيكلة

```
windows-adjust/
├── index.html              # الرابط الرئيسي
├── README.md               # المرجع
├── CHANGELOG.md            # مسجل التغييرات
├── package.json            # بيانات المشروع
├── .gitignore              # الملفات المستثنياة
├── .editorconfig           # اعدادات المحرر
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions CI/CD
├── docs/
│   └── INSTALLATION.md # هذا الملف
└── LICENSE                 # MIT License
```

---

## المميزات التقنية

- 💍 **HTML5** سالم
- 🎨 **CSS3** محدث
- 🔍 **Vanilla JavaScript** بدون مكتبات
- 📱 **Responsive Design** Mobile-First
- 🐝 **Git** للمراقبة

---

## الدعم والمساعدة

إذا واجهت أي مشاكل:

1. راجع [GitHub Issues](https://github.com/sherow1982/windows-adjust/issues)
2. افتح Issue جديد
3. ارشرح المشكلة بروضوح

---

## الخطوات التالية

- [📚 قراءة CONTRIBUTING.md](../CONTRIBUTING.md)
- [🐛 المبلغـ Issues](https://github.com/sherow1982/windows-adjust/issues)
- [🤝 الربط مع المجتمع](https://github.com/sherow1982/windows-adjust/discussions)
