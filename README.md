# Duck Shoot TV: الموبايل بدل المسدس

## الإعداد (مرة واحدة)

### 1) Firebase
1. ادخل https://console.firebase.google.com وأنشئ مشروع جديد.
2. من القائمة: **Build → Realtime Database → Create Database**.
3. اختر **Start in test mode**.
4. من تبويب **Rules** حط الآتي واضغط Publish:

```json
{
  "rules": {
    "rooms": {
      "$room": { ".read": true, ".write": true }
    }
  }
}
```

5. انسخ رابط قاعدة البيانات (شكله `https://xxxx-default-rtdb.firebaseio.com`) وحطه في `config.js` مكان `DB_URL`.

### 2) GitHub Pages
1. أنشئ repo جديد وارفع الملفات الأربعة: `config.js`, `tv.html`, `phone.html`, `README.md`.
2. **Settings → Pages → Branch: main / root → Save**.
3. الرابط هيبقى `https://USERNAME.github.io/REPO/`.

### 3) التشغيل
1. من تطبيق Foxxum افتح `https://USERNAME.github.io/REPO/tv.html`.
2. هيظهر كود من 4 أرقام و QR.
3. من الموبايل امسح الـ QR (أو افتح `phone.html` واكتب الكود)، واضغط **اتصال**.
4. وجّه الموبايل لمنتصف الشاشة واضغط **معايرة**.
5. حرّك الموبايل للتصويب، واضغط **اضرب** للإطلاق.

## للتجربة بدون موبايل
على التلفزيون: الأسهم تحرك التصويب، و OK يضرب.

## لو حصلت مشكلة
- **الشاشة بتفضل "بانتظار الموبايل"**: اتأكد إن `DB_URL` صح في `config.js` وإن الـ Rules اتنشرت.
- **الحساسات مش شغالة**: لازم الصفحة HTTPS (GitHub Pages بيوفرها).
- **التصويب مش مظبوط**: عدّل `RANGE_X` و `RANGE_Y` في `phone.html` (قيمة أصغر = حساسية أعلى).
- **متصفح التلفزيون مش بيقرأ البيانات**: افتح `tv.html` على متصفح الموبايل للتأكد إن الكود شغال، وبعدها نشوف إيه اللي ناقص في متصفح الشاشة.
