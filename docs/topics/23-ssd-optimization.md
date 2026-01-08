# تحسين أداء SSD

## الوصف
تفعيل TRIM وتحسينات SSD للأقراص الصلبة.

## التحقق من SSD

```powershell
# PowerShell (Run as Admin)
# هل SSD يدعم TRIM؟
Get-PhysicalDisk | Select-Object MediaType, FriendlyName

# تفعيل TRIM
Optimize-Volume -DriveLetter C -Defrag -Verbose
```

## تفعيل TRIM

```powershell
# PowerShell (Run as Admin)
fsutil behavior set DisableDeleteNotify 0

# التحقق من التفعيل
fsutil behavior query DisableDeleteNotify
# إذا كانت النتيجة 0: TRIM مفعل
# إذا كانت النتيجة 1: TRIM معطل
```

## تحسين الأداء

```powershell
# تعطيل المسافة البيضاء (White space)
fsutil file queryclustersize C:

# تعطيل Indexing على SSD
Reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Search" /v DisableFullIndexing /t REG_DWORD /d 1 /f
```

## إعادة المحاذاة

```powershell
# PowerShell (Run as Admin)
Optimize-Volume -DriveLetter C -Defrag -Verbose

# أو تحديد أداة أخرى
Optimize-Volume -DriveLetter C -MediaType SSD -Defrag
```

## جدولة التحسين

```
1. اضغط Win وابحث عن "Optimize drives"
2. اختر SSD
3. اضغط "Change settings"
4. فعّل "Run on a schedule"
5. اختر "Weekly"
```

## ملاحظات
- TRIM يحسن الأداء على الأمد الطويل
- لا تحتاج لـ Defragmentation على SSD
- تجنب التجزئة عند الإمكان
